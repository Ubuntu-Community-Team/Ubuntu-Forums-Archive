---
title: "undefined reference to `gconf_client_get_bool'"
date: 2006-08-23
forum: Programming Talk
---

### Post by 3saul on 2006-08-23
I'm having problems compiling and linking my application. I have all of the needed libraries and header files. Now that I've added gconf to my app it won't compile (build messages below). Please help.....

[B][I]Building the whole Project: iop ...
make 
make  all-recursive
make[1]: Entering directory `/home/lx1/Projects/iop'
Making all in src
make[2]: Entering directory `/home/lx1/Projects/iop/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall 	 -g -g -O2 -c support.c
/bin/sh ../libtool --mode=link gcc -Wall 	 -g -g -O2  -o iop  support.o main.o -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lX11   
mkdir .libs
gcc -Wall -g -g -O2 -o iop support.o main.o  /usr/lib/libgtk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lX11
main.o: In function `Func_M_Details':/home/lx1/Projects/iop/src/main.c:1201: undefined reference to `gconf_client_get_default'
:/home/lx1/Projects/iop/src/main.c:1205: undefined reference to `gconf_client_get_bool'
collect2: ld returned 1 exit status
make[2]: *** [iop] Error 1
make[2]: Leaving directory `/home/lx1/Projects/iop/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lx1/Projects/iop'
make: *** [all-recursive-am] Error 2
Completed ... unsuccessful
Total time taken: 2 secs[/I][/B]

---

### Post by 3saul on 2006-08-23
ldconfig -p  | grep gconf
        libgconf-2.so.4 (libc6) => /usr/lib/libgconf-2.so.4
        libgconf-2.so (libc6) => /usr/lib/libgconf-2.so
        libgconf-1.so.1 (libc6) => /usr/lib/libgconf-1.so.1
        libgconf-gtk-1.so.1 (libc6) => /usr/lib/libgconf-gtk-1.so.1

---

