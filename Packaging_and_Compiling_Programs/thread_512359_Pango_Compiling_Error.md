---
title: "Pango Compiling Error"
date: 2007-07-29
forum: Packaging and Compiling Programs
---

### Post by freonix on 2007-07-29
> make  all-recursive
make[1]: Entering directory `/home/freonix/pango-0.26'
Making all in pango
make[2]: Entering directory `/home/freonix/pango-0.26/pango'
Making all in mini-fribidi
make[3]: Entering directory `/home/freonix/pango-0.26/pango/mini-fribidi'
/bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DSYSCONFDIR=\"/usr/local/etc\" -DLIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -I../..    -g -O2 -Wall -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include   -c fribidi.c
rm -f .libs/fribidi.lo
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DSYSCONFDIR=\"/usr/local/etc\" -DLIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -I../.. -g -O2 -Wall -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -c fribidi.c  -fPIC -DPIC -o fribidi.o
fribidi.c: In function 'new_type_link':
fribidi.c:102: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
fribidi.c:102: error: 'mem_chunk' undeclared (first use in this function)
fribidi.c:102: error: (Each undeclared identifier is reported only once
fribidi.c:102: error: for each function it appears in.)
fribidi.c:106: warning: implicit declaration of function 'g_mem_chunk_create'
fribidi.c:106: error: expected expression before 'TypeLink'
fribidi.c:108: warning: implicit declaration of function 'g_chunk_new'
fribidi.c:108: error: expected expression before 'TypeLink'
fribidi.c:108: warning: assignment makes pointer from integer without a cast
make[3]: *** [fribidi.lo] Error 1
make[3]: Leaving directory `/home/freonix/pango-0.26/pango/mini-fribidi'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/freonix/pango-0.26/pango'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/freonix/pango-0.26'
make: *** [all-recursive-am] Error 2
freonix@freonix-laptop:~/pango-0.26$ 




Help! Just installed Ubuntu and thought I give it a try. When I was installing Pango, the ./configure was ok but when I want to make , it gives me error. Log above.

Help~

---

