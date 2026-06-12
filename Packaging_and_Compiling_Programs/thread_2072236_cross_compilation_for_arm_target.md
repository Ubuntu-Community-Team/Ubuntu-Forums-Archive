---
title: "cross compilation for arm target"
date: 2012-10-17
forum: Packaging and Compiling Programs
---

### Post by les sciences on 2012-10-17
Hi,

I try to cross compile an application to be run on arm target (my host is x86 ubuntu 11.10).

when i run "make", i obtain this error:

mar@ubuntu:~/Desktop/App$ make
...
cc1plus: warning: include location "/usr/include/GL/" is unsafe for cross-compilation
cc1plus: warning: include location "/usr/include/c++/4.6/" is unsafe for cross-compilation
cc1plus: warning: include location "/usr/include/qt4/" is unsafe for cross-compilation
..
/usr/include/qt4/QtOpenGL/qgl.h:77:15: fatal error: GL: No such file or directory
compilation terminated.
make: *** [main.o] Error 1


I know that i need to cross compile my librairies qt4 and OpenGL for arm , but i do not know how.

Can you please help me??

for makefile i use those compilers.

CC = arm-none-linux-gnueabi-gcc
CXX = arm-none-linux-gnueabi-g++
AR = ar 

Thank you in advance.

---

