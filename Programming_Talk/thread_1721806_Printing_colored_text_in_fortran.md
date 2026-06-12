---
title: "Printing colored text in fortran?"
date: 2011-04-05
forum: Programming Talk
---

### Post by castiglione on 2011-04-05
Hello, everyone.
 
The title header says it all:  Is it possible to print colored text in fortran?
 
I imagine it must involve using the "write" command with some sort of formatting?
 
Thanks in advance!
 
c

---

### Post by 1clue on 2011-04-05
That's a function of your output device, not the language.  FORTRAN (disclaimer:  My FORTRAN training dates back to 1984) prints characters out, and the output device interprets those characters.  If you print an escape sequence the output device (printer or terminal) understands as a color code, then it will print in that color until you reset the color to something else.

---

