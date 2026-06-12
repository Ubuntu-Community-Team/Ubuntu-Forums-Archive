---
title: "gcc compilation error: can't link required Gtk2.0 libraries"
date: 2017-05-26
forum: Packaging and Compiling Programs
---

### Post by CosmicFlux on 2017-05-26
Hi,

I have a C program that uses the Gtk2 toolkit. When I try to compile with **gcc -o start2 start.c 'pkg-config --cflags --libs gtk-2.0'** I get the following error:

```
gcc: error: pkg-config --cflags --libs gtk-2.0: No such file or directory

```

Sometimes its **gio.h** that's missing, other times its **glib**, but all the required files are there. I know this because I have checked.

However, when I link to all dependencies individually using -I the program compiles. 

```
gcc -o start2 start.c -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangocairo-1.0 -latk-1.0 -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0 -lfontconfig -lfreetype

```

My question is what am I doing wrong that I have to manually request all libraries individually?

Thanks in advance,

CF

P.S. - I know from my Google searching this is a common query, and I've tried a range of solutions suggested to no avail, so apologies if this seems repetitive.

---

### Post by steeldriver on 2017-05-26
You're using the wrong type of quotes - for *command substitution* you need backticks not straight single quotes:

```

gcc -o start2 start.c **[COLOR=#ff0000]`[/COLOR]**pkg-config --cflags --libs gtk-2.0**[COLOR=#ff0000]`[/COLOR]**

```

or using the newer $(...) syntax

```

gcc -o start2 start.c [COLOR=#ff0000]$([/COLOR]pkg-config --cflags --libs gtk-2.0[COLOR=#ff0000])[/COLOR]

```

---

