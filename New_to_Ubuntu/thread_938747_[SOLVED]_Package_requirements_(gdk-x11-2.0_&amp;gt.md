---
title: "[SOLVED] Package requirements (gdk-x11-2.0 &amp;gt;= 2.8) were not met"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-10-05
never mind, I didn't even need to compile in the first place.

I am trying to compile the programs I use most often, to optimize my system (compiling should do that, shouldn't it) Among the things I am trying to compile, is banshee. here is what I tried to do
```
harry@Neo:~$ cd banshee-1-1.2.1/
harry@Neo:~/banshee-1-1.2.1$ ls
aclocal.m4    configure.ac  install-sh           missing
AUTHORS       COPYING       intltool-extract.in  mkinstalldirs
build         data          intltool-merge.in    NEWS
ChangeLog     depcomp       intltool-update.in   po
config.guess  docs          libbanshee           README
config.h.in   extras        libtool              src
config.log    gstreamer     ltmain.sh            tests
config.sub    HACKING       Makefile.am
configure     INSTALL       Makefile.in
harry@Neo:~/banshee-1-1.2.1$ install-sh
bash: install-sh: command not found
harry@Neo:~/banshee-1-1.2.1$ nano INSTALL
harry@Neo:~/banshee-1-1.2.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.21... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.16.4)
checking for GDK_X11... configure: error: Package requirements (gdk-x11-2.0 >= 2.8) were not met:

No package 'gdk-x11-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_X11_CFLAGS
and GDK_X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

harry@Neo:~/banshee-1-1.2.1$ 

```
(I used nano to check the INSTALL file, just to check that I was doing this the right way, and it said to run ./configure, make and make install.)

I have looked through the repos, but I couldn't find the package gdk-x11-2.0
any ideas as to where I could get it, or in some way get banshee to compile, without lost functionality. (I assume I need it to get all the features of banshee, otherwise it wouldn't be needed, then again, we all know that when you assume, it makes an *** out of u and me:))

---

### Post by ichbinesderelch on 2008-10-05
maybe the thing you are looking for is contained in gdk-imlib11 or gdk-imlib11-dev package, try those things out

---

### Post by barbedsaber on 2008-10-05
> **ichbinesderelch said:**
> maybe the thing you are looking for is contained in gdk-imlib11 or gdk-imlib11-dev package, try those things out

```
harry@Neo:~$ sudo apt-get install gdk-imlib11
sudo: unable to resolve host Neo  # I always get this, don't worry about it
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdk-imlib11 is already the newest version.
gdk-imlib11 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harry@Neo:~$ 

```

it seems I already have it, and if I am not mistaken, -dev means development, aka not what I need. but thanks for trying.

---

### Post by oldos2er on 2008-10-05
"I am trying to compile the programs I use most often, to optimize my system (compiling should do that, shouldn't it"

 You're thinking of compiling a custom kernel for system optimization; I've never noticed any speed differences between self-compiled programs and precompiled binaries.

---

### Post by barbedsaber on 2008-10-05
> **oldos2er said:**
> "I am trying to compile the programs I use most often, to optimize my system (compiling should do that, shouldn't it"

 You're thinking of compiling a custom kernel for system optimization; I've never noticed any speed differences between self-compiled programs and precompiled binaries.

well I'm an idiot aren't I?

---

