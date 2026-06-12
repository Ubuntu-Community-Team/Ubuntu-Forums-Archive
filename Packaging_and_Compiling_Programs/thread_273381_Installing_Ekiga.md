---
title: "Installing Ekiga"
date: 2006-10-07
forum: Packaging and Compiling Programs
---

### Post by abhinav_bipnesh on 2006-10-07
Hi 
I using Ubuntu 5.11 release. During compling source code for Ekiga i have got this error message


checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether GNOME support must be compiled in... yes
checking whether documentation should be built... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GDU_MODULE_VERSION_CHECK... yes
checking for intltool >= 0.20... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
root@ubuntu:/home/ekiga-2.0.2# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether GNOME support must be compiled in... yes
checking whether documentation should be built... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GDU_MODULE_VERSION_CHECK... yes
checking for intltool >= 0.20... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for library containing strerror... none required
checking for ANSI C header files... (cached) yes
checking whether strcasecmp is declared... yes
Using config source xml::/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EKIGA... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 gthread-2.0 >= 2.4.0 esound >= 0.2.28 gconf-2.0 >= 2.2.0 libgnome-2.0 >= 2.2.0 libgnomeui-2.0 >= 2.2.0) were not met:

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EKIGA_CFLAGS
and EKIGA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have check the synaptic pakage manager for the GTK+ it is installed but than also i am gettung this error 
Please help me out :-?

---

### Post by qamelian on 2006-10-08
What your missing is the dev files for gtk+. Many times when you are compiling from source, the program you are compiling will link against the source code or headers from other programs or libraries. In Ubuntu, I believe all such packages containing the source will contain a "-dev" in the package name. In such a situation just search in Synaptic for the dev package corresponding to what your program is linking against.

---

### Post by Chickencha on 2006-10-08
The poster above is probably right.  Specifically, you need to install the package called libgtk2.0-dev.  Enter into the console:

```

sudo apt-get install libgtk2.0-dev

```

---

### Post by hey_ian on 2006-10-08
Never try to compile a prog, which is already precompiled in the repo. Else you will have problems to uninstall it.

---

### Post by YannickDefais on 2006-10-15
Well, i'm not sure for 5.11, but this how-to works for 6.06 (you may have to do some change, or this maybe impossible to achive with ekiga 2.0.3) :

[http://doc.ubuntu-fr.org//applications/ekiga#compilation](http://doc.ubuntu-fr.org//applications/ekiga#compilation)

This process use checkinstall to have a nice uninstall system with synaptic or dpkg. It is in french, but commands are anylang friendly :)

Regards,
Yannick

---

### Post by hey_ian on 2006-10-15
> **YannickDefais said:**
> Well, i'm not sure for 5.11, but this how-to works for 6.06 (you may have to do some change, or this maybe impossible to achive with ekiga 2.0.3) :

[http://doc.ubuntu-fr.org//applications/ekiga#compilation](http://doc.ubuntu-fr.org//applications/ekiga#compilation)

This process use checkinstall to have a nice uninstall system with synaptic or dpkg. It is in french, but commands are anylang friendly :)

Regards,
Yannick
Checkinstall is nice and may be used, but only if there are NO precompiled packages. It is better to use APT.

---

### Post by YannickDefais on 2006-10-15
How do you upgrade to Ekiga 2.0.3 on Ubuntu 5.11 using apt ?

Anyway, i've Ekiga 2.0.3 on my Dapper 6.06 from packages available on ekiga.org and Ekiga CVS from a repository provided by ekiga.org too. Before that i've compiled using checkinstall Ekiga 2.0.3 (and some CVS versions too). I never had a problem...

Regards,
Yannick

---

