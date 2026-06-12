---
title: "Linking OpenGL failing?"
date: 2011-11-12
forum: Programming Talk
---

### Post by someoney3000 on 2011-11-12
Hello!

I've been trying to compile and run one of my older programs from a different Ubuntu machine.  The program uses glut, glu, and opengl.

I'm pretty sure I have all the libraries installed and the correct compiler flags (-lGLU -lGL -lglut), but I get this:

```

/tmp/ccw7CRt8.o: In function `setFog()':
assn4.cpp:(.text+0x16): undefined reference to `glFogi'
assn4.cpp:(.text+0x2a): undefined reference to `glFogfv'
assn4.cpp:(.text+0x3f): undefined reference to `glFogf'
/tmp/ccw7CRt8.o: In function `setLights()':
assn4.cpp:(.text+0x5b): undefined reference to `glLightModelfv'
assn4.cpp:(.text+0x77): undefined reference to `glLightfv'
assn4.cpp:(.text+0x93): undefined reference to `glLightfv'
assn4.cpp:(.text+0xaf): undefined reference to `glLightfv'
assn4.cpp:(.text+0xcb): undefined reference to `glLightfv'
assn4.cpp:(.text+0xe7): undefined reference to `glLightfv'
/tmp/ccw7CRt8.o:assn4.cpp:(.text+0x103): more undefined references to `glLightfv' follow
/tmp/ccw7CRt8.o: In function `setLights()':
assn4.cpp:(.text+0x10f): undefined reference to `glEnable'
assn4.cpp:(.text+0x11b): undefined reference to `glEnable'
assn4.cpp:(.text+0x127): undefined reference to `glEnable'
/tmp/ccw7CRt8.o: In function `myInit()':
assn4.cpp:(.text+0x13c): undefined reference to `glEnable'
assn4.cpp:(.text+0x148): undefined reference to `glEnable'
/tmp/ccw7CRt8.o:assn4.cpp:(.text+0x154): more undefined references to `glEnable' follow
/tmp/ccw7CRt8.o: In function `myInit()':
assn4.cpp:(.text+0x168): undefined reference to `glHint'
assn4.cpp:(.text+0x17c): undefined reference to `glHint'
assn4.cpp:(.text+0x1a4): undefined reference to `glClearColor'
assn4.cpp:(.text+0x1b0): undefined reference to `glShadeModel'
/tmp/ccw7CRt8.o: In function `myResized(int, int)':
assn4.cpp:(.text+0x27a): undefined reference to `glViewport'
assn4.cpp:(.text+0x286): undefined reference to `glMatrixMode'
assn4.cpp:(.text+0x28b): undefined reference to `glLoadIdentity'
assn4.cpp:(.text+0x2c5): undefined reference to `gluPerspective'
assn4.cpp:(.text+0x2d1): undefined reference to `glMatrixMode'
assn4.cpp:(.text+0x2d6): undefined reference to `glutPostRedisplay'
/tmp/ccw7CRt8.o: In function `setColor(float*, float)':
assn4.cpp:(.text+0x2f9): undefined reference to `glMaterialfv'
assn4.cpp:(.text+0x314): undefined reference to `glMaterialfv'
assn4.cpp:(.text+0x330): undefined reference to `glMaterialfv'
assn4.cpp:(.text+0x34b): undefined reference to `glMaterialf'
etc.

```While creating the object files, there was no warning.  But then the linking step...

Anyways, I've checked if I have the OpenGL libraries somewhere on my system and found it at /usr/lib/i386-etc/libGL.so and tried linking it to /usr/lib but that didn't make a difference...

Is there any other approach that I should consider to get opengl running?

---

### Post by MadCow108 on 2011-11-12
make sure the link flags are at the end of the command line:

```
gcc somefile.c -lGLU -lGL -lglut
```

---

### Post by someoney3000 on 2011-11-12
> **MadCow108 said:**
> make sure the link flags are at the end of the command line:

```
gcc somefile.c -lGLU -lGL -lglut
```

WHAT

That worked.

Still in shock.

Thanks!

---

