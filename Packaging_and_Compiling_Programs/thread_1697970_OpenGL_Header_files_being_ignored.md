---
title: "OpenGL Header files being ignored?"
date: 2011-03-01
forum: Packaging and Compiling Programs
---

### Post by tomkat3 on 2011-03-01
I'm trying to run an OpenGL program in ubuntu 10.04 with nvidia version 270.29.
Whenever I put 'make' into the terminal the following error is returned:

display.c:(.text+0x13a): undefined reference to `gluPerspective'

I thought I installed all the header files from freeglut, including glu.h, but it doesn't work all the same. What's happening?

I'm quite new to all this, so let me know if you need more information to help.

---

### Post by SevenMachines on 2011-03-01
You'll need to add the glu libs (-lGLU) to the linker flags, ie, for an simple test program using glut you might have something like
gcc -o test test.c -I/usr/include/GL -lGLU -lGL

---

