---
title: "How to install Gambas2  2.6.0 ?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Biggy on 2008-05-11
I download [Source Packages]("http://prdownloads.sourceforge.net/gambas/gambas2-2.6.0.tar.bz2?download") new version Gambas2 2.6.0 from Gambas site. I follow Gambas installation instructions to install, but can't install. From Synaptic manager is aviable the older version Gambas 2.5.0. I want to install the new stable version 2.6.0

any help for Gambas installation ??

thanks

---

### Post by Biggy on 2008-05-11
?

---

### Post by Monicker on 2008-05-11
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Biggy on 2008-05-11
after command
sudo make install
give this message
> Nothing to be done for `install-data-am'

---

### Post by Monicker on 2008-05-11
That by itself is not an error.  It could just be an optional component.  Does it continue after that?

---

### Post by erginemr on 2008-05-11
This usually happens when the configure stage cannot be completed. Are you sure that there are no error messages issued when you run ./configure?

Besides than that, you may not have installed all development packages neeeded for the compilation of gambas. The following command should just do that:
```
sudo apt-get build-dep gambas
```
But for it to work, you should first enable the sources section from Main Menu -> System -> Administration -> Software Sources.

---

### Post by Biggy on 2008-05-11
./configure
> checking for dlfcn.h... (cached) yes
checking how to run the C++ preprocessor... (cached) g++ -E
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
checking whether we are using the GNU Fortran 77 compiler... (cached) no
checking whether  accepts -g... (cached) no
checking the maximum length of command line arguments... (cached) 98304
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking for objdir... (cached) .libs
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking if gcc supports -fno-rtti -fno-exceptions... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for CORBA component headers... no
configure: WARNING: Unable to find file: CORBA.h
checking for CORBA component libraries... no
configure: WARNING: Unable to find file: libomniORB4.so
configure: WARNING: Unable to find file: libomniDynamic4.so
configure: WARNING: *** CORBA component is disabled
configure: updating cache ../config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
=== configuring in gb.image (/home/biggy/gambas2-2.6.0/gb.image)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking for style of include used by make... GNU
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... (cached) gcc -E
checking for g++... (cached) g++
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for setenv... (cached) yes
checking for unsetenv... (cached) yes
checking for getdomainname... (cached) yes
checking for getpt... (cached) yes
checking for ccache... no
checking for main in -lm... (cached) yes
checking for main in -lz... (cached) yes
checking for main in -lgcc_s... (cached) yes
checking for main in -lstdc++... (cached) yes
checking target system... LINUX
checking which extension is used for shared libraries... .so
checking for threading compiler options... -D_REENTRANT
checking for threading linker options... -lpthread
checking for mathematic libraries... -lm
checking for external gettext library... 
checking CFLAGS for gcc -fvisibility=hidden... (cached) -fvisibility=hidden
checking for a sed that does not truncate output... (cached) /bin/sed
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... (cached) /bin/grep -E
checking for ld used by gcc... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking how to recognize dependent libraries... (cached) pass_all
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for dlfcn.h... (cached) yes
checking how to run the C++ preprocessor... (cached) g++ -E
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
checking whether we are using the GNU Fortran 77 compiler... (cached) no
checking whether  accepts -g... (cached) no
checking the maximum length of command line arguments... (cached) 98304
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking for objdir... (cached) .libs
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking if gcc supports -fno-rtti -fno-exceptions... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for Image processing component headers... 
checking for Image processing component libraries... 
configure: updating cache ../config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
=== configuring in gb.desktop (/home/biggy/gambas2-2.6.0/gb.desktop)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking for style of include used by make... GNU
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... (cached) gcc -E
checking for g++... (cached) g++
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for setenv... (cached) yes
checking for unsetenv... (cached) yes
checking for getdomainname... (cached) yes
checking for getpt... (cached) yes
checking for ccache... no
checking for main in -lm... (cached) yes
checking for main in -lz... (cached) yes
checking for main in -lgcc_s... (cached) yes
checking for main in -lstdc++... (cached) yes
checking target system... LINUX
checking which extension is used for shared libraries... .so
checking for threading compiler options... -D_REENTRANT
checking for threading linker options... -lpthread
checking for mathematic libraries... -lm
checking for external gettext library... 
checking CFLAGS for gcc -fvisibility=hidden... (cached) -fvisibility=hidden
checking for a sed that does not truncate output... (cached) /bin/sed
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... (cached) /bin/grep -E
checking for ld used by gcc... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking how to recognize dependent libraries... (cached) pass_all
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for dlfcn.h... (cached) yes
checking how to run the C++ preprocessor... (cached) g++ -E
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
checking whether we are using the GNU Fortran 77 compiler... (cached) no
checking whether  accepts -g... (cached) no
checking the maximum length of command line arguments... (cached) 98304
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking for objdir... (cached) .libs
checking for ar... (cached) ar
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking if gcc supports -fno-rtti -fno-exceptions... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for X... (cached) libraries , headers 
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking for XTestQueryExtension in -lXtst... no
configure: WARNING: *** Desktop-neutral routines is disabled
configure: updating cache ../config.cache
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
=== configuring in comp (/home/biggy/gambas2-2.6.0/comp)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
=== configuring in app (/home/biggy/gambas2-2.6.0/app)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
checking for xdg-mime... (cached) xdg-mime
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
=== configuring in examples (/home/biggy/gambas2-2.6.0/examples)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
=== configuring in help (/home/biggy/gambas2-2.6.0/help)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=../config.cache --srcdir=.
configure: loading cache ../config.cache
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) gawk
checking whether make sets $(MAKE)... (cached) yes
checking build system type... (cached) i686-pc-linux-gnu
checking for style of include used by make... GNU
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... (cached) i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... (cached) gcc -E
checking for g++... (cached) g++
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for setenv... (cached) yes
checking for unsetenv... (cached) yes
checking for getdomainname... (cached) yes
checking for getpt... (cached) yes
checking for ccache... no
checking for main in -lm... (cached) yes
checking for main in -lz... (cached) yes
checking for main in -lgcc_s... (cached) yes
checking for main in -lstdc++... (cached) yes
checking target system... LINUX
checking which extension is used for shared libraries... .so
checking for threading compiler options... -D_REENTRANT
checking for threading linker options... -lpthread
checking for mathematic libraries... -lm
checking for external gettext library... 
checking CFLAGS for gcc -fvisibility=hidden... (cached) -fvisibility=hidden
configure: creating ./config.status
config.status: creating Makefile
config.status: creating help/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

************************************************************

THESE COMPONENTS ARE DISABLED:

- gb.compress.bzlib2
- gb.corba
- gb.db.firebird
- gb.db.mysql
- gb.db.odbc
- gb.db.postgresql
- gb.db.sqlite2
- gb.db.sqlite3
- gb.desktop
- gb.gtk.svg
- gb.net.curl
- gb.opengl
- gb.pcre
- gb.pdf
- gb.qt
- gb.qt.kde
- gb.qte
- gb.sdl
- gb.sdl.sound
- gb.v4l
- gb.xml

************************************************************


make
> make  all-recursive
make[1]: Entering directory `/home/biggy/gambas2-2.6.0'
Making all in main
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/main'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/main'
Making all in libltdl
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main/libltdl'
make  all-am
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/libltdl'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2   -o libltdlc.la  ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/libltdl'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main/libltdl'
Making all in gbx
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main/gbx'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main/gbx'
Making all in gbc
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main/gbc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main/gbc'
Making all in lib
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib'
Making all in debug
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/debug'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/debug'
Making all in eval
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/eval'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/eval'
Making all in db
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/db'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/db'
Making all in compress
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/compress'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/compress'
Making all in vb
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/vb'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/vb'
Making all in option
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/option'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/option'
Making all in draw
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/draw'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/draw'
Making all in gui
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib/gui'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib/gui'
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/main/lib'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main/lib'
Making all in share
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main/share'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main/share'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/main'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/main'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/main'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/main'
Making all in gb.compress.bzlib2
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.bzlib2'
Making all in gb.compress.zlib
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib/src'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.compress.zlib'
Making all in gb.db.mysql
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.mysql'
Making all in gb.db.odbc
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.odbc'
Making all in gb.db.postgresql
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.postgresql'
Making all in gb.db.sqlite3
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite3'
Making all in gb.db.sqlite2
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.sqlite2'
Making all in gb.db.firebird
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.db.firebird'
Making all in gb.gtk
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk/src'
Making all in ext
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk/src/ext'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk/src/ext'
make[5]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk/src'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk/src'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk'
Making all in gb.net
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net/src'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net'
Making all in gb.net.curl
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.curl'
Making all in gb.net.smtp
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.smtp/src'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.smtp/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.net.smtp'
Making all in gb.pcre
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pcre'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pcre'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pcre'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pcre'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pcre'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pcre'
Making all in gb.qt
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt'
Making all in gb.qte
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qte'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qte'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qte'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qte'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qte'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qte'
Making all in gb.qt.kde
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.qt.kde'
Making all in gb.sdl
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl'
Making all in gb.sdl.sound
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.sdl.sound'
Making all in gb.xml
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.xml'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.xml'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.xml'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.xml'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.xml'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.xml'
Making all in gb.v4l
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.v4l'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.v4l'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.v4l'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.v4l'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.v4l'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.v4l'
Making all in gb.crypt
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.crypt'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.crypt'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.crypt/src'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.crypt/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.crypt'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.crypt'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.crypt'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.crypt'
Making all in gb.opengl
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.opengl'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.opengl'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.opengl'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.opengl'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.opengl'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.opengl'
Making all in gb.corba
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.corba'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.corba'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.corba'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.corba'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.corba'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.corba'
Making all in gb.pdf
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pdf'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pdf'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.pdf'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pdf'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pdf'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.pdf'
Making all in gb.gtk.svg
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.gtk.svg'
Making all in gb.image
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.image'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.image'
Making all in src
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.image/src'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.image/src'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.image'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.image'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.image'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.image'
Making all in gb.desktop
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/gb.desktop'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/gb.desktop'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/gb.desktop'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.desktop'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.desktop'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/gb.desktop'
Making all in comp
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/comp'
make  all-am
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/comp'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/comp'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/comp'
Making all in app
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/app'
make  all-am
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/app'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/app'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/app'
Making all in help
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/help'
make  all-recursive
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/help'
Making all in help
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/help/help'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/help/help'
make[4]: Entering directory `/home/biggy/gambas2-2.6.0/help'
make[4]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
Making all in examples
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/examples'
make  all-am
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/examples'
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/examples'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/examples'
make[2]: Entering directory `/home/biggy/gambas2-2.6.0'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0'


make install
> Running the informer again because of dependencies between information files
gb.info
gb.vb
gb.gui
gbi2: warning: component gb.qt not found
gb.net
gb.eval
gb.db
gb.option
gb.web
gb.compress
gb.chart
gb.debug
gb.db.form
gb.report
gb
gb.crypt
gb.form
gb.form.mdi
gb.gtk.ext
gb.net.smtp
gb.gtk
gb.settings
gb.image
gb.form.dialog
Installing the components...
Compiling gb.settings...
OK
Installing gb.settings...
Compiling gb.info...
OK
Installing gb.info...
Compiling gb.form...
/home/biggy/gambas2-2.6.0/comp/src/gb.form/Balloon.class:5: Unknown identifier: Control
Installing gb.form...
Compiling gb.form.dialog...
/home/biggy/gambas2-2.6.0/comp/src/gb.form.dialog/FDirDialog.class:52: Unknown identifier: HBox
Installing gb.form.dialog...
Compiling gb.form.mdi...
/home/biggy/gambas2-2.6.0/comp/src/gb.form.mdi/CWindow.class:3: Unknown identifier: Window
Installing gb.form.mdi...
Compiling gb.db.form...
/home/biggy/gambas2-2.6.0/comp/src/gb.db.form/Common.module:3: Unknown identifier: Control
Installing gb.db.form...
Compiling gb.web...
OK
Installing gb.web...
Compiling gb.report...
/home/biggy/gambas2-2.6.0/comp/src/gb.report/FReportTutorial1.class:141: Unknown identifier: Button
Installing gb.report...
Compiling gb.chart...
/home/biggy/gambas2-2.6.0/comp/src/gb.chart/CAxe.class:6: Unknown identifier: Font
Installing gb.chart...
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/comp'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0/comp'
Making install in app
make[1]: Entering directory `/home/biggy/gambas2-2.6.0/app'
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/app'
Installing the development environment...
Compiling gambas2...
/home/biggy/gambas2-2.6.0/app/src/gambas2/CClassInfo.class:46: Unknown identifier: Form
Compiling gambas2-database-manager...
/home/biggy/gambas2-2.6.0/app/src/gambas2-database-manager/CConnection.class:167: Unknown identifier: Form
Compiling gbs2...
OK
ln: creating symbolic link `/usr/local/bin/gambas2': File exists
Installing the scripter...
ln: creating symbolic link `/usr/local/bin/gbs2': File exists
Registering Gambas script mimetype
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/app'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0/app'
Making install in help
make[1]: Entering directory `/home/biggy/gambas2-2.6.0/help'
Making install in help
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/help/help'
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/help/help'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/help/help'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/help/help'
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/help'
make[3]: Entering directory `/home/biggy/gambas2-2.6.0/help'

Installing the gambas help files...
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0/help'
Making install in examples
make[1]: Entering directory `/home/biggy/gambas2-2.6.0/examples'
make[2]: Entering directory `/home/biggy/gambas2-2.6.0/examples'

Installing the gambas examples...
Compiling Automation/KateBrowser/...
/usr/local/share/gambas2/examples/Automation/KateBrowser/FBrowser.class:117: Unknown identifier: Menu
Compiling Automation/Scripting/...
/usr/local/share/gambas2/examples/Automation/Scripting/FScript.class:80: Unknown identifier: Label
Compiling Basic/Blights/...
OK
Compiling Basic/Collection/...
OK
Compiling Basic/DragNDrop/...
/usr/local/share/gambas2/examples/Basic/DragNDrop/FDragNDrop.class:140: Unknown identifier: VBox
Compiling Basic/Object/...
OK
Compiling Basic/Timer/...
OK
Compiling Control/Embedder/...
OK
Compiling Control/HighlightEditor/...
/usr/local/share/gambas2/examples/Control/HighlightEditor/FEditor.class:3: Unknown identifier: Editor
Compiling Control/TextEdit/...
/usr/local/share/gambas2/examples/Control/TextEdit/FMain.class:174: Unknown identifier: HBox
Compiling Control/TreeView/...
/usr/local/share/gambas2/examples/Control/TreeView/TreeViewExample.class:170: Unknown identifier: Menu
Compiling Database/Database/...
/usr/local/share/gambas2/examples/Database/Database/FMain.class:186: Unknown identifier: Frame
Compiling Database/DataReportExample/...
/usr/local/share/gambas2/examples/Database/DataReportExample/Fabout.class:25: Unknown identifier: ScrollView
Compiling Database/PictureDatabase/...
/usr/local/share/gambas2/examples/Database/PictureDatabase/FormPictureDatabase.class:233: Unknown identifier: HSplit
Compiling Drawing/AnalogWatch/...
/usr/local/share/gambas2/examples/Drawing/AnalogWatch/FrmClock.class:232: Unknown identifier: Menu
Compiling Drawing/Chart/...
OK
Compiling Drawing/Clock/...
/usr/local/share/gambas2/examples/Drawing/Clock/FClock.class:3: Unknown identifier: Image
Compiling Drawing/Gravity/...
OK
Compiling Drawing/ImageViewer/...
/usr/local/share/gambas2/examples/Drawing/ImageViewer/FViewer.class:132: Unknown identifier: Menu
Compiling Drawing/OnScreenDisplay/...
/usr/local/share/gambas2/examples/Drawing/OnScreenDisplay/FOnScreenDisplay.class:9: Unknown identifier: Font
Compiling Drawing/Sensor/...
/usr/local/share/gambas2/examples/Drawing/Sensor/FSensor.class:3: Unknown identifier: Image
Compiling Games/BeastScroll/...
/usr/local/share/gambas2/examples/Games/BeastScroll/MMain.module:3: Unknown identifier: Window
Compiling Games/Concent/...
/usr/local/share/gambas2/examples/Games/Concent/fotos.class:13: Unknown identifier: Button
Compiling Games/DeepSpace/...
/usr/local/share/gambas2/examples/Games/DeepSpace/FAbout.class:25: Unknown identifier: TextLabel
Compiling Games/GameOfLife/...
/usr/local/share/gambas2/examples/Games/GameOfLife/CGameField.class:4: Unknown identifier: Image
Compiling Games/RobotFindsKitten/...
/usr/local/share/gambas2/examples/Games/RobotFindsKitten/Frfk.class:192: Unknown identifier: Label
Compiling Games/Snake/...
/usr/local/share/gambas2/examples/Games/Snake/FrmMain.class:21: Unknown identifier: Picture
Compiling Games/Solitaire/...
OK
Compiling Misc/Console/...
/usr/local/share/gambas2/examples/Misc/Console/FConsole.class:145: Unknown identifier: TextArea
Compiling Misc/Evaluator/...
OK
Compiling Misc/Explorer/...
OK
Compiling Misc/Notepad/...
OK
Compiling Misc/PDFViewer/...
/usr/local/share/gambas2/examples/Misc/PDFViewer/FMain.class:33: Unknown identifier: PdfDocument
Compiling Networking/ClientSocket/...
OK
Compiling Networking/DnsClient/...
OK
Compiling Networking/HTTPGet/...
/usr/local/share/gambas2/examples/Networking/HTTPGet/F.class:299: Unknown identifier: Button
Compiling Networking/HTTPPost/...
/usr/local/share/gambas2/examples/Networking/HTTPPost/F.class:2: Unknown identifier: HttpClient
Compiling Networking/SerialPort/...
OK
Compiling Networking/ServerSocket/...
OK
Compiling Networking/UDPServerClient/...
/usr/local/share/gambas2/examples/Networking/UDPServerClient/FrmClient.class:77: Unknown identifier: Panel
Compiling Networking/WebBrowser/...
/usr/local/share/gambas2/examples/Networking/WebBrowser/FBrowser.class:65: Unknown identifier: HBox
Compiling OpenGL/3DWebCam/...
/usr/local/share/gambas2/examples/OpenGL/3DWebCam/Mmain.module:3: Unknown identifier: VideoDevice
Compiling OpenGL/GambasGears/...
/usr/local/share/gambas2/examples/OpenGL/GambasGears/Module1.module:11: Unknown identifier: Window
Compiling OpenGL/PDFPresentation/...
/usr/local/share/gambas2/examples/OpenGL/PDFPresentation/Clogo.class:30: Unknown identifier: Gl
Compiling Printing/Printing/...
/usr/local/share/gambas2/examples/Printing/Printing/FormPrinting.class:70: Unknown identifier: Image
Compiling Sound/CDPlayer/...
/usr/local/share/gambas2/examples/Sound/CDPlayer/Fcdplayer.class:8: Unknown identifier: CDRom
Compiling Sound/MusicPlayer/...
/usr/local/share/gambas2/examples/Sound/MusicPlayer/FSoundPlayer.class:13: Unknown identifier: Music
Compiling Video/MoviePlayer/...
OK
Compiling Video/MyWebCam/...
/usr/local/share/gambas2/examples/Video/MyWebCam/Form1.class:2: Unknown identifier: VideoDevice
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0/examples'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0/examples'
make[1]: Entering directory `/home/biggy/gambas2-2.6.0'
make[2]: Entering directory `/home/biggy/gambas2-2.6.0'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/biggy/gambas2-2.6.0'
make[1]: Leaving directory `/home/biggy/gambas2-2.6.0'


---

### Post by Biggy on 2008-05-11
sudo apt-get build-dep gambas

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gambas


any idea !!??

---

### Post by nowshining on 2008-05-11
try opening up the Makefile in the src folder & change all /usr/lib to /usr/local/lib

and make clean and try again with make. No need to ./configure again.

---

### Post by Biggy on 2008-05-11
i don't understand how to do this!!!

---

### Post by nowshining on 2008-05-11
in the folder for the program source u downloaded, in the file manager go into it and find a file named Makefile (if any) and open it up with a text editor and replace if can use ctrl+R for replacing files if it works in gedit (or equiv) and replace alll /usr/lib txt to /usr/local/lib

if not u can also try

in terminal..

sudo ldconfig (lowercase L)

---

### Post by Biggy on 2008-05-24
i can't install the new 2.6.0 version of Gambas2.
i reinstall older version (2.5.0) from synaptic, but now i try to start Gambas and give error:
> ERROR: #2: Cannot load class 'Project': Unable to load class file
any idea ???!!

---

### Post by Biggy on 2008-05-24
help !

---

### Post by kalaharix on 2008-06-10
I have just seen your post (better late than never). 

I have just this morning compiled Gambas 2.6 on Ubuntu 8.04. I followed the instructions in [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/) (go to 'getting started', 'installation page', 'Ubuntu').

The trick that made it work for me (at long last!) was to copy the sudo apt-get paragraph for Hardy into gedit first. You can see the results of a lot of carriage returns in the file which prevent the installation of required packages completing. Delete the carriage returns one by one until you have a non-stop paragraph and then paste that into terminal.

After that it was plain sailing.

Hope you have not given up in the meantime.

---

### Post by cariboo on 2008-06-10
Is there a compelling reason for installing the latest version?

---

### Post by kalaharix on 2008-06-10
I don't think so. 

It was suggested to me that it might fix what appeared to be a minor bug: it didn't, but I worked round the problem anyway.

Most of (what little) work I have done is on 2.5.

I must confess that I really like Gambas2.

---

### Post by Aaron4 on 2008-07-01
> **Biggy said:**
> sudo apt-get build-dep gambas



any idea !!??


Try:
sudo apt-get build-dep gambas2

---

### Post by Biggy on 2008-07-23
> **Aaron4 said:**
> Try:
sudo apt-get build-dep gambas2


apt-get build-dep gambas2

>  sudo apt-get build-dep gambas2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for gambas2 could not be satisfied.


---

### Post by kalaharix on 2008-08-11
Wow, 

This has been going on a long time. I give you 11/10 for perseverence! As I said earlier, I am having no problem so perhaps I can help you step by step.

I think you are missing a required library but cannot think why. build-dep should do the trick but it is not used in the Gambas installation instructions so I guess it does not fulfill some requirement.

Right! What Ubuntu version are you using?

---

