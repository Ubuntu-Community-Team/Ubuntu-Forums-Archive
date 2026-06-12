---
title: "Error when using make &quot;client.c:108:5: error: too many arguments to function&quot;"
date: 2014-04-05
forum: Programming Talk
---

### Post by r530er on 2014-04-05
When i try to use make a get errors:

> 
make  all-recursive
make[1]: Entering directory `/home/sander/Downloads/volnoti'
Making all in src
make[2]: Entering directory `/home/sander/Downloads/volnoti/src'
depbase=`echo client.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
    gcc -DHAVE_CONFIG_H -I. -I..  -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -pthread -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -DPREFIX="\"/usr/share/pixmaps/volnoti/\""   -g -O2 -MT client.o -MD -MP -MF $depbase.Tpo -c -o client.o client.c &&\
    mv -f $depbase.Tpo $depbase.Po
client.c: In function &#8216;main&#8217;:
client.c:108:5: warning: passing argument 3 of &#8216;uk_ac_cam_db538_VolumeNotification_notify&#8217; makes pointer from integer without a cast [enabled by default]
value-client-stub.h:29:1: note: expected &#8216;struct GError **&#8217; but argument is of type &#8216;int&#8217;
client.c:108:5: error: too many arguments to function &#8216;uk_ac_cam_db538_VolumeNotification_notify&#8217;
value-client-stub.h:29:1: note: declared here
make[2]: *** [client.o] Error 1
make[2]: Leaving directory `/home/sander/Downloads/volnoti/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sander/Downloads/volnoti'
make: *** [all] Error 2



And this is what is in the dir (If it at all matters):

> 
aclocal.m4      ChangeLog       compile      config.h.in~   configure     depcomp     Makefile     missing     pkg         README.md  stamp-h1
AUTHORS         CMakeCache.txt  config.h     config.log     configure.ac  INSTALL     Makefile.am  NEWS        prepare.sh  res
autom4te.cache  CMakeFiles      config.h.in  config.status  COPYING       install-sh  Makefile.in  package.sh  README      src


---

### Post by r530er on 2014-04-05
here is a --debug version:

> 
[FONT=courier new]Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for x86_64-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `all' does not exist.
   File `all-am' does not exist.
     File `volnoti-show' does not exist.
       File `client.o' does not exist.
      Must remake target `client.o'.
make[2]: Entering directory `/home/sander/Downloads/volnoti/src'
depbase=`echo client.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
    gcc -DHAVE_CONFIG_H -I. -I..  -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -pthread -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -DPREFIX="\"/usr/share/pixmaps/volnoti/\""   -g -O2 -MT client.o -MD -MP -MF $depbase.Tpo -c -o client.o client.c &&\
    mv -f $depbase.Tpo $depbase.Po
client.c: In function &#8216;main&#8217;:
client.c:108:5: warning: passing argument 3 of &#8216;uk_ac_cam_db538_VolumeNotification_notify&#8217; makes pointer from integer without a cast [enabled by default]
value-client-stub.h:29:1: note: expected &#8216;struct GError **&#8217; but argument is of type &#8216;int&#8217;
client.c:108:5: error: too many arguments to function &#8216;uk_ac_cam_db538_VolumeNotification_notify&#8217;
value-client-stub.h:29:1: note: declared here
make[2]: *** [client.o] Error 1
make[2]: Leaving directory `/home/sander/Downloads/volnoti/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sander/Downloads/volnoti'
make: *** [all] Error 2[/FONT]


---

### Post by ofnuts on 2014-04-05
Nothing to do with make. There is a problem with the code you are compiling:
```

[FONT=courier new] client.c:108:5: error: too many arguments to function &#8216;uk_ac_cam_db538_VolumeNotification_notify&#8217;[/FONT]
```[FONT=courier new]
[/FONT]
You get this error like this because the function usage in the code doesn't match the function declaration. If you are recompiling someone else's code, it's likely because the code includes header files from some library and you and the author are using different (and incompatible) versions. So right now you have to find where [FONT=courier new]uk_ac_cam_db538_VolumeNotification_notify[/FONT] is declared and why it is declared that way (wrong version, missing conditional includes (any compile configuration script to run?)

---

### Post by r530er on 2014-04-06
Umm, yeah, this is my "First cup of Ubuntu" so I am not able to understand that, sorry. Could you please explain like I'm 5. Tho I'm guessing that I need to update header-somethings (I don't know what they are :P) Thanks for the quick reply btw. :)

---

### Post by steeldriver on 2014-04-06
OK so I pulled the git repo and had a play with this for you

It looks like the problem is within the source distribution itself - the supplied src/client.c file is not compatible with the supplied src/value-client-stub.h

I *think* that's slipped through because the author is intending for the value-client-stub.h (and value-daemon-stub.h) to be regenerated on the local system, however despite having build targets for them, they don't seem to get recreated without manual intervention. That *may* be because the timestamps get messed up by the git clone.

Here's what seemed to work for me - basically cd to the volnoti/src subdirectory and remove and re-make those two header files:

```

/src/volnoti$ cd src
/src/volnoti/src$ 
/src/volnoti/src$ rm value-client-stub.h && make value-client-stub.h
dbus-binding-tool --prefix=volume_object --mode=glib-client \
      specs.xml > value-client-stub.h
/src/volnoti/src$ rm value-daemon-stub.h && make value-daemon-stub.h
dbus-binding-tool --prefix=volume_object --mode=glib-server \
      specs.xml > value-daemon-stub.h
/src/volnoti/src$ 

```

Hope this helps

---

### Post by r530er on 2014-04-06
Yes it did! :D Thanks alot! :DDD

---

