---
title: "GTK2 compile failing on glibconfig.h"
date: 2012-02-20
forum: Packaging and Compiling Programs
---

### Post by MidnightJava on 2012-02-20
I'm trying to compile a program that depends on gtk, and I get the following failure when I run make

```
gcc  -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -g -O3 -msse -msse3 -ffast-math -march=core2 -Wall -c -o agc.o agc.c
In file included from /usr/include/glib-2.0/glib/galloca.h:34:0,
                 from /usr/include/glib-2.0/glib.h:32,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from agc.c:30:
/usr/include/glib-2.0/glib/gtypes.h:34:24: fatal error: glibconfig.h: No such file or directory
compilation terminated.
make: *** [agc.o] Error 1

```

locate glibconfig.h returns
```
/usr/lib/x86_64-linux-gnu/glib-2.0/include/glibconfig.h
```

When I do apt-get show on glib, gtk, and other packages in the dependency chain, they all have Architecture amd64. I've tried removing and re-installing gtk and glib, but I still get the same error.  I don't know what else to check for. I'm not a C developer, and these kind of compile errors mystify me.

---

### Post by SevenMachines on 2012-02-21
gtk has a long list of dependencies that are a pain to do by hand. Best try using pkg-config to generate them instead. for example,
```
gcc -o testprog testprog.c `pkg-config --cflags --libs gtk+-2.0`
```Note how many flags this actually generates automatically that you would have to do by hand
```
$ pkg-config --cflags --libs gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  
```

---

### Post by MidnightJava on 2012-02-21
Thanks. I'm not sure if I understood your reply correctly. I ran the pkg-config command you gave me and got output analogous to what you indicated. I set CFLAGS to the output of the pkg-config command and ran make again, and got the same error. Was I supposed to do something different?

---

### Post by SevenMachines on 2012-02-21
You don't need to set cflags or anything else manually. See the first command line previously, the pkg-config command is run as part of the gcc compilation line. Since the pkg-config command is included between `backquotes`, it is run and the output inserted into the command line automatically

---

### Post by MidnightJava on 2012-02-21
Thanks, that worked. I changed the gcc command in the make file to include the pkg-config call inside the back-ticks, and it compiled and installed successfully. Much appreciated.

---

