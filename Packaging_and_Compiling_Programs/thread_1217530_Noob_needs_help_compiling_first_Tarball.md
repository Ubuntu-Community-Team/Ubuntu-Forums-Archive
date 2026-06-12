---
title: "Noob needs help compiling first Tarball"
date: 2009-07-19
forum: Packaging and Compiling Programs
---

### Post by Horomancer on 2009-07-19
Hi!
I've been using Ubuntu for almost a year now, but today is the first day I needed to compile a file from a tarball.
The ubunutu repositories have desmumes-0.7.3 which is close to two years old. I want to install the newer desmume-0.9.4 using the source files from the desmume.org website

I've been using the [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) to help with this and I've gotten a fair amount done.

Currently, when I type ./configure in the /usr/local/src/desmume-0.9.4 directory i get this spitout-
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.8.8
checking for XML::Parser... ok
checking for gzopen in -lz... yes
checking for zzip_open in -lzzip... no
checking for sdl-config... no
checking for sdl11-config... no
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking for main in -ldl... yes
checking for main in -lGL... no
checking for main in -lOSMesa... no
checking for pkg-config... pkg-config
checking for GLIB... no
checking for GTK... no
checking for GTKGLEXT... no
checking for GTHREAD... no
checking for LIBGLADE... no
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/cli/Makefile
config.status: creating src/cli/doc/Makefile
config.status: creating src/cocoa/Makefile
config.status: creating src/gtk/Makefile
config.status: creating src/gtk/doc/Makefile
config.status: creating src/gtk-glade/Makefile
config.status: creating src/gtk-glade/doc/Makefile
config.status: creating src/windows/Makefile
config.status: creating src/gdbstub/Makefile
config.status: creating autopackage/default.apspec
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
grep: po/Makefile.in: No such file or directory
config.status: error: po/Makefile.in.in was not created by intltoolize.

I don't know what to do from here.
Also i don't know how to make the command line data show up in nice little boxes like the Ubuntu help docs and other people on this forum.

---

### Post by ibutho on 2009-07-19
You are missing some dependencies. Install libgtk2.0-dev, libglib2.0-dev, libglade2-dev, libglut3-dev, libsdl1.2-dev and libgl1-mesa-dev. After that run ./configure again. Post back if you need more help.

---

### Post by Horomancer on 2009-07-19
thanks ibutho this libs did the trick
I ran 'make' and then sudo checkinstall

The program seems to be running much better than the old version (it actually opens files)

---

