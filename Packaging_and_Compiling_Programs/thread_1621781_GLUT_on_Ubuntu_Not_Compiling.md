---
title: "GLUT on Ubuntu Not Compiling"
date: 2010-11-14
forum: Packaging and Compiling Programs
---

### Post by dragonwrenn on 2010-11-14
Hi
I programmed OpenGL on Windows with GLUT
I recently installed Ubuntu (I have no Linux experience).

When I try to compile a not particularly special program with GLUT, I get the errors:

||=== OpenGL on Linux, Debug ===|
ld||cannot find -lXxf86vm|
ld||cannot find -lglut.so|
||=== Build finished: 2 errors, 0 warnings ===|

I installed the
freeglut3-dev
freeglut3
freeglut3-dbg

packages and included the header files in my source

#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/freeglut.h>



Help Appreciated,
dragonwrenn

---

### Post by SevenMachines on 2010-11-14
> ld||cannot find -lXxf86vm|Is it installed?
$ sudo apt-get install libxxf86vm-dev

> ld||cannot find -lglut.so| Theres no file extension to library linking so no .so
$ gcc -lglut .....etc

---

### Post by dragonwrenn on 2010-11-15
Got it!  Thanks!

Ditched Code::Blocks for the command line and...

g++ -glut -lGL -lGLU  -o <EXECUTABLENAME> <SOURCECODENAME>

Works like a charm

---

