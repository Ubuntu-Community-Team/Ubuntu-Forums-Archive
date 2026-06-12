---
title: "Problem compililng MythTV - ld: cannot find -lXxf86vm"
date: 2006-02-21
forum: Programming Talk
---

### Post by oblib on 2006-02-21
I am trying to compile mythtv 0.19 and get the error ```
. . . -L/usr/X11R6/lib -lXinerama -lXv -lXxf86vm -lXrandr -lXvMCW -lXvMC -lGL -lGLU -lqt-mt -lXext -lX11 -lm -lpthread
/usr/bin/ld: cannot find -lXxf86vm
``` 
locate returns /usr/lib/libXxf86vm.so.1.0.0 and /usr/lib/libXxf86vm.so.1, which leads me to believe that it is just looking in the wrong place. 

So I changed the make file to look in /usr/lib rather than /usr/X11R6/lib and it comes back with the same error. I tried changing the compiler to CC=gcc-3.4 as well, with no results. Can anyone help?

I've got x-window-system-dev. I must be missing some other package.

---

### Post by hod139 on 2006-02-21
Install the libXxf86vm-dev package

---

