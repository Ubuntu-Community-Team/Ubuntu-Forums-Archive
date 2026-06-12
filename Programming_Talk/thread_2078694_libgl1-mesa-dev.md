---
title: "libgl1-mesa-dev"
date: 2012-10-31
forum: Programming Talk
---

### Post by thedardanius on 2012-10-31
hey,

si installed libgl1-mesa-dav for opengl xlib programming on linux (with build-essentials too). My question: is this the standard library or it there like many things in linux no standard opengl lib for linux?

And it is quite confusing: on many forums, they use linux as an OS, while Ive just learned linux is only the kernel and NOT the OS. Strange...

---

### Post by xytron on 2012-11-01
> **thedardanius said:**
> hey,

si installed libgl1-mesa-dav for opengl xlib programming on linux (with build-essentials too). My question: is this the standard library or it there like many things in linux no standard opengl lib for linux?

And it is quite confusing: on many forums, they use linux as an OS, while Ive just learned linux is only the kernel and NOT the OS. Strange...


When people say Linux they are almost always referring to the OS, technically Linux is just the kernel and the OS is GNU Linux.

For OpenGL development you'll first want to install libgl1-mesa-dev package it will give you a software implementation of OpenGL and the the headers you need for development.

For example when I compile an OpenGL program that just uses GLX and Xlib I include the following files;


```

#include <X11/Xlib.h>
#include <GL/gl.h>
#include <GL/glx.h>

```

Then you can compile your program with the following line;


```


gcc -g -L /usr/X11R6/lib -lX11  -lGL 



```

---

### Post by thedardanius on 2012-11-01
ok but one thing confuses me:
when I installed ubuntu, I didnt see anywhere to install opengl drivers or any opengl support. On windows,there;s a terrible standard driver, So i downloaded nvidias driver. Is there a similar situation on linux or ubuntu and is there a concept like Video driver on linux anyway, or is it already distruited within the linux kernel???

---

