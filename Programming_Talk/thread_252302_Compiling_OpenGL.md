---
title: "Compiling OpenGL"
date: 2006-09-06
forum: Programming Talk
---

### Post by davek20 on 2006-09-06
Hi. I'm starting to do some OpenGL programming and I am having some problems compiling the code.

I used the tutorials off of NeHe, I just downloaded Lesson 2 for Linux just to see if it will compile, and it doesn't. I used the make file provided and this is the output:

$ make lesson2
gcc -Wall -I/usr/include/   -c -o lesson2.o lesson2.c
gcc -Wall -I/usr/include/ -o lesson2 -L/usr/X11R6/lib  lesson2.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [lesson2] Error 1
rm lesson2.o

I did a search on the forums for something similar to this, but none of the threads have the solution. Does anyone know how to fix this?

---

### Post by Hacim on 2006-09-06
Download the libX11-6 and libX11-dev packages,and then try.

---

