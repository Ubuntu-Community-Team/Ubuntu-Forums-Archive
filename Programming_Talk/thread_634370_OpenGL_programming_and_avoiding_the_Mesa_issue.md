---
title: "OpenGL programming and avoiding the Mesa issue"
date: 2007-12-07
forum: Programming Talk
---

### Post by Degenko on 2007-12-07
I'll be doing some OpenGL programming with Qt (again), but the last time I required GL/gl.h and other OpenGL headers, the freeglut3-dev package that I required through apt pulled with it some mesa packages and I was immediately (after next restart actually, until then the Qt framebuffer examples were working perfect) having Mesa issues. My graphics card is Radeon 9550.

So, none of the solutions seemed to work for me, so I was only left to reinstall Ubuntu. Not wanting to do that again (even though it's super-fast, other customizing and installing takes me another 3-4 hours), I'm applying to the Ubuntu community - what are other ways to get OpenGL header files? To simply build the source code, downloaded from the freeglut's sourceforge site?

Also, while framebuffer examples worked, pbuffer examples didn't. Radeon 9550 is a part of the third generation of Radeon cards, so it should use OpenGL 2.0. AFAIK, OpenGL already has a support for pbuffer extension in that version. Is my knowledge wrong or is this a drivers fault? Since, while I was still using Windows, the pbuffer examples worked, if I remember correctly.

All responses are welcome, thanks!

---

### Post by geirha on 2007-12-08
The freeglut3-dev package depends on a lot of packages, which it will install as well. One of those packages, libgl1-mesa-dev, will install it's own gl-library (/usr/lib/libGL*) which overwrites the existing one, installed by your graphics driver (I'm guessing you're using fglrx?) The package system should figure out this and do some magic to prevent it, but I'm guessing it didn't in this case.

Anyway, after installing the freeglut package, reinstalling your graphics driver should fix the problem I think.

---

