---
title: "Trying to install gnomenu"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by mike18 on 2013-08-11
Hi UbuntuForums,

I'm trying to install gnomenu. I've got xubuntu 12.04 installed. I read somewhere that you first have to get 'xfce4-xfapplet-plugin' to use gnomenu. So I downloaded a zipped file called 'xfce4-xfapplet-plugin_0.1.0.orig.tar'. I extracted it and proceeded to follow the instructions. The first step was to use the ./configure command. This is what the console output:

```
mike@x40:~/Downloads/xfce4-xfapplet-plugin-0.1.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking for intltool >= 0.31... 0.34.2 found
checking for perl... /usr/bin/perl
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
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
checking for msgfmt... no
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${prefix}/share/locale
checking for additional xgettext flags... --keyword=Q_
checking for X... no
configure: error: X Window system libraries and header files are required

```

I don't think that was supposed to happen. So now I'm stuck. Can someone help me get past this step?

---

### Post by qamelian on 2013-08-11
You shouldn't need to install this from source. It's included in the Ubuntu repositories in the package, xfce4-goodies. The following command in a terminal will install it for you:
```
sudo apt-get install xfce4-goodies
```

---

### Post by mike18 on 2013-08-11
Hey thanks for replying man. 

So I've installed xfce4-goodies from Synaptic Manager. Is there any way I can confirm that xfapplet-plugin is actually installed?

Also,  I tried to install gnomenu from a file named 'gnomenu-2.9.1.tar.gz'.  The instructions say that all I have to is use the  command: 'sudo make install'. I did this and the following occured:

```
mike@x40:~/Downloads/gnomenu$ sudo make install
[sudo] password for mike: 
install -d /etc/gnomenu /usr/bin/ /usr/lib \
    /usr/share /usr/lib/bonobo/servers /usr/share/cairo-dock/plug-ins/Dbus/third-party/GnoMenu /usr/share/kde4/apps/plasma
python -u setup.py
Preparing to install translation
/home/mike/Downloads/gnomenu/po
installing translations
Creating language Binary for : gnomenu-es
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ko
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ro
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ia
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-sk
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-he
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-oc
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ar
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-tr
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ja
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-lt
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-uk
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-de
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-hu
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-da
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-fr
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-bg
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-yi
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-it
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-sr
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-zh_TW
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-gl
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-pt
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-nb
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-tet
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ml
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-nl
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ru
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-pl
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-ca
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-cs
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-sv
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-fi
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-pt_BR
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-id
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-zh_CN
sh: 1: msgfmt: not found
Creating language Binary for : gnomenu-el
sh: 1: msgfmt: not found
#-install src/bin/GnoMenu.py /usr/bin/
cp -r src/lib/gnomenu /usr/lib
cp -r src/share/gnomenu /usr/share
cp -r src/share/avant-window-navigator /usr/share
install src/share/dockmanager/scripts/GnoMenu.py /usr/share/dockmanager/scripts/
install: target `/usr/share/dockmanager/scripts/' is not a directory: No such file or directory
make: [install] Error 1 (ignored)
cp -r src/share/dockmanager/scripts/GnoMenu /usr/share/dockmanager/scripts/
cp: cannot create directory `/usr/share/dockmanager/scripts/': No such file or directory
make: [install] Error 1 (ignored)
#-cp -r src/share/xfce4 /usr/share
cp -r src/share/locale /usr/share
#-cp -r src/share/plasma/plasmoids /usr/share/kde4/apps/plasma
install src/share/cairo-dock/third-party/GnoMenu/* /usr/share/cairo-dock/plug-ins/Dbus/third-party/GnoMenu/
#-cp -r src/share/cairo-dock ~/.config/
install src/bin/GnoMenu.py /usr/bin/
install src/lib/bonobo/GNOME_GnoMenu.server /usr/lib/bonobo/servers
plasmapkg -i src/share/plasma/plasmoids/GnoMenu.zip -p /usr/share/kde4/apps/plasma/plasmoids
make: plasmapkg: Command not found
make: [install] Error 127 (ignored)
Makefile: GnoMenu installed.
```

I noticed that there were a couple of errors during the install. But in the last line it says that gnomenu is installed. 

I assume (doubtfully) that it is installed. I restart my laptop, right click on the panel, and can't find xfapplet or gnomenu anywhere.

Help is appreciated. Thanks!

---

### Post by Frogs Hair on 2013-08-11
The  GnoMenu was meant to run in Gnome 2 and not xfwm4 and If you have some instructions post a link . AFA Ubuntu 12.04 goes there is no source package but I found mention of Mate installations  . [https://launchpad.net/ubuntu/precise/+source/gnomenu](https://launchpad.net/ubuntu/precise/+source/gnomenu)

---

### Post by mike18 on 2013-08-11
Thanks Frog, it's reassuring to know that my efforts were in vain. Reassuring because, now I can stop trying to cram this circle peg into the square hole (if you know what I mean).

---

