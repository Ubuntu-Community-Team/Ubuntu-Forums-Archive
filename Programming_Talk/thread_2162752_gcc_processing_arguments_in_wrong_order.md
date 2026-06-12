---
title: "gcc processing arguments in wrong order"
date: 2013-07-15
forum: Programming Talk
---

### Post by ElWilliaM on 2013-07-15
I am a newbie C programmer, and while trying a little practice work to learn libncurses, I discovered a very strange behaviour in gcc 4.7 on my Lubuntu 13.04 system: when I try this:
```
gcc -lncurses cursesprogram.c
```
I get a long string of "undefined reference to" errors, but, when I try
```
gcc cursesprogram.c -lncurses
```
it compiles just fine. Is this how it is supposed to work? I read in the gcc man page that the placement of the -l[library] option in a gcc command string affects the order of processing, and that gcc processes files in the order in which they appear in the command string, so it seems logical that ```
gcc -lncurses cursesprogram.c
``` would tell gcc to process libncurses before compiling my source code file, but it seems to be happening in reverse. This behaviour is also breaking the makefiles of numerous other programs I have compiled successfully on other ubuntu computers.
(I have build-essential and libncurses5-dev installed)
Any ideas on how to fix this would be Hugely appreciated.

---

### Post by Bachstelze on 2013-07-15
Yes, this is how it's supposed to work. The best thing to do would be to fix the Makefiles, but if that's not practical, you can add -no-as-needed to your LDFLAGS.

---

### Post by ElWilliaM on 2013-07-15
Is this behaviour new in GCC 4.7? My code compiles quite nicely on my Raspbery Pi running Raspbian with GCC 4.6 using the same makefile that is malfunctioning for me now. The following commands both compile equally well (and error-free). 
```
gcc -lncurses cursesprogram.c
```
```
gcc cursesprogram.c -lncurses
```
Is there any way to reconfigure GCC 4.7 on Lubuntu 13.04 to work the same way?

---

### Post by Bachstelze on 2013-07-15
This is actually caused by the linker, not the compiler. Like I said, the way to revert to the old behavior is to use -no-as-needed in your linker flags. It was the default before, now -as-needed is the default in Ubuntu. If you are interested just Google something along the lines of "Ubuntu as-needed", there is plenty of information around.

---

### Post by ElWilliaM on 2013-07-16
Thank you very much for the info. I am learning more about the compilation process than I ever knew before.

---

