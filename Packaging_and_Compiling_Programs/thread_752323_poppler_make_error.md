---
title: "poppler make error"
date: 2008-04-11
forum: Packaging and Compiling Programs
---

### Post by maphilphilip on 2008-04-11
Dear all,

           I need poppler-0.5.9 for building epdf.What i have done is i configured the poppler,it works properly by giving all dependencies such as cairo,but during make i stuck with an error

./.libs/libpoppler-glib.so: undefined reference to `g_fopen(char const*, char const*)'
collect2: ld returned 1 exit status


The full error is pasted below


creating libpoppler-glib.la
(cd .libs && rm -f libpoppler-glib.la && ln -s ../libpoppler-glib.la libpoppler-glib.la)
if gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I. -I.. -I../poppler -DG_LOG_DOMAIN=\"Poppler\" -I.. -I../poppler -I/usr/include/cairo   -DXTHREADS -D_REENTRANT -DXUSE_MTSAFE_API -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2    -I/usr/include/cairo                       -g -O2 -MT test-poppler-glib.o -MD -MP -MF ".deps/test-poppler-glib.Tpo" -c -o test-poppler-glib.o test-poppler-glib.c; \
then mv -f ".deps/test-poppler-glib.Tpo" ".deps/test-poppler-glib.Po"; else rm -f ".deps/test-poppler-glib.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc -std=gnu99  -g -O2   -o test-poppler-glib  test-poppler-glib.o ../poppler/libpoppler.la libpoppler-glib.la -Wl,--export-dynamic -lgdk-x11-2.0 -lXrandr -lXfixes -lXcursor -lgdk_pixbuf-2.0 -lpangoxft-1.0 -lXft -lXrender -lXext -lfontconfig -lfreetype -lz -lpangox-1.0 -lX11 -lpango-1.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lfreetype -lz   ../poppler/libpoppler-cairo.la -lcairo
gcc -std=gnu99 -g -O2 -o .libs/test-poppler-glib test-poppler-glib.o -Wl,--export-dynamic  ../poppler/.libs/libpoppler.so ./.libs/libpoppler-glib.so /usr/lib/libgdk-x11-2.0.so -lXrandr -lXfixes -lXcursor /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangoxft-1.0.so -lXft -lXrender -lXext /usr/lib/libfontconfig.so /usr/lib/libpangox-1.0.so -lX11 /usr/lib/libpango-1.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so /usr/lib/libfreetype.so -[COLOR="Red"]lz ../poppler/.libs/libpoppler-[B]cairo.a /usr/lib/libstdc++.so /usr/lib/libcairo.so
./.libs/libpoppler-glib.so: undefined reference to `g_fopen(char const*, char const*)'
collect2: ld returned 1 exit status
make[4]: *** [test-poppler-glib] Error 1
make[4]: Leaving directory `/home/maphil/poppler-0.5.9/glib'[/COLOR]
make[3]: *** [all-recursive] Error 1[/B]make[3]: Leaving directory `/home/maphil/poppler-0.5.9/glib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/maphil/poppler-0.5.9/glib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maphil/poppler-0.5.9'
make: *** [all] Error 2

Please help me to overcome this.......

---

