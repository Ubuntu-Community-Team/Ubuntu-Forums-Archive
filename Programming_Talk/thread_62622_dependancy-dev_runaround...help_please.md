---
title: "dependancy-dev runaround...help please"
date: 2005-09-05
forum: Programming Talk
---

### Post by tehwa on 2005-09-05
I'm trying to get my hands dirty learning development within GNOME. I've found Anjuta/Glade and it looks good, but I am getting an error from a tutorial that is killing me:

During compilation:```
tehwa@moog:~/Projects/TempConvert/src$ make
gcc -DHAVE_CONFIG_H -I. -I. -I.. -pthread -DORBIT2=1 -DXTHREADS -I/usr/local/inc lude/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libgnomeui-2.0 -I /usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2 .0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2 .0 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/gnome-vf s-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/bonobo-activation-2.0 -I/u sr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include -I/usr/ X11R6/include -I/usr/include/atk-1.0 -I/usr/include/libxml2     -Wall    -g  -c support.c
In file included from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from /usr/include/libgnomeui-2.0/gnome.h:4,
                 from support.c:15:
/usr/include/gtk-2.0/gdk/gdk.h:70: error: syntax error before '*' token
In file included from /usr/include/gtk-2.0/gtk/gtk.h:114,
                 from /usr/include/libgnomeui-2.0/gnome.h:4,
                 from support.c:15:
/usr/include/gtk-2.0/gtk/gtkmain.h:101: error: syntax error before "GOptionEntry "
/usr/include/gtk-2.0/gtk/gtkmain.h:105: error: syntax error before '*' token
/usr/include/gtk-2.0/gtk/gtkmain.h:105: warning: type defaults to `int' in decla ration of `gtk_get_option_group'
/usr/include/gtk-2.0/gtk/gtkmain.h:105: warning: data definition has no type or storage class
make: *** [support.o] Error 1
tehwa@moog:~/Projects/TempConvert/src$
```So```
/usr/include/gtk-2.0/gdk/gdk.h:70: error: syntax error before '*' token
```Is in reference to (line 70, gdk.h):```
void gdk_add_option_entries_libgtk_only (GOptionGroup *group);
```It seems I am missing what it needs to use this GOptionGroup?

It would be great if someone could tell my why I am getting this error, since any Anjuta Project I start raises this error upon building.

---

### Post by LordHunter317 on 2005-09-05
My guess is it's using a local version of something that's incompatible with that GTK (like glib)

Why did you install local development headers?  Why didn't you installed the appropriate -dev packages?

---

### Post by tehwa on 2005-09-05
[QUOTE=LordHunter317]My guess is it's using a local version of something that's incompatible with that GTK (like glib)

Why did you install local development headers?  Why didn't you installed the appropriate -dev packages?[/QUOTE]I think I understood that about half as much as you would have liked me to.

Perhaps the GNOME community isn't ready for incompetence of this scale:```

tehwa@moog:~$ dpkg -l *-dev | grep 'ii'

ii  aalib1-dev     1.4p5-22       ascii art library, development kit
ii  autotools-dev  20041130.2     Update infrastructure for config.{guess,sub}
ii  dpkg-dev       1.10.27ubuntu2 Package building tools for Debian
ii  libart-2.0-dev 2.3.17-1       Library of functions for 2D graphics - devel
ii  libasound2-dev 1.0.8-1        ALSA library development files
ii  libatk1.0-dev  1.9.1-0ubuntu1 Development files for the ATK accessibility
ii  libaudio-dev   1.7-2ubuntu1   The Network Audio System (NAS). (development
ii  libaudiofile-d 0.2.6-5        Open-source version of SGI's audiofile libra
ii  libbonobo2-dev 2.8.1-2        Bonobo CORBA interfaces library -- developme
ii  libbonoboui2-d 2.8.1-1ubuntu1 The Bonobo UI library - development files
ii  libc6-dev      2.3.2.ds1-20ub GNU C Library: Development Libraries and Hea
ii  libdb3-dev     3.2.9-22       Berkeley v3 Database Libraries [development]
ii  libesd0-dev    0.2.35-2ubuntu Enlightened Sound Daemon - Development files
ii  libexpat1-dev  1.95.8-1       XML parsing C library - development kit
ii  libfontconfig1 2.2.3-4ubuntu7 generic font configuration library (developm
ii  libfreetype6-d 2.1.7-2.3      FreeType 2 font engine, development files
ii  libgconf2-dev  2.10.0-0ubuntu GNOME configuration database system developm
ii  libgcrypt11-de 1.2.0-11       LGPL Crypto library - development files
ii  libglade2-dev  2.5.1-0ubuntu1 Development files for libglade
ii  libglib2.0-dev 2.6.3-1        Development files for the GLib library
ii  libgnome-keyri 0.4.2-0ubuntu1 Development files for GNOME keyring service
ii  libgnome2-dev  2.10.0-0ubuntu The GNOME 2 library - development files
ii  libgnomecanvas 2.10.0-0ubuntu A powerful object-oriented display - develop
ii  libgnomeui-dev 2.10.0-0ubuntu The GNOME 2 libraries (User Interface) - dev
ii  libgnomevfs2-d 2.10.0-0ubuntu The GNOME virtual file-system library (devel
ii  libgnorba-dev  1.4.2-19       GNOME CORBA services -- development package
ii  libgnutls11-de 1.0.16-13ubunt GNU TLS library - development files
ii  libgpg-error-d 1.0-1          library for common error values and messages
ii  libgtk2.0-dev  2.6.4-0ubuntu3 Development files for the GTK+ library
ii  libice-dev     6.8.2-10       Inter-Client Exchange library development fi
ii  libidl-dev     0.8.5-0ubuntu1 development files for programs that use libI
ii  libjpeg62-dev  6b-9           Development files for the IJG JPEG library
ii  libncurses5-de 5.4-4          Developer's libraries and docs for ncurses
ii  libopencdk8-de 0.5.5-10       Open Crypto Development Kit (OpenCDK) (devel
ii  liborbit2-dev  2.12.1-0ubuntu development files for ORBit2 - a CORBA ORB
ii  libpango1.0-de 1.8.1-0ubuntu2 Development files for the Pango
ii  libpopt-dev    1.7-5          lib for parsing cmdline parameters - develop
ii  libsdl1.2-dev  1.2.7+1.2.8cvs Simple DirectMedia Layer development files
ii  libsigc++-1.2- 1.2.5-1ubuntu2 Type-safe Signal Framework for C++ - develop
ii  libsigc++-2.0- 2.0.6-1        Type-safe Signal Framework for C++ - develop
ii  libsm-dev      6.8.2-10       X Window System Session Management library d
ii  libstdc++5-3.3 3.3.5-8ubuntu2 The GNU Standard C++ Library v3 (development
ii  libtasn1-2-dev 0.2.10-4       Manage ASN.1 structures (development)
ii  libwrap0-dev   7.6.dbs-6      Wietse Venema's TCP wrappers library, develo
ii  libx11-dev     6.8.2-10       X Window System protocol client library deve
ii  libxau-dev     6.8.2-10       X Authentication library development files
ii  libxext-dev    6.8.2-10       X Window System miscellaneous extension libr
ii  libxft-dev     2.1.2-6ubuntu1 FreeType-based font drawing library for X (d
ii  libxi-dev      6.8.2-10       X Window System Input extension library deve
ii  libxkbfile-dev 6.8.2-10       X Keyboard Extension file parsing library de
ii  libxml-dev     1.8.17-10      Development files for the GNOME XML library
ii  libxml2-dev    2.6.17-0ubuntu Development files for the GNOME XML library
ii  libxmu-dev     6.8.2-10       X Window System miscellaneous utility librar
ii  libxmuu-dev    6.8.2-10       lightweight X Window System miscellaneous ut
ii  libxp-dev      6.8.2-10       X Window System printing extension library d
ii  libxpm-dev     6.8.2-10       X pixmap library development files
ii  libxrandr-dev  6.8.2-10       X Window System Resize, Rotate and Reflectio
ii  libxrender-dev 0.9.0-0ubuntu4 X Rendering Extension client library (develo
ii  libxt-dev      6.8.2-10       X Toolkit Intrinsics development files
ii  libxtrap-dev   6.8.2-10       X Window System protocol-trapping extension
ii  libxtst-dev    6.8.2-10       X Window System event recording and testing
ii  libxv-dev      6.8.2-10       X Window System video extension library deve
ii  libxvidcore4-d 1.0.3-0.0      High quality ISO MPEG4 codec library -- deve
ii  pm-dev         6.8.2-10       proxy management protocol development files
ii  render-dev     0.9-0ubuntu1   X Rendering Extension header files and docum
ii  slang1-dev     1.4.9dbs-8     The S-Lang programming library, development
ii  x-dev          6.8.2-10       X protocol development files
ii  xlibmesa-gl-de 6.8.2-10       Mesa 3D graphics library development files [
ii  xlibmesa-glu-d 6.8.2-10       Mesa OpenGL utility library development file
ii  xlibs-dev      6.8.2-10       X Window System client library development f
ii  xlibs-static-d 6.8.2-10       X Window System client library development f
ii  zlib1g-dev     1.2.2-4ubuntu1 compression library - development
tehwa@moog:~$
```
This is a Carbon-based error. I am constantly playing with my system (MAS sound attempts and the like) which has left a lot of development packages on my machine. That list is after I did a massive cleanout of of packages while trying to remedu this Anjuta error.

If you can clarify your previous reply, I will have a bash at fixing this dev package dilemma.

Thanks

---

### Post by tehwa on 2005-09-06
[QUOTE=tehwa]I think I understood that about half as much as you would have liked me to.

Perhaps the GNOME community isn't ready for incompetence of this scale:```

tehwa@moog:~$ dpkg -l *-dev | grep 'ii'

ii  aalib1-dev     1.4p5-22       ascii art library, development kit
ii  autotools-dev  20041130.2     Update infrastructure for config.{guess,sub}
ii  dpkg-dev       1.10.27ubuntu2 Package building tools for Debian
ii  libart-2.0-dev 2.3.17-1       Library of functions for 2D graphics - devel
ii  libasound2-dev 1.0.8-1        ALSA library development files
ii  libatk1.0-dev  1.9.1-0ubuntu1 Development files for the ATK accessibility
ii  libaudio-dev   1.7-2ubuntu1   The Network Audio System (NAS). (development
ii  libaudiofile-d 0.2.6-5        Open-source version of SGI's audiofile libra
ii  libbonobo2-dev 2.8.1-2        Bonobo CORBA interfaces library -- developme
ii  libbonoboui2-d 2.8.1-1ubuntu1 The Bonobo UI library - development files
ii  libc6-dev      2.3.2.ds1-20ub GNU C Library: Development Libraries and Hea
ii  libdb3-dev     3.2.9-22       Berkeley v3 Database Libraries [development]
ii  libesd0-dev    0.2.35-2ubuntu Enlightened Sound Daemon - Development files
ii  libexpat1-dev  1.95.8-1       XML parsing C library - development kit
ii  libfontconfig1 2.2.3-4ubuntu7 generic font configuration library (developm
ii  libfreetype6-d 2.1.7-2.3      FreeType 2 font engine, development files
ii  libgconf2-dev  2.10.0-0ubuntu GNOME configuration database system developm
ii  libgcrypt11-de 1.2.0-11       LGPL Crypto library - development files
ii  libglade2-dev  2.5.1-0ubuntu1 Development files for libglade
ii  libglib2.0-dev 2.6.3-1        Development files for the GLib library
ii  libgnome-keyri 0.4.2-0ubuntu1 Development files for GNOME keyring service
ii  libgnome2-dev  2.10.0-0ubuntu The GNOME 2 library - development files
ii  libgnomecanvas 2.10.0-0ubuntu A powerful object-oriented display - develop
ii  libgnomeui-dev 2.10.0-0ubuntu The GNOME 2 libraries (User Interface) - dev
ii  libgnomevfs2-d 2.10.0-0ubuntu The GNOME virtual file-system library (devel
ii  libgnorba-dev  1.4.2-19       GNOME CORBA services -- development package
ii  libgnutls11-de 1.0.16-13ubunt GNU TLS library - development files
ii  libgpg-error-d 1.0-1          library for common error values and messages
ii  libgtk2.0-dev  2.6.4-0ubuntu3 Development files for the GTK+ library
ii  libice-dev     6.8.2-10       Inter-Client Exchange library development fi
ii  libidl-dev     0.8.5-0ubuntu1 development files for programs that use libI
ii  libjpeg62-dev  6b-9           Development files for the IJG JPEG library
ii  libncurses5-de 5.4-4          Developer's libraries and docs for ncurses
ii  libopencdk8-de 0.5.5-10       Open Crypto Development Kit (OpenCDK) (devel
ii  liborbit2-dev  2.12.1-0ubuntu development files for ORBit2 - a CORBA ORB
ii  libpango1.0-de 1.8.1-0ubuntu2 Development files for the Pango
ii  libpopt-dev    1.7-5          lib for parsing cmdline parameters - develop
ii  libsdl1.2-dev  1.2.7+1.2.8cvs Simple DirectMedia Layer development files
ii  libsigc++-1.2- 1.2.5-1ubuntu2 Type-safe Signal Framework for C++ - develop
ii  libsigc++-2.0- 2.0.6-1        Type-safe Signal Framework for C++ - develop
ii  libsm-dev      6.8.2-10       X Window System Session Management library d
ii  libstdc++5-3.3 3.3.5-8ubuntu2 The GNU Standard C++ Library v3 (development
ii  libtasn1-2-dev 0.2.10-4       Manage ASN.1 structures (development)
ii  libwrap0-dev   7.6.dbs-6      Wietse Venema's TCP wrappers library, develo
ii  libx11-dev     6.8.2-10       X Window System protocol client library deve
ii  libxau-dev     6.8.2-10       X Authentication library development files
ii  libxext-dev    6.8.2-10       X Window System miscellaneous extension libr
ii  libxft-dev     2.1.2-6ubuntu1 FreeType-based font drawing library for X (d
ii  libxi-dev      6.8.2-10       X Window System Input extension library deve
ii  libxkbfile-dev 6.8.2-10       X Keyboard Extension file parsing library de
ii  libxml-dev     1.8.17-10      Development files for the GNOME XML library
ii  libxml2-dev    2.6.17-0ubuntu Development files for the GNOME XML library
ii  libxmu-dev     6.8.2-10       X Window System miscellaneous utility librar
ii  libxmuu-dev    6.8.2-10       lightweight X Window System miscellaneous ut
ii  libxp-dev      6.8.2-10       X Window System printing extension library d
ii  libxpm-dev     6.8.2-10       X pixmap library development files
ii  libxrandr-dev  6.8.2-10       X Window System Resize, Rotate and Reflectio
ii  libxrender-dev 0.9.0-0ubuntu4 X Rendering Extension client library (develo
ii  libxt-dev      6.8.2-10       X Toolkit Intrinsics development files
ii  libxtrap-dev   6.8.2-10       X Window System protocol-trapping extension
ii  libxtst-dev    6.8.2-10       X Window System event recording and testing
ii  libxv-dev      6.8.2-10       X Window System video extension library deve
ii  libxvidcore4-d 1.0.3-0.0      High quality ISO MPEG4 codec library -- deve
ii  pm-dev         6.8.2-10       proxy management protocol development files
ii  render-dev     0.9-0ubuntu1   X Rendering Extension header files and docum
ii  slang1-dev     1.4.9dbs-8     The S-Lang programming library, development
ii  x-dev          6.8.2-10       X protocol development files
ii  xlibmesa-gl-de 6.8.2-10       Mesa 3D graphics library development files [
ii  xlibmesa-glu-d 6.8.2-10       Mesa OpenGL utility library development file
ii  xlibs-dev      6.8.2-10       X Window System client library development f
ii  xlibs-static-d 6.8.2-10       X Window System client library development f
ii  zlib1g-dev     1.2.2-4ubuntu1 compression library - development
tehwa@moog:~$
```
This is a Carbon-based error. I am constantly playing with my system (MAS sound attempts and the like) which has left a lot of development packages on my machine. That list is after I did a massive cleanout of of packages while trying to remedu this Anjuta error.

If you can clarify your previous reply, I will have a bash at fixing this dev package dilemma.

Thanks[/QUOTE]
 So I have a library installed that is causing conflicts. 

I can't find him, so I am going to remove Anjuta+Glade, then remove development libraries that still exist. Then reinstall Glade+ Anjuta.

If anyone can offer an alternative, please do.

---

