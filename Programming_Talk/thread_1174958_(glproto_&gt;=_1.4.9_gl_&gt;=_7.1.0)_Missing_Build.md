---
title: "(glproto &gt;= 1.4.9 gl &gt;= 7.1.0) Missing Building Kdrive"
date: 2009-05-31
forum: Programming Talk
---

### Post by cycling_joe on 2009-05-31
I'm trying to build kdrive from Xorg-Server source and I am getting the following error running the "autofgen.sh" script provided.

[B]checking for GL... configure: error: Package requirements (glproto >= 1.4.9 gl >= 7.1.0) were not met:

No package 'gl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GL_CFLAGS
and GL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/B]
I thought libgl1-mesa-dev package would fix it but still receiving the same error.

Any ideas out there?

---

### Post by shariefbe on 2010-01-13
This is old thread i now. antway i am facing this similar problem now. The difference is i am trying to compile from "ltib". So i tries to install "gl"(ie mesa) but there i am getting these below errors
```
SOURCE -DPTHREADS -DHAVE_POSIX_MEMALIGN -DUSE_XSHM  glx_api.c -o glx_api.o
In file included from glx_api.c:34:
../../../../../include/GL/glx.h:38: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make[5]: *** [glx_api.o] Error 1


```please help me

---

### Post by Zugzwang on 2010-01-13
> **shariefbe said:**
> 
[/code]please help me

You need to install a missing package: [http://packages.ubuntu.com/search?searchon=contents&keywords=Xlib.h&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=Xlib.h&mode=exactfilename&suite=karmic&arch=any)

---

### Post by shariefbe on 2010-01-13
i solved this problem after installing the X!! package and i copied the X11 folder from PREFIX and stored in Mesa/include. Now it works fine. thanks a lot.
But i am getting different error now. when i try to compile "libXfont" i am getting this error
```

checking for FONTCACHEPROTO... yes
checking for gzopen in -lz... no
configure: error: *** zlib is required
Configuration of glib library  has failed
sharief@sharief-desktop:/mnt/freescale/sources/xwindow/libXfont-1.3.3$ vim configure

```
I searched but i didnt get it. Please help me

---

