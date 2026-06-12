---
title: "GTK+ Problem."
date: 2011-12-13
forum: Programming Talk
---

### Post by basil2style on 2011-12-13
I am new to gtk gui programming.i install gtk,glib,pango,atk..etc lib from  package manager.

when i compiled codes from a book "Foundation of GTK+ development"
I got an error that "gtk/gtk.h"is not in directory.

---

### Post by SevenMachines on 2011-12-14
You need to add gtk's include directory and libraries to the compile command. There can be a lot of them, so you can use pkg-config to sort it all out for you. An example...
```
$ gcc -o example example.c `pkg-config --cflags --libs gtk+-2.0`
```Note, those are backquotes surrounding the pkg-config command, it means it will be replaced with the output, ie
```
$ pkg-config --cflags --libs gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0 
```Thats why its better to use pkg-config than type it in :)

---

### Post by basil2style on 2011-12-14
Thanks for your response @sevenmachines.Let me try it.

---

