---
title: "Issues getting GLUT working in Ubuntu under x64.."
date: 2010-01-10
forum: Programming Talk
---

### Post by trycatch on 2010-01-10
**Uname:**  2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
**Version:** Ubuntu 9.10

**Issue:**  Display errors using GLUT under Ubuntu 64bit

So..  I've been doing glut programming here and there on Windows / Fedora and yet to have a problem...  but I can't seem to get it to cooperate under Ubuntu 64 bit..  Although I'm not entirely sure whether it's GLUT or X11.

I've got:
libGL.so.1.2 
libGLU.so.1.3.070600
libGLEW.so.1.5.1
libglut.so.3.8.0

All of which are  ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped.

And all the headers that came with them.  Trying to run a simple app that creates a black window (that works on Windows / Fedora) seems to try to create something..  an item appears in the bottom panel and I can select "move", but the window is never visible.

When I compile / execute this:

[http://www.opengl.org/resources/code/samples/redbook/aaindex.c](http://www.opengl.org/resources/code/samples/redbook/aaindex.c)

App straight out of the gl red book online, I get the following error:

```

freeglut (./sampleApp):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  31
  Current serial number in output stream:  34

```Again, this code compiles and executes fine in Windows / Fedora, so I'm not sure what the issue is..  has anyone else ever experienced this?

---

