---
title: "No development packages in default Ubuntu installation"
date: 2008-01-07
forum: Programming Talk
---

### Post by jcgp on 2008-01-07
After a default Ubuntu installation, trying to compile an application produced the error lines below, so it is pretty clear that not even the standard C library headers were installed. How can I install all these development packages, including C, X, Gtk, OpenGL/Mesa etc.?



./engine/gamgi_engine.h:18:20: error: stdlib.h: No such file or directory
./engine/gamgi_engine.h:19:19: error: stdio.h: No such file or directory
./engine/gamgi_engine.h:20:20: error: string.h: No such file or directory
./engine/gamgi_engine.h:21:18: error: math.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:11,
                 from ./engine/gamgi_engine.h:22,
                 from ./engine/gamgi_engine_array.c:12:
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from ./engine/gamgi_engine_array.c:12:
./engine/gamgi_engine.h:24:22: error: X11/Xlib.h: No such file or directory
./engine/gamgi_engine.h:25:19: error: GL/gl.h: No such file or directory
./engine/gamgi_engine.h:26:20: error: GL/glu.h: No such file or directory
./engine/gamgi_engine.h:27:21: error: gtk/gtk.h: No such file or directory
./engine/gamgi_engine.h:28:29: error: gtkgl/gtkglarea.h: No such file or directory

---

### Post by [h2o] on 2008-01-07
installing build-essential package should give you gcc and some other stuff.
The other development files you need to find yourself. They are usually called something-dev.
Good luck!

---

### Post by jcgp on 2008-01-07
Ok,
I installed all the library and header files I needed to compile GAMGI, this is now up and running. In fact I was quite pleased that Ubuntu 7.10 even comes with GtkglArea 1.

I found out that libXmu (X miscellaneous utilities) was not found. A quick look into /usr/lib64 showed the problem, no link to libXmu.so:

-rw-r--r-- 1 root root 101992 2007-07-24 09:00 libXmu.so.6.2.0
-rw-r--r-- 1 root root  13800 2007-07-24 09:00 libXmuu.so.1.0.0
lrwxrwxrwx 1 root root     16 2007-12-05 11:19 libXmuu.so.1 -> libXmuu.so.1.0.0
lrwxrwxrwx 1 root root     15 2007-12-05 11:19 libXmu.so.6 -> libXmu.so.6.2.0

I just added this link manually, with:

sudo ln -s libXmu.so.6 libXmu.so

and libXmu is now recognized. So I guess everyone compiling X applications on Ubuntu 7.10 on xf86_64 might be hit by this minor bug?

Thanks for your quick answer!
Carlos Pereira

---

