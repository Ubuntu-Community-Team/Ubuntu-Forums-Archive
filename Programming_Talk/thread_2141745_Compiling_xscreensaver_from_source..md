---
title: "Compiling xscreensaver from source."
date: 2013-05-03
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2013-05-03
Putting together an all-encompassing matrix theme (yeah, go ahead and boo :P ) for my xubuntu install, even creating a custom x11 cursor theme based on the icons from StarCraft (look pretty nice too, I've smoothed the default animations alot, expect it to be on gnome-look et all). And as a bit of a vanity shot I've rewrote the xmatrix.c source code to reference my handle instead of Neo. Problem is I'm having hell compiling it. I got the code from github, ./configure, make, make install etc. But its not working with the gdk-pixbuf. Error message:
```
make[1]: Entering directory `/home/ntzrmtthihu777/.src/xscreensaver-debian-5.10-3ubuntu4/utils'
make[1]: Nothing to be done for `default'.
make[1]: Leaving directory `/home/ntzrmtthihu777/.src/xscreensaver-debian-5.10-3ubuntu4/utils'
make[1]: Entering directory `/home/ntzrmtthihu777/.src/xscreensaver-debian-5.10-3ubuntu4/driver'
WARNING: neither GTK nor Motif are available, therefore no xscreensaver-demo!
gcc -pedantic -Wall -Wstrict-prototypes -Wnested-externs -Wmissing-prototypes -Wno-overlength-strings -Wdeclaration-after-statement -std=c89 -U__STRICT_ANSI__ -c -I. -I. -I./../utils -I..  -pthread -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -DHAVE_CONFIG_H -g -O2  xscreensaver-getimage.c
xscreensaver-getimage.c: In function ‘read_file_gdk’:
xscreensaver-getimage.c:390:34: error: too few arguments to function ‘gdk_pixbuf_new_from_file’
In file included from ../gdk-pixbuf/gdk-pixbuf.h:35:0,
                 from ../gdk-pixbuf/gdk-pixbuf-xlib.h:24,
                 from xscreensaver-getimage.c:58:
../gdk-pixbuf/gdk-pixbuf-core.h:290:12: note: declared here
xscreensaver-getimage.c:413:9: warning: ‘gdk_pixbuf_unref’ is deprecated (declared at ../gdk-pixbuf/gdk-pixbuf-core.h:243): Use 'g_object_unref' instead [-Wdeprecated-declarations]
xscreensaver-getimage.c:430:15: warning: ‘gdk_pixbuf_unref’ is deprecated (declared at ../gdk-pixbuf/gdk-pixbuf-core.h:243): Use 'g_object_unref' instead [-Wdeprecated-declarations]
make[1]: *** [xscreensaver-getimage.o] Error 1
make[1]: Leaving directory `/home/ntzrmtthihu777/.src/xscreensaver-debian-5.10-3ubuntu4/driver'
make: *** [default] Error 5


```

Would someone more 1337 than I care to assist?

Nevermind, seems I got it. I got the source from apt-get instead of github, seems to be woring.

---

