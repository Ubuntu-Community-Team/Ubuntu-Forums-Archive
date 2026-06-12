---
title: "Need help compiling gtk 2.10.9.."
date: 2007-02-13
forum: Programming Talk
---

### Post by eitan_a on 2007-02-13
Hey guys...i'm trying to compile gtk 2.10.9 but have run into a brick wall.  I believe I have all the dependencies needed.  ./configure runs fine, but when I do make, I get these errors halfway through...

```

make[3]: Entering directory `/home/eitan/Desktop/gtk+-2.10.9/gtk'
make[3]: `gtk-update-icon-cache' is up to date.
make[3]: Leaving directory `/home/eitan/Desktop/gtk+-2.10.9/gtk'
GDK_PIXBUF_MODULE_FILE=../gdk-pixbuf/gdk-pixbuf.loaders ./gtk-update-icon-cache --force --ignore-theme-index            \
           --source builtin_icons stock-icons > gtkbuiltincache.h.tmp &&        \
        mv gtkbuiltincache.h.tmp gtkbuiltincache.h
/home/eitan/Desktop/gtk+-2.10.9/gtk/.libs/lt-gtk-update-icon-cache: symbol lookup error: /home/eitan/Desktop/gtk+-2.10.9/gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so.0: undefined symbol: g_type_register_static_simple
make[2]: *** [gtkbuiltincache.h] Error 127
make[2]: Leaving directory `/home/eitan/Desktop/gtk+-2.10.9/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eitan/Desktop/gtk+-2.10.9'
make: *** [all] Error 2

```

Any suggestions will be much appreciated!  Thanks!

---

### Post by eitan_a on 2007-02-15
bump...still would love to hear suggestions

---

