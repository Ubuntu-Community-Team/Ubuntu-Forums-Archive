---
title: "TiLem program won't &quot;make&quot;"
date: 2011-02-14
forum: Programming Talk
---

### Post by searchfgold6789 on 2011-02-14
Hi.
I just downloaded the source for a program called TiLem - A Graphing calculator emulator that I need for school. I have installed all of its dependencies, and successfully ./configure'd it but when I run make, a bunch of errors occur. sudo make install does not work either - Does anyone know what they mean or how to solve them?```
richie@richie-desktop:~/Downloads/tilem-0.972$ make
cd src && make
make[1]: Entering directory `/home/richie/Downloads/tilem-0.972/src'
cd tilem && make
make[2]: Entering directory `/home/richie/Downloads/tilem-0.972/src/tilem'
gcc -g -O2 -O2 -c -Wall main.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/usr/local/include/tilp  
In file included from /usr/local/include/tilp/ticables.h:29,
                 from main.c:47:
/usr/local/include/tilp/cabl_def.h:29:21: error: stdints.h: No such file or directory
In file included from /usr/local/include/tilp/ticables.h:29,
                 from main.c:47:
/usr/local/include/tilp/cabl_def.h:126: warning: parameter names (without types) in function declaration
/usr/local/include/tilp/cabl_def.h:127: error: expected ‘)’ before ‘*’ token
/usr/local/include/tilp/cabl_def.h:128: error: expected ‘;’ before ‘int’
In file included from /usr/local/include/tilp/ticables.h:30,
                 from main.c:47:
/usr/local/include/tilp/cabl_int.h:121: error: expected ‘)’ before ‘data’
/usr/local/include/tilp/cabl_int.h:122: error: expected ‘)’ before ‘*’ token
main.c: In function ‘main’:
main.c:214: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
main.c:225: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
main.c:226: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
main.c:258: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
main.c:260: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
main.c:262: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/richie/Downloads/tilem-0.972/src/tilem'
make[1]: *** [xtilem] Error 2
make[1]: Leaving directory `/home/richie/Downloads/tilem-0.972/src'
make: *** [compile] Error 2
```
Having this emulator beats having to save up 100$ for a new graphing calculator - thank you linux and ubuntuforums!

---

### Post by searchfgold6789 on 2011-02-14
...Bump

---

### Post by Arand on 2011-02-14
I just compiled it successfully here, make sure you have libgtk2.0-dev installed and have run ./configure after installing that.

I also have ubuntu-dev-tools installed, but I don't know if that makes a difference.

- arand

---

### Post by searchfgold6789 on 2011-02-14
I have that installed ...
But I just found out that I had the wrong source package. I have the one for Windows.
Could you give me a link to the one you have???

---

### Post by Arand on 2011-02-14
[http://sourceforge.net/projects/tilem/files/tilem-devel/0.973/](http://sourceforge.net/projects/tilem/files/tilem-devel/0.973/)

Also, a tip is to use checkinstall (instead of "make install" command), thus you can easily uninstall it.

- arand

---

### Post by searchfgold6789 on 2011-02-14
Well, I downloaded the correct source code. Thanks for the link. While running 'make', I still get errors though. Thank you for the help so far!
```

richie@richie-desktop:~/Downloads/tilem-0.973$ make
cd src && make
make[1]: Entering directory `/home/richie/Downloads/tilem-0.973/src'
cd tilem && make
make[2]: Entering directory `/home/richie/Downloads/tilem-0.973/src/tilem'
gcc -g -O2  -O2 -c main.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/usr/local/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
main.c: In function ‘main’:
main.c:288: warning: assignment discards qualifiers from pointer target type
main.c:214: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
gcc -g -O2  -O2 -c tools.c -DSHARE_DIR=\"/usr/local/share\" -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   
gcc -g -O2  -O2 -c gui/screen.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/local/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
gui/screen.c: In function ‘lcfresh’:
gui/screen.c:142: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
gcc -g -O2  -O2 -c gui/files.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
gui/files.c: In function ‘create_filedlg’:
gui/files.c:129: warning: passing argument 3 of ‘gtk_signal_connect_full’ from incompatible pointer type
/usr/include/gtk-2.0/gtk/gtksignal.h:119: note: expected ‘GCallback’ but argument is of type ‘filewinfunc’
gui/files.c:130: warning: passing argument 3 of ‘gtk_signal_connect_full’ from incompatible pointer type
/usr/include/gtk-2.0/gtk/gtksignal.h:119: note: expected ‘GCallback’ but argument is of type ‘filewinfunc’
gui/files.c:131: warning: passing argument 3 of ‘gtk_signal_connect_full’ from incompatible pointer type
/usr/include/gtk-2.0/gtk/gtksignal.h:119: note: expected ‘GCallback’ but argument is of type ‘filewinfunc’
gcc -g -O2  -O2 -c gui/changehw.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
gui/changehw.c: In function ‘add_rom’:
gui/changehw.c:200: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
gui/changehw.c: In function ‘changehw’:
gui/changehw.c:273: warning: assignment discards qualifiers from pointer target type
In file included from /usr/include/stdio.h:910,
                 from /usr/include/pango-1.0/pango/pango-utils.h:25,
                 from /usr/include/pango-1.0/pango/pango.h:46,
                 from /usr/include/gtk-2.0/gdk/gdktypes.h:37,
                 from /usr/include/gtk-2.0/gdk/gdkscreen.h:32,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:31,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from gui/changehw.c:22:
In function ‘snprintf’,
    inlined from ‘changehw’ at gui/changehw.c:276:
/usr/include/bits/stdio2.h:65: warning: call to __builtin___snprintf_chk will always overflow destination buffer
gcc -g -O2  -O2 -c gui/menus.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
gcc -g -O2  -O2 -c gui/commands.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
gcc -g -O2  -O2 -c gui/linkset.c -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/local/include/tilp2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
In file included from gui/linkset.c:30:
gui/../core/dep/link.h:11: error: conflicting types for ‘CableOptions’
/usr/local/include/tilp2/ticables.h:253: note: previous declaration of ‘CableOptions’ was here
gui/linkset.c: In function ‘setuplink’:
gui/linkset.c:61: warning: assignment discards qualifiers from pointer target type
gui/linkset.c:64: warning: assignment discards qualifiers from pointer target type
make[2]: *** [linkset.o] Error 1
make[2]: Leaving directory `/home/richie/Downloads/tilem-0.973/src/tilem'
make[1]: *** [xtilem] Error 2
make[1]: Leaving directory `/home/richie/Downloads/tilem-0.973/src'
make: *** [compile] Error 2
```

---

### Post by Arand on 2011-02-14
I think I managed to reproduce your error by having the packages```
libticables-dev libticalcs-dev libticonv-dev
```installed, so you might want to try to uninstall them?

Unless you absolutely need them, in which case [http://sourceforge.net/projects/tilem/forums/forum/84646/topic/3533313](http://sourceforge.net/projects/tilem/forums/forum/84646/topic/3533313) has some (not very helpful) discussion regarding it.

My guess is that if you uninstall them tilem will simply be compiled without support for link cables

- arand

---

### Post by searchfgold6789 on 2011-02-16
I tried to purge those three packages, and I ./configure'd it again, successfully, but it still did not make successfully!
Thanks for the help so far. Really!

---

### Post by linuxman94 on 2011-06-19
If you're still need help, try getting the cvs version by typing:

```
cvs -d:pserver:anonymous@tilem.cvs.sourceforge.net:/cvsroot/tilem login

cvs -z3 -d:pserver:anonymous@tilem.cvs.sourceforge.net:/cvsroot/tilem co -P TiLem
``` 

Just leave the password blank.  Then cd into the directory with the source and compile

---

