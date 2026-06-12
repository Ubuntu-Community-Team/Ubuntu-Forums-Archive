---
title: "Opengl 2.0 or shader extensions help..."
date: 2006-11-10
forum: Programming Talk
---

### Post by bodiddlie on 2006-11-10
I was interested in trying to get into a little glsl coding, so I was checking out a tutorial and it mentioned using GLEW to check for either OpenGL 2.0 support or for the ARB extenstions, so I borrowed the code from the tutorial and it says that I have no support for either.  

I've got mesa 6.5.1 and the current repo version of the nvidia driver for my card.  Any ideas?  I'm away from my linux box for the time being so I can't post any output unfortunately.

-bodiddlie

---

### Post by hod139 on 2006-11-27
You can try installing the nvidia-glx-dev package, but then make sure you read the README about moving 
```
usr/share/doc/nvidia-glx-dev/include/GL/gl.h
```
to /usr/include/GL.  That will get you the nvidia specific shader extensions.  

Installing mesa-common-dev should install the mesa API, which I think supports openGL 2.0, but I could be wrong.

---

