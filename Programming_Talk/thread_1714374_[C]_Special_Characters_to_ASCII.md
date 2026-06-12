---
title: "[C] Special Characters to ASCII"
date: 2011-03-25
forum: Programming Talk
---

### Post by Royk14 on 2011-03-25
[B][FONT=Arial]Hi,
I'm developing a program that generates a mystery word puzzle.
The program must read words from a .txt file (portuguese words, with characters like Á, á, é, à, í, ç, ...) and put them on the grid, BUT with those special characters turned into ordinary ASCII characters (A, a, e, a , i, c, ...).
How can i do this?

Thanks in advance.[/FONT]
[/B][]("http://en.wikipedia.org/wiki/Puzzle")

---

### Post by Vaphell on 2011-03-25
if your input file is 1byte encoded (e.g iso-8859-1 or win-1252) you can create a list of translations for all special chars and test each string char if it matches criteria and replace with proper value
[http://en.wikipedia.org/wiki/ISO/IEC_8859-1#Codepage_layout](http://en.wikipedia.org/wiki/ISO/IEC_8859-1#Codepage_layout)
[http://en.wikipedia.org/wiki/Windows-1252#Codepage_layout](http://en.wikipedia.org/wiki/Windows-1252#Codepage_layout)
Á=193 -> A=65
á=225 -> a=97
...

unicode is more complicated because you can't count on fixed width characters.

---

