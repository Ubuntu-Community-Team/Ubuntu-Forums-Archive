---
title: "freeglut3"
date: 2006-07-21
forum: Programming Talk
---

### Post by theconley on 2006-07-21
I'm trying to use glut and I have used Adept to install both freeglut3 and freeglut3-dev.

I can find the header files from the dev package just fine, and so can my program, but I'm having a hard time finding the object files, and so is g++.  In other words, I'm getting a lot of "undefined references".

```
:lesson1.c:(.text+0x1d2): undefined reference to `glutInitDisplayMode'
:lesson1.c:(.text+0x1e1): undefined reference to `glutInitWindowSize'
:lesson1.c:(.text+0x1f0): undefined reference to `glutInitWindowPosition'
:lesson1.c:(.text+0x1fa): undefined reference to `glutCreateWindow'
:lesson1.c:(.text+0x20a): undefined reference to `glutDisplayFunc'
:lesson1.c:(.text+0x20f): undefined reference to `glutFullScreen'
:lesson1.c:(.text+0x219): undefined reference to `glutIdleFunc'
:lesson1.c:(.text+0x223): undefined reference to `glutReshapeFunc'
:lesson1.c:(.text+0x22d): undefined reference to `glutKeyboardFunc'
:lesson1.c:(.text+0x241): undefined reference to `glutMainLoop'
```

I can install freeglut by hand, but is there something I'm missing with my Adept install?

~Conley

---

### Post by Harleen on 2006-07-21
You have to link against the library to solve the undefines references. 
You can link dynamically with the compiler flag -l<library-name>. So you first have to find out the name of the library. If you have the name (maybe libglut.so?) you skip the "lib" part of the name and the extension and pass "-lglut" to the compiler.

---

### Post by theconley on 2006-07-21
O wow...

You're right...I can't believe I missed that.

I have a large project I have moved from Fedora Core to Ubuntu.  On the large project I have the -lglut flag set in my Makefile and I was getting errors (Not the same ones), so I moved to a small glut example, and I forgot to use -lglut on that one.

Well back to the drawing board to find out what the main problem really is.

---

### Post by theconley on 2006-07-21
OK, so here's the real problem:

I can initialize everything in glut just fine, but when I try to actually create a window, using:

```
glutCreateWindow("title")
```

I get this error:

```
freeglut (./exe):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  15
  Current serial number in output stream:  18
```

Is this a problem with my glut install?  Is it something I need to edit in my X configuration?

~Conley

---

