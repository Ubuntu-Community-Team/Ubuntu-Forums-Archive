---
title: "Trying to compile Anjuta..."
date: 2005-07-26
forum: Programming Talk
---

### Post by grofaz on 2005-07-26
...but I'm not getting anywhere. Will someone PLEASE help me out here ??

Here's a copy of the build message:

Generating Project ...
Loading Project ...
Saving Project ...
Generating source codes ...
Warning: Can not generate c/c++ source code.
Warning: It is because either glade (for gtk/gnome projects) or glademm (for gtkmm/gnomemm projects) is not installed.
Warning: Your generated project will still be fine, though.
Copying icon file ...
Locating files ...
Saving Project ...
Updating Project ...
Running autogen.sh ...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running gettextize...  Ignore non-fatal messages.
  autopoint --force
autopoint: *** cvs program not found
autopoint: *** Stop.
Making ./aclocal.m4 writable ...
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
configure.in: 80: required file `./ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exist
Running autoconf ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
Package gtkmm-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.0' found
Auto generation completed...............Unsuccessful

What am I doing wrong ? Am I missing any packages ? Have I not configured the compiler correctly ? What ?? I can't find the gtkmm-2.0 package anywhere. Is that the trouble ?

Thanks!

---

### Post by dataw0lf on 2005-07-26
Try

  ```
 export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```

---

### Post by grofaz on 2005-07-26
OK, where do I try that?

---

### Post by dataw0lf on 2005-07-26
In a terminal/shell.

---

### Post by grofaz on 2005-07-26
Ah so, thank you!

I think I also need to set the include and library directories properly. Where are they located ? Or is that what your bit of code does?

Thanks for the help, really appreciated.

---

