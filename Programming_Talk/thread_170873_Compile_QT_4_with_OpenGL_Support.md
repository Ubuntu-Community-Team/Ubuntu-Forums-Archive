---
title: "Compile QT 4 with OpenGL Support"
date: 2006-05-05
forum: Programming Talk
---

### Post by alexsb on 2006-05-05
Hi,

I am new to (k)ubuntu, switched yesterday from gentoo  - just could not stand compiling everything any more :). Anyway, I have user nothing but Linux for more than two years, so I am not completely illiterate :)

Here is my first problem I ran into: 

I have to install QT 4 with OpenGL Support enabled. I downloaded the sources directly from trolltech. I understand that there are some dependencies, especially mesa afaik, I have these packages installed. OpenGL is working fine too, at least tuxracer and glxgears are. I use NVidia drivers.

When I try to run the ./configure script in QT's source directory it always selects OpenGL as no. Some friends of mine had the same problem but fixed it installing these mesa packages.

Does anyone know what other dependencies there are?

Thank you,

Alex

---

### Post by alexsb on 2006-05-05
I guess something is wrong with my paths, when I run configure with the -v version it shows the following error:

```
OpenGL auto-detection... () 
g++  -o opengl opengl.o    -L/usr/X11R6/lib -lGL -lGLU -lXext -lX11 -lm /usr/bin/ld: cannot find -lXext collect2: ld returned 1 exit status 
make: *** [opengl] Error 1 
OpenGL disabled. 
```

I tried setting 

QMAKE_INCDIR_OPENGL and/or QMAKE_LIBDIR_OPENGL

to /usr/include/GL but it did not work either.

---

### Post by asimon on 2006-05-06
The error message says the linker can't find library libXext.so, which should reside under /usr/lib. Is it there? It comes with the packages libxext6.

Regarding paths: /usr/lib is a default place where the linker will search for libs additionally to what is specified via the -L option.

---

### Post by alexsb on 2006-06-21
Thank you for your help, it simply was an unmet dependency :)

Greetings,

Alex

---

