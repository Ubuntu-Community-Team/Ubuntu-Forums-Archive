---
title: "gnome-applets in xfce"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by mlnease on 2014-02-14
Hello,

Really enjoying Xubuntu with Xfce desktop, but am missing a couple of my old GNOME applets with no equivalents in xfce.  Is there a safe way to use gnome-applets in Xubuntu/Xfce?

Thanks in advance.

---

### Post by Dennis N on 2014-02-14
Apparently so.

Look here:

[http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin)

---

### Post by Dennis N on 2014-02-14
The idea looked interesting, so I did some further looking. As far as I can see, xfce4-xfapplet-plugin is no longer available, at least in our repositories: 

```
dn@Roxanne:~$ apt-cache policy xfce4-xfapplet-plugin
xfce4-xfapplet-plugin:
  Installed: (none)
  Candidate: (none)

```

Probably worked with gnome 2 applets, such as in the old Ubuntus?

If you find anything to the contrary, please post it.

Added: Information on package, but don't know if this is usable.

[https://packages.debian.org/sid/xfce4-xfapplet-plugin](https://packages.debian.org/sid/xfce4-xfapplet-plugin)

Added2: it's not usable for x86 or amd64 - wrong architecture

---

### Post by tgalati4 on 2014-02-15
What were the specific applets?  Perhaps there are substitute programs or scripts you can write to display the info that you want.

---

### Post by mlnease on 2014-02-15
Thanks for the quick response.

I downloaded and extracted the tarball and tried compiling it.  Here's the result:

```
mn@mn-OptiPlex-745:~$ cd /home/mn/Desktop
mn@mn-OptiPlex-745:~/Desktop$ cd xfce4-xfapplet-plugin-0.1.0
mn@mn-OptiPlex-745:~/Desktop/xfce4-xfapplet-plugin-0.1.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.31... 0.34.2 found
checking for perl... /usr/bin/perl
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for ANSI C header files... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  el fr hu ja nl pl pt_BR ru vi zh_CN zh_TW
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${prefix}/share/locale
checking for additional xgettext flags... --keyword=Q_
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -lX11... yes
checking for SmcSaveYourselfDone in -lSM... yes
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.26
checking for gobject-2.0 >= 2.4.0... 2.32.4
checking GOBJECT_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include  
checking GOBJECT_LIBS... -lgobject-2.0 -lglib-2.0  
checking for gtk+-2.0 >= 2.4.0... 2.24.10
checking GTK_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  
checking for ORBit-2.0 >= 2.12.5... not found
*** The required package ORBit-2.0 was not found on your system.
*** Please install ORBit-2.0 (atleast version 2.12.5) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

```
I've been unable to get any farther so far.  There are clearly some unmet dependencies ([per Xfce.org]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin")) including ORBit2 and Libpanelapplet, which I don't find in the repositories.

But I suspect that xfapplets is simply obsolete.

I'd be most grateful for any additional advice--thanks in advance.

---

### Post by mlnease on 2014-02-15
> **Dennis N said:**
> The idea looked interesting, so I did some further looking. As far as I can see, xfce4-xfapplet-plugin is no longer available, at least in our repositories: 

```
dn@Roxanne:~$ apt-cache policy xfce4-xfapplet-plugin
xfce4-xfapplet-plugin:
  Installed: (none)
  Candidate: (none)

```

Probably worked with gnome 2 applets, such as in the old Ubuntus?

If you find anything to the contrary, please post it.

Added: Information on package, but don't know if this is usable.

[https://packages.debian.org/sid/xfce4-xfapplet-plugin](https://packages.debian.org/sid/xfce4-xfapplet-plugin)

Added2: it's not usable for x86 or amd64 - wrong architecture

Thanks again, I'm guessing you're right, that this was for GNOME2 and is now obsolete.  If I discover anything to the contrary, I will post it here.

---

### Post by mlnease on 2014-02-15
> **tgalati4 said:**
> What were the specific applets?  Perhaps there are substitute programs or scripts you can write to display the info that you want.

Thanks for you response.  The applets were gnome-timer and gnome-system-monitor (the one with the animated panel icon).  I like your idea to write my own scripts, but I'm afraid my skills aren't up the task--yet, at least.

---

### Post by Frogs Hair on 2014-02-15
XFCE applets from the goodies package include both a a timer and system monitor .

---

### Post by mlnease on 2014-02-15
Thanks, yes, I know--I've tried them both and they're fine applets, all due credit to their developers--but *very* different from their GNOME2 predecessors.

---

