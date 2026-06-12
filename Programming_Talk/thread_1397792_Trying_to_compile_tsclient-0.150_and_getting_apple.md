---
title: "Trying to compile tsclient-0.150 and getting applet.c:24:42: error: libgnomeui/gnome-"
date: 2010-02-03
forum: Programming Talk
---

### Post by volodymyr on 2010-02-03
Hello,

I am trying to compile TS client under my Karmic x64 and I am stuck :) 

I took the sources from [http://packages.ubuntu.com/source/karmic/tsclient](http://packages.ubuntu.com/source/karmic/tsclient) and I applied the patch. I do ./configure and it works perfectly. I do make and the following error is raised:

```
Making all in applet
make[2]: entrant dans le répertoire « /home/volodymyr/development/tsclient-0.150/applet »
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -DORBIT2=1 -pthread -D_REENTRANT -I/usr/include/panel-2.0 -I/usr/include/gconf/2 -I/usr/include/gtk-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/libbonobo-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/gail-1.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include      -g -O2 -MT applet.o -MD -MP -MF ".deps/applet.Tpo" -c -o applet.o applet.c; \
    then mv -f ".deps/applet.Tpo" ".deps/applet.Po"; else rm -f ".deps/applet.Tpo"; exit 1; fi
applet.c:24:42: error: libgnomeui/gnome-window-icon.h: Aucun fichier ou dossier de ce type
applet.c: In function ‘create_menu’:
applet.c:172: warning: assignment discards qualifiers from pointer target type
applet.c:185: warning: assignment from incompatible pointer type
make[2]: *** [applet.o] Erreur 1
make[2]: quittant le répertoire « /home/volodymyr/development/tsclient-0.150/applet »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/volodymyr/development/tsclient-0.150 »
make: *** [all] Erreur 2
```It seems like here:

```
applet.c:24:42: error: libgnomeui/gnome-window-icon.h: Aucun fichier ou dossier de ce type
```It does not find some header file ... Bizzare. What it could be? There is not much info in google, only two references about this problem leading to dead end :(

---

### Post by dwhitney67 on 2010-02-03
Do you have the libgnomeui-dev package installed on your system?

If so, can you verify whether the header file gnome-window-icon.h exists within /usr/include/libgnomeui?

---

### Post by volodymyr on 2010-02-04
Yes, I got this package installed. However the folder at include is not exactly with the same name ...

$ ls /usr/include/ | grep libgno
libgnome-2.0
libgnomecanvas-2.0
libgnomeui-2.0

---

### Post by volodymyr on 2010-02-04
I made this symbolik link to make sure the headers are properly "seen":

```
sudo ln -s /usr/include/libgnomeui-2.0/libgnomeui /usr/include/libgnomeui
```

However, now I got another error, not related to headers:

```
make[2]: entrant dans le répertoire « /home/volodymyr/development/tsclient-0.150/applet »
gcc  -g -O2   -o tsclient-applet  applet.o support.o rdpfile.o mrulist.o -pthread -lpanel-applet-2 -lgconf-2 -lbonoboui-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   
applet.o: In function `tsclient_applet_create':
/home/volodymyr/development/tsclient-0.150/applet/applet.c:89: undefined reference to `gnome_window_icon_set_default_from_file'
collect2: ld returned 1 exit status
```

---

### Post by dwhitney67 on 2010-02-04
Before ever attempting to 'make' tsclient, did you ever run 'configure'?

It is very odd that your Makefile's CFLAGS does not list the /usr/include/libgnomeui-2.0 path.  Your workaround, to create the symbolic link, it not the proper solution.

Your latest problem is related; the Makefile does not have the -l (lowercase-ell) option for gnomeui-2.0 (or whatever it may be called) library.  Hence the unresolved error that you are getting.

To summarize, re-run the 'configure' again to see if it properly detects that you have the gnomeui-2.0 library installed on your system.

P.S.  I do not have any of these packages on my system; I am working off of gut instinct, and thus I'm expecting for you to ensure that you follow every step properly as documented at the tsclient website, or within the 'README' or similar file that came with the source package.

---

