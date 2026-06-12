---
title: "Help me create a .deb file for lightwieght volume control appler"
date: 2010-02-09
forum: Packaging and Compiling Programs
---

### Post by Ventil on 2010-02-09
Hi, 

I don't like the gnome-volume-control applet cause it takes a lot of RAM. So I am trying to compile a lightwieght one. It runs in system tray. But I got all kind of trouble and errors with it.

I found the applet on this page [http://www.pcbypaul.com/software/absvolume.shtml](http://www.pcbypaul.com/software/absvolume.shtml)

I need System tray Version: [AbsVolume-4.3.tar.bz2 ](http://www.pcbypaul.com/software/dl/AbsVolume-4.3.tar.bz2)

Could someone make a .deb file for me, please?


Thank you

---

### Post by SevenMachines on 2010-02-10
hi. this isnt really a forum for getting people to create .deb packages for you (although maybe someone will) but more for helping people with compiling and packaging problems. if you have any specific problems your more likely to get help. if you try the advice below and have problems for example.
It sounds like you're just wanting a deb package for installing on your own machine, luckily theres a helpful program for just this situation, checkinstall

In the source code directory (and with build-essential and checkinstall packages installed of course) run,
$./autogen
$make

You can then use checkinstall to create a debain package by running
$sudo checkinstall
and following its questions (the defaults should be fine)

---

### Post by Ventil on 2010-02-10
Hi. 
Thank you for your answer. I tried:

1. $./configure  
didn't work
2.$sh autogen.sh
passed after lots of trouble(needed to install extra libraries)
3. make
don't work

Here is the output:
```
make[1]: Entering directory `/home/marko/Desktop/aa'
Making all in src
make[2]: Entering directory `/home/marko/Desktop/aa/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c: In function &#8216;store_filename&#8217;:
main.c:131: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
main.c: In function &#8216;on_mixer&#8217;:
main.c:145: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
main.c:165: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c:169: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c:188: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c:193: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c: In function &#8216;main&#8217;:
main.c:381: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c:382: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
main.c:383: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result
mv -f .deps/main.Tpo .deps/main.Po
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT actions.o -MD -MP -MF .deps/actions.Tpo -c -o actions.o actions.c
mv -f .deps/actions.Tpo .deps/actions.Po
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT callbacks.o -MD -MP -MF .deps/callbacks.Tpo -c -o callbacks.o callbacks.c
mv -f .deps/callbacks.Tpo .deps/callbacks.Po
gcc  -g -O2   -o absvolume main.o actions.o callbacks.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0    
make[2]: Leaving directory `/home/marko/Desktop/aa/src'
Making all in po
make[2]: Entering directory `/home/marko/Desktop/aa/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/marko/Desktop/aa/po'
make[2]: Entering directory `/home/marko/Desktop/aa'
make[2]: Leaving directory `/home/marko/Desktop/aa'
make[1]: Leaving directory `/home/marko/Desktop/aa'
```


I know about the checkinstall. But that's after "make", right?

---

### Post by SevenMachines on 2010-02-10
from your output it looks like make was successful, it has warnings but no errors. you should be able to run checkinstall now

---

### Post by SevenMachines on 2010-02-10
checkinstall runs after make yes. a typical gnu-type compilation process might look something like this

-configure build for this system
$./configure

- compile the program
$make

- install the program 
$make install

Checkinstall replaces the last step, it pretends to run 'make install' inside of a fake installation environment, sees what files go where, and then creates a package that does the same thing. 
Essentially this means that the package management system can handle installing and removing your compiled program instead of 'make install' / 'make uninstall'

---

### Post by Ventil on 2010-02-10
It worked! It worked!
Thanks a lot SevenMachines

---

### Post by Ventil on 2010-02-10
Finnaly managed to compiled it! Takes 1,2MB of RAM now. It can load a sound mixer too. I love it! ;)

[[img]http://file.si/pthumbs/large/8699/10-02-2010--1265803976_1366x768.jpg[/img]](http://file.si/public/view/8699)


Here is the .deb if someone wants to try it
[http://www.2shared.com/file/11270447/39ce0c3f/absvolume_43-1_i386.html](http://www.2shared.com/file/11270447/39ce0c3f/absvolume_43-1_i386.html)

---

