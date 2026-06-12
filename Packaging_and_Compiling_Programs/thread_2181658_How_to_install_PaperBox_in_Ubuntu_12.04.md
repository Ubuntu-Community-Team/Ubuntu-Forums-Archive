---
title: "How to install PaperBox in Ubuntu 12.04"
date: 2013-10-18
forum: Packaging and Compiling Programs
---

### Post by WttcGTw on 2013-10-18
I quite liked the screenshot of PaperBox as a GUI for Tracker and tried to
install PaperBox on Ubuntu 12.04. The configuration went ok but make gave me
the following output:

```
user@user:~/paperbox-0.4.4$ make
make all-recursive
make[1]: Entering directory `/home/user/paperbox-0.4.4'
Making all in data
make[2]: Entering directory `/home/user/paperbox-0.4.4/data'
Making all in icons
make[3]: Entering directory `/home/user/paperbox-0.4.4/data/icons'
Making all in 16x16
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/16x16'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/16x16'
Making all in 22x22
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/22x22'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/22x22'
Making all in 24x24
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/24x24'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/24x24'
Making all in 32x32
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons/scalable'
make[4]: Entering directory `/home/user/paperbox-0.4.4/data/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/user/paperbox-0.4.4/data/icons'
make[3]: Leaving directory `/home/user/paperbox-0.4.4/data/icons'
make[3]: Entering directory `/home/user/paperbox-0.4.4/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/user/paperbox-0.4.4/data'
make[2]: Leaving directory `/home/user/paperbox-0.4.4/data'
Making all in po
make[2]: Entering directory `/home/user/paperbox-0.4.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/paperbox-0.4.4/po'
Making all in src
make[2]: Entering directory `/home/user/paperbox-0.4.4/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I.. -I.. -DPREFIX=\""/usr/local"\"
-DSYSCONFDIR=\""/usr/local/etc"\" -DLIBDIR=\""/usr/local/lib"\"
-DDATADIR=\""/usr/local/share"\"
-DPAPERBOX_PKGDATADIR=\""/usr/local/share/paperbox"\"
-DGTKMM_DISABLE_DEPRECATED -DDBUS_API_SUBJECT_TO_CHANGE -pthread
-I/usr/include/gtkmm-2.4 -I/usr/lib/i386-linux-gnu/gtkmm-2.4/include
-I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4
-I/usr/lib/i386-linux-gnu/giomm-2.4/include -I/usr/include/pangomm-1.4
-I/usr/lib/i386-linux-gnu/pangomm-1.4/include -I/usr/include/gtk-2.0
-I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4
-I/usr/lib/i386-linux-gnu/gdkmm-2.4/include -I/usr/include/atk-1.0
-I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include
-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include
-I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include
-I/usr/include/cairomm-1.0 -I/usr/lib/i386-linux-gnu/cairomm-1.0/include
-I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1
-I/usr/include/freetype2 -I/usr/include/libpng12
-I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0
-I/usr/include/gio-unix-2.0/ -I/usr/include/libglade-2.0
-I/usr/include/libxml2 -I/usr/include/libglademm-2.4
-I/usr/lib/libglademm-2.4/include -pthread -I/usr/include/giomm-2.4
-I/usr/lib/i386-linux-gnu/giomm-2.4/include -I/usr/include/glibmm-2.4
-I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/glib-2.0
-I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/sigc++-2.0
-I/usr/lib/i386-linux-gnu/sigc++-2.0/include -pthread
-I/usr/include/gtkmm-2.4 -I/usr/lib/i386-linux-gnu/gtkmm-2.4/include
-I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include
-I/usr/include/gdkmm-2.4 -I/usr/lib/i386-linux-gnu/gdkmm-2.4/include
-I/usr/include/pangomm-1.4 -I/usr/lib/i386-linux-gnu/pangomm-1.4/include
-I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4
-I/usr/lib/i386-linux-gnu/giomm-2.4/include -I/usr/include/gtk-2.0
-I/usr/include/gtk-unix-print-2.0 -I/usr/include/atk-1.0
-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include
-I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include
-I/usr/include/cairomm-1.0 -I/usr/lib/i386-linux-gnu/cairomm-1.0/include
-I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1
-I/usr/include/freetype2 -I/usr/include/libpng12
-I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0
-I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-utils-1.0
-I/usr/include/glibmm-utils-1.0 -pthread -DORBIT2=1 -D_REENTRANT
-I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0
-I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1
-I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0
-I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0
-I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0
-I/usr/lib/i386-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0
-I/usr/lib/i386-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0
-I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0
-I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0
-I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0
-I/usr/include/freetype2 -I/usr/include/atk-1.0
-I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/cairo
-I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12
-pthread -I/usr/include/gtk-2.0 -I/usr/include/cairo
-I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0
-I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0
-I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0
-I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1
-I/usr/include/freetype2 -I/usr/include/libpng12
-I/usr/include/goocanvas-1.0 -I/usr/include/dbus-1.0
-I/usr/lib/i386-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0
-I/usr/lib/i386-linux-gnu/glib-2.0/include -DDBUS_API_SUBJECT_TO_CHANGE
-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include
-I/usr/include/dbus-1.0 -I/usr/lib/i386-linux-gnu/dbus-1.0/include
-DPAPERBOX_LOCALEDIR=\"/usr/local/share/locale\" -Wall -Wextra
-Wctor-dtor-privacy -Woverloaded-virtual -Wchar-subscripts -Wpointer-arith
-Wcast-align -Wsign-compare -g -O2 -MT document-tile.o -MD -MP -MF
.deps/document-tile.Tpo -c -o document-tile.o document-tile.cc
document-tile.cc: In member function ‘virtual void
paperbox::DocumentTile::connect_signals()’:
document-tile.cc:114:9: error: ‘set_uri_hook’ is not a member of
‘Gtk::LinkButton’
make[2]: *** [document-tile.o] Error 1
make[2]: Leaving directory `/home/user/paperbox-0.4.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/paperbox-0.4.4'
make: *** [all] Error 2
user@user:~/paperbox-0.4.4$
```

Can you help?

---

### Post by oldos2er on 2013-10-18
Moved to Packaging & Compiling Programs.

---

