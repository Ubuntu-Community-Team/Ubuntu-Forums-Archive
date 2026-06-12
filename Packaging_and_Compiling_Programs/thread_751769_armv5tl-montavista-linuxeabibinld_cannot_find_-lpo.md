---
title: "armv5tl-montavista-linuxeabi/bin/ld: cannot find -lpoppler-glib"
date: 2008-04-10
forum: Packaging and Compiling Programs
---

### Post by maphilphilip on 2008-04-10
when i try to compile epdf ,during the make section i got the error as listed





    lfreetype -lz -lpangox-1.0 -lX11 -lpango-1.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   ../src/gtk/libshell-gtk.a -Wl,--export-dynamic -lpoppler-glib -lcairo -lgdk-x11-2.0 -lXrandr -lXfixes -lXcursor -lgdk_pixbuf-2.0 -lpangoxft-1.0 -lXft -lXrender -lXext -lfontconfig -lfreetype -lz -lpangox-1.0 -lX11 -lpango-1.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lcups -lgnutls -lz -lpthread -lm -lcrypt
/usr/lib/gcc/armv5tl-montavista-linuxeabi/3.4.3/../../../../armv5tl-montavista-linuxeabi/bin/ld: cannot find -lpoppler-glib
collect2: ld returned 1 exit status
make[3]: *** [epdfview] Error 1
make[3]: Leaving directory `/home/maphil/epdfview-0.1.6/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/maphil/epdfview-0.1.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maphil/epdfview-0.1.6'
make: *** [all] Error 2
root@10.1.11.14:/home/maphil/epdfview-0.1.6#




anyone please help me how to remove the bug

---

### Post by mc4man on 2008-04-10
try installing libpoppler-glib-dev

---

### Post by maphilphilip on 2008-04-15
Is this poppler-glib another package or is it comes with poppler itself

---

