---
title: "Working with mesa and glut on ubuntu, compiling glxdemo"
date: 2007-09-06
forum: Programming Talk
---

### Post by TheNonBornKing on 2007-09-06
I'm trying to create some applications using mesa and glut. I'm a beginner with both of these libraries. I think I have glut but I'm not sure about mesa. Here are the mesa packages I have:

libgl1-mesa-dev
libgl1-mesa-dri
libgl1-mesa-glx
libglu1-mesa
libglu1-mesa-dev
mesa-common-dev
mesa-utils

None of these packages seem to install any header files except for gl.h, glu.h, and glx.h in /usr/include/GL.

Now, the mesa-utils package installs the glxdemo, a program that apparently draws a square on the screen. I looked up the source code for this and downloaded it from here:
[http://www.koders.com/c/fid10F11B11616845C8D962EF597D341D56F50A214C.aspx](http://www.koders.com/c/fid10F11B11616845C8D962EF597D341D56F50A214C.aspx)

Then I try to compile it and get the following errors:
abaddon@fraggle-rock:~/work/drawing$ gcc glxdemo.c -o mydemo
/tmp/ccuDufpy.o: In function `redraw':
glxdemo.c: (.text+0x1a): undefined reference to `glClear'
glxdemo.c: (.text+0x39): undefined reference to `glColor3f'
glxdemo.c: (.text+0x61): undefined reference to `glRectf'
glxdemo.c: (.text+0x73): undefined reference to `glXSwapBuffers'
/tmp/ccuDufpy.o: In function `resize':
glxdemo.c: (.text+0xa9): undefined reference to `glViewport'
glxdemo.c: (.text+0xb5): undefined reference to `glMatrixMode'
glxdemo.c: (.text+0xba): undefined reference to `glLoadIdentity'
glxdemo.c: (.text+0xee): undefined reference to `glOrtho'
/tmp/ccuDufpy.o: In function `make_rgb_db_window':
glxdemo.c: (.text+0x17c): undefined reference to `glXChooseVisual'
glxdemo.c: (.text+0x1ce): undefined reference to `XCreateColormap'
glxdemo.c: (.text+0x240): undefined reference to `XCreateWindow'
glxdemo.c: (.text+0x265): undefined reference to `glXCreateContext'
glxdemo.c: (.text+0x29f): undefined reference to `glXMakeCurrent'
/tmp/ccuDufpy.o: In function `event_loop':
glxdemo.c: (.text+0x2d2): undefined reference to `XNextEvent'
/tmp/ccuDufpy.o: In function `main':
glxdemo.c: (.text+0x32d): undefined reference to `XOpenDisplay'
glxdemo.c: (.text+0x35a): undefined reference to `glShadeModel'
glxdemo.c: (.text+0x382): undefined reference to `glClearColor'
glxdemo.c: (.text+0x394): undefined reference to `XMapWindow'
collect2: ld returned 1 exit status

I have no idea what to do from here. Any suggestions?

---

### Post by Mirrorball on 2007-09-06
You should link it to the libraries: GL, GLU, and glut.
```
gcc -lGL -lGLU -lglut glxdemo.c -o mydemo
```

---

### Post by gnusci on 2007-09-07
In case you still can no compile it, just to make sure you have everything try:

**$ sudo apt-get install freeglut3-dev** (OpenGL)


And maybe: 

**$ sudo apt-get install build-essential** (compiling tools)
**$ sudo apt-get build-dep xorg-dev**       (x11 for developing)

---

### Post by TheNonBornKing on 2007-09-07
> **Mirrorball said:**
> You should link it to the libraries: GL, GLU, and glut.
```
gcc -lGL -lGLU -lglut glxdemo.c -o mydemo
```

Thanks Mirrorball, that worked perfectly.

---

