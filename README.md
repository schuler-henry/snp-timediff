# snp-timediff
DHBW Exam in assembly language with the following requirements:


## Programmentwurf Systemnahe Programmierung Kurs TIT20

### Bearbeitungshinweise
Die Prüfungsleistung für die Vorlesung Systemnahe Programmierung wird durch einen Programmentwurf in Intel x86-64 Assembler für den NASM Assembler unter dem Betriebssystem Linux erbracht. Andere Programmiersprachen sowie C-Bibliotheksfunktionen in Assemblerprogrammen dürfen nicht verwendet werden, außer dies ist in der Aufgabenstellung ausdrücklich gefordert.

### Aufgabenstellung
Schreiben Sie ein Assembler-Programm timediff, welches eine Folge aufstei-
gend sortierter Zeitstempel einliest und für jeden Zeitstempel die Zeitdifferenz 
zu dessen Vorgänger ausgibt.

- Die Eingabe erfolgt zeilenweise von der Standardeingabe als formatierter ASCII-Text.
- Gültige Eingabezeilen enthalten genau einen Zeitstempel.
- Eingabezeilen werden durch einen Zeilenumbruch abgeschlossen.
- Die Ausgabe erfolgt auf der Standardausgabe. Die Anzahl der Sys-tem-Call Aufrufe (hier System-Call `write`) ist zu minimieren.
- Eingabezeilen werden nicht ausgegeben.
- Die Ausgabe erfolgt erst, nachdem der Eingabetext vollständig eingelesen wurde.
- Ein Eingabetext kann maximal 10000 Zeitstempel enthalten.
- Ein gültiger Zeitstempel wird im Format `S+.M+` angegeben, wobei `S` die Anzahl Sekunden seit der UNIX Epoche angibt und `M` die Anzahl Mikrosekunden seit Sekundenbeginn. `S` und `M` sind Dezimalziffern im ASCII-Format.
- Ein Zeitstempel ist in eine Struktur des Typs `struct timeval` zu konvertieren (Definition siehe `man 2 gettimeofday`).
- Wenn eine Eingabezeile einen ungültigen Zeitstempel enthält, dann beendet sich das Programm mit einer entsprechenden Fehlermeldung.
- Der Sekundenanteil eines Zeitstempels ist bei der Eingabe vorzeichenlos und mindestens einstellig mit einem maximalen Wertebereich von 64 Bit.
- Der Mikrosekundenanteil eines Zeitstempels ist bei der Eingabe grundsätzlich auf sechs Stellen zu normieren, d.h. der Mikrosekundenanteil des Zeitstempels `1502736311.5` ist `500000`.
- Die konvertierten Zeitstempel werden in einer Liste gespeichert.
- Das Modul Liste implementiert mindestens die in der Datei `list.asm` vordefinierten Funktionen.
- Die Datei `list_test.c` definiert den Modultest für das Modul Liste.
- Für die Ausgabe werden die Zeitstempel aus der Liste ausgelesen.
- Die Ausgabe der Zeitstempel und der Zeitdifferenzen muss dem Format des unten aufgeführten Beispiels entsprechen.

#### Beispiel einer Eingabefolge:
```
1000000000.0
1234567890.000000
1483225200.000000
1491861600.000
1500000000.000000
1502529000.000001
1502529001.000000
1502530860.999999
1502617201.999998
1502617202.000000
1502736311.000001
```

#### Format für die Ausgabe:
```
1000000000.000000
=======
1234567890.000000
2714 days, 20:44:50.000000
=======
1483225200.000000
2877 days, 23:28:30.000000
=======
1491861600.000000
100 days, 00:00:00.000000
=======
1500000000.000000
94 days, 04:40:00.000000
=======
1502529000.000001
29 days, 06:30:00.000001
=======
1502529001.000000
00:00:00.999999
=======
1502530860.999999
00:30:59.999999
=======
1502617201.999998
23:59:00.999999
=======
1502617202.000000
00:00:00.000002
=======
1502736311.000001
1 day, 09:05:09.000001
```

## [LICENSE](LICENSE)
MIT License

Copyright (c) 2022 Johannes Brandenburger, Lukas Braun, Henry Schuler

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
