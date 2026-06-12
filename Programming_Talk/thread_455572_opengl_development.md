---
title: "opengl development"
date: 2007-05-26
forum: Programming Talk
---

### Post by newen on 2007-05-26
Hi! I need some tips. What I have to set up to develop with Opengl? I mean, which package provides the headers and libraries, and how should I compile the code? I think I should use mesa...

Anyway, there is a nvidia-glx-dev package? Is this a replacement for mesa? Anyone knows why nvidia-glx depends on mesa when it should be a drop-in-replacement?

Thx

---

### Post by hod139 on 2007-05-27
You need to install the packages: libgl1-mesa-dev and libglu1-mesa-dev.  To compile the code you would add

```

#include <GL/gl.h> 
#include <GL/glu.h>

```

The nvidia-glx-dev package is a header allowing you to use nvidia specific opengl extensions, assuming you have an nvidia card.

Also, in addition to openGL you will most likely want a windowing toolkit to view stuff.  The two common solutions are SDL and GLUT.  For using SDL see the [ubuntu-gamedev wiki]("http://ubuntu-gamedev.wikispaces.com/"):

---

