---
title: "Problem compiling DVDstyler-2.5b3"
date: 2013-04-28
forum: Packaging and Compiling Programs
---

### Post by gimmeallurstuf on 2013-04-28
I run sudo ./configure then sudo make and this happens
```
Making all in wxVillaLib
make[1]: Entering directory `/home/mega/Downloads/dvdstyler-depend/DVDStyler-2.5b3/wxVillaLib'
g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"2.5b3\" -DPACKAGE_STRING=\"DVDStyler\ 2.5b3\" -DPACKAGE_BUGREPORT=\"http://www.dvdstyler.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"2.5b3\" -I.   -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12   -I/usr/include/libexif   -DWX_SVG -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -MT ExifHandler.o -MD -MP -MF .deps/ExifHandler.Tpo -c -o ExifHandler.o ExifHandler.cpp
mv -f .deps/ExifHandler.Tpo .deps/ExifHandler.Po
g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"2.5b3\" -DPACKAGE_STRING=\"DVDStyler\ 2.5b3\" -DPACKAGE_BUGREPORT=\"http://www.dvdstyler.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"2.5b3\" -I.   -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12   -I/usr/include/libexif   -DWX_SVG -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -MT ImageProc.o -MD -MP -MF .deps/ImageProc.Tpo -c -o ImageProc.o ImageProc.cpp
mv -f .deps/ImageProc.Tpo .deps/ImageProc.Po
g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"2.5b3\" -DPACKAGE_STRING=\"DVDStyler\ 2.5b3\" -DPACKAGE_BUGREPORT=\"http://www.dvdstyler.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"2.5b3\" -I.   -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12   -I/usr/include/libexif   -DWX_SVG -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -MT imagjpg.o -MD -MP -MF .deps/imagjpg.Tpo -c -o imagjpg.o imagjpg.cpp
mv -f .deps/imagjpg.Tpo .deps/imagjpg.Po
g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"2.5b3\" -DPACKAGE_STRING=\"DVDStyler\ 2.5b3\" -DPACKAGE_BUGREPORT=\"http://www.dvdstyler.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"2.5b3\" -I.   -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12   -I/usr/include/libexif   -DWX_SVG -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -MT PipeExecute.o -MD -MP -MF .deps/PipeExecute.Tpo -c -o PipeExecute.o PipeExecute.cpp
mv -f .deps/PipeExecute.Tpo .deps/PipeExecute.Po
g++ -DPACKAGE_NAME=\"DVDStyler\" -DPACKAGE_TARNAME=\"dvdstyler\" -DPACKAGE_VERSION=\"2.5b3\" -DPACKAGE_STRING=\"DVDStyler\ 2.5b3\" -DPACKAGE_BUGREPORT=\"http://www.dvdstyler.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"dvdstyler\" -DVERSION=\"2.5b3\" -I.   -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12   -I/usr/include/libexif   -DWX_SVG -g -O2  -fno-strict-aliasing  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread  -I/usr/local/include   -DGNOME2     -DHAVE_LIBUDEV -DDATADIR=\"/usr/local/share/dvdstyler\" -MT PropDlg.o -MD -MP -MF .deps/PropDlg.Tpo -c -o PropDlg.o PropDlg.cpp
PropDlg.cpp: In member function &#8216;void wxPropDlg::AddBitmapToggleButton(wxSizer*, bool, long int, const wxBitmap&, const wxSize&)&#8217;:
PropDlg.cpp:834:3: error: &#8216;wxBitmapToggleButton&#8217; was not declared in this scope
PropDlg.cpp:834:25: error: &#8216;ctrl&#8217; was not declared in this scope
PropDlg.cpp:834:54: error: expected primary-expression before &#8216;)&#8217; token
PropDlg.cpp:834:56: error: expected &#8216;;&#8217; before &#8216;m_controls&#8217;
PropDlg.cpp:839:2: error: &#8216;wxBitmapToggleButton&#8217; was not declared in this scope
PropDlg.cpp:839:24: error: &#8216;ctrl&#8217; was not declared in this scope
PropDlg.cpp:839:35: error: expected type-specifier before &#8216;wxBitmapToggleButton&#8217;
PropDlg.cpp:839:35: error: expected &#8216;;&#8217; before &#8216;wxBitmapToggleButton&#8217;
PropDlg.cpp: In member function &#8216;bool wxPropDlg::GetBool(int)&#8217;:
PropDlg.cpp:968:12: error: &#8216;wxBitmapToggleButton&#8217; was not declared in this scope
PropDlg.cpp:968:33: error: expected primary-expression before &#8216;)&#8217; token
PropDlg.cpp:968:35: error: expected &#8216;)&#8217; before &#8216;m_controls&#8217;
make[1]: *** [PropDlg.o] Error 1
make[1]: Leaving directory `/home/mega/Downloads/dvdstyler-depend/DVDStyler-2.5b3/wxVillaLib'
make: *** [all-recursive] Error 1

```

---

### Post by schragge on 2013-04-29
Why *sudo*? You are not supposed to run *sudo* with *./configure* and *make*, only with *make install*

---

### Post by gimmeallurstuf on 2013-04-29
well i just redid it without sudo same reusult here what ./configure gives me if that helps
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for install location... /usr/local
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... none needed
checking whether yytext is a pointer... no
checking for bison... bison -y
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.8.7... yes (version 2.8.12)
checking for wxWidgets static library... no
checking for wxWidgets media... yes
checking for LIBAV... yes
checking for libavformat/avformat.h... yes
checking for wxSVG... yes
checking for wxSVG library with LIBAV support... yes
checking if wxWindows was linked with GTK2... yes
checking for GNOMEUI2... yes
checking for LIBEXIF... yes
checking for FONTCONFIG... yes
checking for LIBUDEV... yes
checking for avconv... /usr/local/bin/avconv
checking for msgfmt... /usr/bin/msgfmt
checking for xmlto... /usr/bin/xmlto
checking for zip... /usr/bin/zip
checking for dvdauthor... /usr/bin/dvdauthor
checking for mkisofs... /usr/bin/mkisofs
checking for growisofs... /usr/bin/growisofs
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/rc/Makefile
config.status: creating wxVillaLib/Makefile
config.status: creating locale/Makefile
config.status: creating backgrounds/Makefile
config.status: creating buttons/Makefile
config.status: creating docs/Makefile
config.status: creating objects/Makefile
config.status: creating data/Makefile
config.status: creating templates/Makefile
config.status: creating src/Version.h
config.status: creating Info.plist
config.status: executing depfiles commands
```

---

