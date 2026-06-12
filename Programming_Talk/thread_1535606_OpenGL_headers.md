---
title: "OpenGL headers?"
date: 2010-07-21
forum: Programming Talk
---

### Post by theraje on 2010-07-21
Hey guys, I've been poking around trying to find out how to get the OpenGL headers on my system so I can start writing OpenGL programs. I tried the FAQ's and searched the forums, and found nothing. OpenGL's site wasn't much help in the Linux front.

Anyway, how can I acquire the OpenGL headers and get coding? Is there something in one of the repositories I need to grab, or...?

---

### Post by kahumba on 2010-07-21
I usually use freeglut:
sudo apt-get install freeglut3-dev

Then include the header:
#include <GL/gl.h>
which is at /usr/include/GL/gl.h

to compile (and link) successfully you have to add -lGL to the compiler command line.
if you're gonna use freeglut then also add -lglut -lGLU
and -lm for math functions like sin() and cos().

---

### Post by kahumba on 2010-07-21
Here's a working [NetBeans 6.9]("http://netbeans.org/downloads/index.html") (with C/C++ support) project using OpenGL (through glut) to draw a green rectangle in a window on 64 bit Ubuntu 10.04.

---

### Post by theraje on 2010-07-21
> **kahumba said:**
> Then include the header:
#include <GL/gl.h>
which is at /usr/include/GL/gl.h

to compile (and link) successfully you have to add -lGL to the compiler command line.

The header is what I was asking about, I don't have gl.h in my /usr/include/GL/ directory (it's completely empty). I'll try installing freeglut to see if that fixes things. Thanks! :)

---

### Post by programminglinguist on 2010-07-21
Why isn't there an easier approach to getting this done?

---

### Post by kahumba on 2010-07-21
Cause OpenGL is only cross-platform 2D/3D graphics, but to use it you also have to create a window for the graphics, handle mouse events, etc, that's why people usually use OpenGL as part of either GLUT or SDL which offer cross-platform support for mouse events, windows etc, hence to get up and running with OpenGL you should rather google for "glut tutorial" or "SDL tutorial" rather than "OpenGL tutorial".

---

### Post by efikkan on 2010-07-21
I usually grab the latest headers from [http://www.opengl.org/registry/](http://www.opengl.org/registry/) and put them in /usr/include/GL/ manually.

The header files gl.h, glu.h and glx.h are included in the proprietary nVidia driver, mesa, glut, freeglut and many more packages.

Direct links:
[glext.h]("http://www.opengl.org/registry/api/glext.h")
[glxext.h]("http://www.opengl.org/registry/api/glxext.h")
[wglext.h]("http://www.opengl.org/registry/api/wglext.h") (Windows)

---

### Post by theraje on 2010-07-22
> **efikkan said:**
> The header files gl.h, glu.h and glx.h are included in the proprietary nVidia driver, mesa, glut, freeglut and many more packages.

Sorry guys, but I am still having problems... I've installed all of the above (including the nVidia driver, since my system uses one anyway), but my usr/include/GL/ directory is still *completely* empty. :?

Is there anything else I could be doing incorrectly? This is getting highly annoying...

---

### Post by kahumba on 2010-07-22
Are you sure you installed freeglut3-dev and not just freeglut3?
Because if you installed the -dev then you should at least have these files:
/usr/include/GL/glut.h
/usr/include/GL/freeglut.h
/usr/include/GL/freeglut_std.h
/usr/include/GL/freeglut_ext.h

(and the gl.h and other headers should have been installed automatically as dependencies)

---

