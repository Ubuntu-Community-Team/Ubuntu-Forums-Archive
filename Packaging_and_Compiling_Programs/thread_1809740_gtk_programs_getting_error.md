---
title: "gtk programs getting error"
date: 2011-07-22
forum: Packaging and Compiling Programs
---

### Post by suryak on 2011-07-22
OS: Ubuntu Karmic

I installed libgtk2.0-dev [ gtk lib for GUI] using synaptic manager.
I wrote a sample test program which was given in a tutorial which mainly opens a window.

I used the following code to compile at terminal:

 ```
gcc -o simple simple.c `pkg-config --libs --cflags gtk+-2.0`
```

I am getting the following error :
```
/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

```

why this is happening . how do I fix this.

when I entered :
```
pkg-config --libs --cflags gtk+-2.0
```

I got the following :
```
-D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 
```

why this error is coming. how do i fix it. I have very less knowledge in linux .. so please describe in detail.

Thanks!

---

### Post by suryak on 2011-07-22
when I entered :
```
$ pkg-config --libs gtk+2.0

```

its saying ...
[PHP]Package gtk+2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+2.0' found
[/PHP]

---

### Post by bapoumba on 2011-07-22
Moved to Packaging and Compiling Programs.

---

### Post by .... on 2011-07-23
If your program is small, can you post the code?

---

### Post by .... on 2011-07-23
> **suryak said:**
> when I entered :
```
$ pkg-config --libs gtk+2.0

```

its saying ...
[PHP]Package gtk+2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+2.0' found
[/PHP]
You forgt the '-' in gtk+**-**2.0

---

