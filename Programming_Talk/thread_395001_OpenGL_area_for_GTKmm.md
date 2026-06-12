---
title: "OpenGL area for GTKmm"
date: 2007-03-27
forum: Programming Talk
---

### Post by Laterix on 2007-03-27
I'm playing around and learning to program GTK+OpenGL software. I would like to use GTK-ui for my program with an area for OpenGL graphics. I use C++ and GTKmm librarys. Is there some good OpenGL drawing area widgets available?

I found GtkGLareamm with google, but I can't find where to download it. There is also something called GtkGLExt. Is this for me?

---

### Post by lnostdal on 2007-03-27
yes, you probably want gtkglext .. there are c++ bindings to it named gtkglextmm

---

### Post by Laterix on 2007-03-27
> **lnostdal said:**
> yes, you probably want gtkglext .. there are c++ bindings to it named gtkglextmm
I installed this, but the compilation doesn't seem to find it. I have include like example GTKGLmm apps:
```

#include <gtkglmm.h>

```
and compiler says
```

test.cpp:10:21: error: gtkglmm.h: No such file or directory

```
This is my compile command
```

g++ -Wall test.cpp -o test `pkg-config gtkmm-2.4 --cflags --libs`

```
Any help is appriciated!

---

### Post by lnostdal on 2007-03-28
Try..
```

$ pkg-config --list-all | grep gtkgl

```

..and add a `pkg-config ...` as needed.

---

### Post by Laterix on 2007-03-28
Thank you for your help, but I still can't get it to work. Now my compile command is
```

g++ -Wall test.cpp -o test -lGL -lGLU `pkg-config gtkmm-2.4 --cflags --libs` `pkg-config gtkglextmm-x11-1.2 --cflags --libs`

```
And it compiles without any errors or warnings. But when i run the executable I get
```

./test: error while loading shared libraries: libgtkglextmm-x11-1.2.so.0: cannot open shared object file: No such file or directory

```
Anyway, gtkglextmm example appilcations compile and work just fine.

Maybe this is helpfull
```

[late@oiva gtkmm]$ locate libgtkglextmm-
/usr/lib/libgtkglextmm-x11-1.0.so.0.0.1
/usr/lib/libgtkglextmm-x11-1.0.so.0
/usr/lib/libgtkglextmm-x11-1.0.a
/usr/lib/libgtkglextmm-x11-1.0.la
/usr/lib/libgtkglextmm-x11-1.0.so
/usr/local/lib/libgtkglextmm-x11-1.2.la
/usr/local/lib/libgtkglextmm-x11-1.2.a
/usr/local/lib/libgtkglextmm-x11-1.2.so.0.0.0
/usr/local/lib/libgtkglextmm-x11-1.2.so
/usr/local/lib/libgtkglextmm-x11-1.2.so.0

```

---

### Post by Laterix on 2007-03-28
Ok, it seems that I'm now alone with this problem. There is a [bug report at launchpad.]("https://launchpad.net/ubuntu/+source/gtkglextmm/+bugs")

Now, my question is. How do I compile and install this myself so that I can use it and not the one in the repositories?

---

