---
title: "opengl and glut:"
date: 2007-12-21
forum: Programming Talk
---

### Post by Elisei on 2007-12-21
hi there : 

i am trying to compile some OpenGL code but i get an error about gluti think:

i enter:
     gcc testgl.c -lGL -lGLU -lSDL -lpthread -o testgl

and get a linker error:

/usr/bin/ld: warning: libGL.so.1, needed by /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libGLU.so, may conflict with libGL.so.1.2
/tmp/ccUy82pp.o: In function `main':
testgl.c: (.text+0x14e): undefined reference to `glutInit'
testgl.c: (.text+0x15a): undefined reference to `glutInitDisplayMode'
testgl.c: (.text+0x16e): undefined reference to `glutInitWindowSize'
testgl.c: (.text+0x182): undefined reference to `glutInitWindowPosition'
testgl.c: (.text+0x18e): undefined reference to `glutCreateWindow'
testgl.c: (.text+0x19f): undefined reference to `glutDisplayFunc'
testgl.c: (.text+0x1a4): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

cant seem to fix it so any suggestions or a link to a tutorial would be great!

---

### Post by revanthedarth on 2007-12-21
Don't forget to include glut libary, -lglut. Inlude it and it will link with no errors.

---

