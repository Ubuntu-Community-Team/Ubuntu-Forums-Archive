---
title: "Compiling VIVE 2.0.0beta2"
date: 2007-07-18
forum: Programming Talk
---

### Post by alexef on 2007-07-18
Hi all!

I'm a Feisty user, trying to build Vive ( [http://vive.sourceforge.net/](http://vive.sourceforge.net/) ) and I'm stuck here:

> alex@alex-laptop:~/svn/vive/2.0.0$ make
make  all-recursive
make[1]: Entering directory `/home/alex/svn/vive/2.0.0'
Making all in src
make[2]: Entering directory `/home/alex/svn/vive/2.0.0/src'
make[3]: Entering directory `/home/alex/svn/vive/2.0.0'
make[3]: Leaving directory `/home/alex/svn/vive/2.0.0'
gcc  -g -O2 -D PREFIX=\"/usr/local\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -o vive error.o interface.o options.o preferences.o presets.o combo_menus.o encode.o dvd.o tooltips.o vive.o  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -lvte
combo_menus.o: In function `populate_ffmpeg':
/home/alex/svn/vive/2.0.0/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/alex/svn/vive/2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/alex/svn/vive/2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/alex/svn/vive/2.0.0/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/alex/svn/vive/2.0.0/src/combo_menus.c:94: undefined reference to `first_avcodec'
collect2: ld returned 1 exit status
make[2]: *** [vive] Error 1


I have installed ffmpeg, libavcodec(-dev), libavformat(-dev), and tried a lot of forums suggestions, but no succes. I believe there must be somthing related to /usr/lib and /usr/local/lib, because I also had some problems trying to build gtkpod.

Thanks anticipated!

---

### Post by zcold on 2009-04-04
I am also having this problem.

```

-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -o vive error.o interface.o options.o preferences.o presets.o combo_menus.o encode.o dvd.o tooltips.o vive.o  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -pthread -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0   -pthread -lgnomevfs-2 -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0   -lvte
combo_menus.o: In function `populate_ffmpeg':
/home/fuckwad/vive-2.0.0/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/fuckwad/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/fuckwad/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/fuckwad/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/fuckwad/vive-2.0.0/src/combo_menus.c:94: undefined reference to `first_avcodec'
collect2: ld returned 1 exit status
make[2]: *** [vive] Error 1
make[2]: Leaving directory `/home/fuckwad/vive-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fuckwad/vive-2.0.0'
make: *** [all] Error 2

```

all I want is a working gui for ffmpeg.. stick with cl for now i guess.

---

