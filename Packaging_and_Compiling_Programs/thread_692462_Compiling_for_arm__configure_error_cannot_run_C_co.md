---
title: "Compiling for arm?  configure: error: cannot run C compiled programs"
date: 2008-02-09
forum: Packaging and Compiling Programs
---

### Post by montgoss on 2008-02-09
I've tried compiling a few things today, and nothing is working anymore.  When I do the typical ./configure, I get the following error:
```
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

config.log says: 
```
configure:2523: result: GNU
configure:2596: checking for gcc
configure:2623: result: ccache arm-angstrom-linux-gnueabi-gcc -march=armv4t -mtune=arm920t
configure:2861: checking for C compiler version
configure:2868: ccache arm-angstrom-linux-gnueabi-gcc -march=armv4t -mtune=arm920t --version >&5
arm-angstrom-linux-gnueabi-gcc (GCC) 4.1.2
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2871: $? = 0
configure:2878: ccache arm-angstrom-linux-gnueabi-gcc -march=armv4t -mtune=arm920t -v >&5
Using built-in specs.
Target: arm-angstrom-linux-gnueabi
Configured with: /builder/newBuild/build/tmp/work/i686-armv4t-sdk-angstrom-linux-gnueabi/gcc-cross-sdk-4.1.2-r10/gcc-4.1.2/configure --build=i686-linux --host=i686-linux --target=arm-angstrom-linux-gnueabi --prefix=/usr/local/openmoko/arm --exec_prefix=/usr/local/openmoko/arm --bindir=/usr/local/openmoko/arm/bin --sbindir=/usr/local/openmoko/arm/bin --libexecdir=/usr/local/openmoko/arm/libexec --datadir=/usr/local/openmoko/arm/share --sysconfdir=/usr/local/openmoko/arm/etc --sharedstatedir=/usr/local/openmoko/arm/share/com --localstatedir=/usr/local/openmoko/arm/var --libdir=/usr/local/openmoko/arm/lib --includedir=/usr/local/openmoko/arm/include --oldincludedir=/usr/local/openmoko/arm/include --infodir=/usr/local/openmoko/arm/share/info --mandir=/usr/local/openmoko/arm/share/man --with-gnu-ld --enable-shared --enable-target-optspace --enable-languages=c,c++ --enable-threads=posix --enable-multilib --enable-c99 --enable-long-long --enable-symvers=gnu --enable-libstdcxx-pch --program-prefix=arm-angstrom-linux-gnueabi- --with-local-prefix=/usr/local/openmoko/arm/local --with-gxx-include-dir=/usr/local/openmoko/arm/include/c++/4.1.2 --with-float=soft --disable-libssp --with-sysroot=/builder/newBuild/build/tmp/work/i686-armv4t-sdk-angstrom-linux-gnueabi/gcc-cross-sdk-4.1.2-r10/sysroot --disable-libunwind-exceptions --with-mpfr=/builder/newBuild/build/tmp/staging/i686-linux --enable-__cxa_atexit
Thread model: posix
gcc version 4.1.2
configure:2881: $? = 0
configure:2888: ccache arm-angstrom-linux-gnueabi-gcc -march=armv4t -mtune=arm920t -V >&5
arm-angstrom-linux-gnueabi-gcc: '-V' must come at the start of the command line
configure:2891: $? = 1
configure:2914: checking for C compiler default output file name
configure:2941: ccache arm-angstrom-linux-gnueabi-gcc -march=armv4t -mtune=arm920t -isystem/usr/local/openmoko/arm/arm-angstrom-linux-gnueabi/include -fexpensive-optimizations -fomit-frame-pointer -frename-registers -Os -isystem/usr/local/openmoko/arm/arm-angstrom-linux-gnueabi/include -L/usr/local/openmoko/arm/arm-angstrom-linux-gnueabi/lib -Wl,-rpath-link,/usr/local/openmoko/arm/arm-angstrom-linux-gnueabi/lib -Wl,-O1 conftest.c  >&5
configure:2944: $? = 0
configure:2982: result: a.out
configure:2999: checking whether the C compiler works
configure:3009: ./a.out
./configure: line 3010: ./a.out: cannot execute binary file
configure:3012: $? = 126
configure:3021: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
```

I've gotten this same error on several different packages now.  I think it's saying that gcc is set to compile for arm (which is possible since I've been doing some stuff with OpenEmbedded).  I did "./configure --host i686" and that seemed to work.  But my default still seems to be arm.  How do I change the default back to i686?


Extra info
```
~$ gcc --version
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

---

### Post by thijs on 2008-02-10
just install g++ to and wil works!

---

### Post by montgoss on 2008-02-12
Not using gcc is not a solution.  :mad:

---

### Post by bgs100 on 2008-12-01
bumping so this will egt more help, as I have the same problem

---

### Post by jpkotta on 2009-01-23
Two things I can think of off the top of my head:
```
readlink -f $(which gcc)
echo $CC
```

Other than that, need more info.

---

### Post by jukzh on 2010-06-24
Ok, help me!
```
readlink -f $(which gcc)
/usr/bin/gcc-4.4
CXX=arm-linux-gnueabi-g++
CC=arm-linux-gnueabi-gcc
AR=arm-linux-gnueabi-ar
./configure arm-linux-gnueabi --target=arm-linux-gnueabi
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for arm-linux-gnueabi-gcc... arm-linux-gnueabi-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: in `/home/user/dev/scim-1.4.9':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```
Ok, next try:
```

./configure --host arm-linux-gnueabi
configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for arm-linux-gnueabi-strip... arm-linux-gnueabi-strip
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for arm-linux-gnueabi-gcc... arm-linux-gnueabi-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... yes
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether arm-linux-gnueabi-gcc accepts -g... yes
checking for arm-linux-gnueabi-gcc option to accept ISO C89... none needed
checking dependency style of arm-linux-gnueabi-gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... arm-unknown-linux-gnueabi
checking for arm-linux-gnueabi-ranlib... arm-linux-gnueabi-ranlib
checking for strerror in -lcposix... no
checking how to run the C preprocessor... /lib/cpp
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... guessing yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... no
checking for working mmap... no
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... guessing no
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/arm-linux-gnueabi/bin/ld
checking if the linker (/usr/arm-linux-gnueabi/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
checking argz.h usability... no
checking argz.h presence... yes
configure: WARNING: argz.h: present but cannot be compiled
configure: WARNING: argz.h:     check for missing prerequisite headers?
configure: WARNING: argz.h: see the Autoconf documentation
configure: WARNING: argz.h:     section "Present But Cannot Be Compiled"
configure: WARNING: argz.h: proceeding with the preprocessor's result
configure: WARNING: argz.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------ ##
configure: WARNING:     ## Report this to suzhe@tsinghua.org.cn ##
configure: WARNING:     ## ------------------------------------ ##
checking for argz.h... yes
checking limits.h usability... no
checking limits.h presence... yes
configure: WARNING: limits.h: present but cannot be compiled
configure: WARNING: limits.h:     check for missing prerequisite headers?
configure: WARNING: limits.h: see the Autoconf documentation
configure: WARNING: limits.h:     section "Present But Cannot Be Compiled"
configure: WARNING: limits.h: proceeding with the preprocessor's result
configure: WARNING: limits.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------ ##
configure: WARNING:     ## Report this to suzhe@tsinghua.org.cn ##
configure: WARNING:     ## ------------------------------------ ##
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... no
checking sys/param.h presence... yes
configure: WARNING: sys/param.h: present but cannot be compiled
configure: WARNING: sys/param.h:     check for missing prerequisite headers?
configure: WARNING: sys/param.h: see the Autoconf documentation
configure: WARNING: sys/param.h:     section "Present But Cannot Be Compiled"
configure: WARNING: sys/param.h: proceeding with the preprocessor's result
configure: WARNING: sys/param.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------ ##
configure: WARNING:     ## Report this to suzhe@tsinghua.org.cn ##
configure: WARNING:     ## ------------------------------------ ##
checking for sys/param.h... yes
checking for asprintf... no
checking for fwprintf... no
checking for getcwd... no
checking for getegid... no
checking for geteuid... no
checking for getgid... no
checking for getuid... no
checking for mempcpy... no
checking for munmap... no
checking for putenv... no
checking for setenv... no
checking for setlocale... no
checking for snprintf... no
checking for stpcpy... no
checking for strcasecmp... no
checking for strdup... no
checking for strtoul... no
checking for tsearch... no
checking for wcslen... no
checking for __argz_count... no
checking for __argz_stringify... no
checking for __argz_next... no
checking for __fsetlocking... no
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... bison
checking version of bison... 2.4.1, ok
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for a sed that does not truncate output... /bin/sed
checking for ld used by arm-linux-gnueabi-gcc... /usr/arm-linux-gnueabi/bin/ld
checking if the linker (/usr/arm-linux-gnueabi/bin/ld) is GNU ld... yes
checking for /usr/arm-linux-gnueabi/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/arm-linux-gnueabi-nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for arm-linux-gnueabi-g++... arm-linux-gnueabi-g++
checking whether we are using the GNU C++ compiler... yes
checking whether arm-linux-gnueabi-g++ accepts -g... yes
checking dependency style of arm-linux-gnueabi-g++... gcc3
checking how to run the C++ preprocessor... /lib/cpp
checking for arm-linux-gnueabi-g77... no
checking for arm-linux-gnueabi-xlf... no
checking for arm-linux-gnueabi-f77... no
checking for arm-linux-gnueabi-frt... no
checking for arm-linux-gnueabi-pgf77... no
checking for arm-linux-gnueabi-cf77... no
checking for arm-linux-gnueabi-fort77... no
checking for arm-linux-gnueabi-fl32... no
checking for arm-linux-gnueabi-af77... no
checking for arm-linux-gnueabi-xlf90... no
checking for arm-linux-gnueabi-f90... no
checking for arm-linux-gnueabi-pgf90... no
checking for arm-linux-gnueabi-pghpf... no
checking for arm-linux-gnueabi-epcf90... no
checking for arm-linux-gnueabi-gfortran... no
checking for arm-linux-gnueabi-g95... no
checking for arm-linux-gnueabi-xlf95... no
checking for arm-linux-gnueabi-f95... no
checking for arm-linux-gnueabi-fort... no
checking for arm-linux-gnueabi-ifort... no
checking for arm-linux-gnueabi-ifc... no
checking for arm-linux-gnueabi-efc... no
checking for arm-linux-gnueabi-pgf95... no
checking for arm-linux-gnueabi-lf95... no
checking for arm-linux-gnueabi-ftn... no
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
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/arm-linux-gnueabi-nm -B output from arm-linux-gnueabi-gcc object... ok
checking for objdir... .libs
checking for arm-linux-gnueabi-ar... arm-linux-gnueabi-ar
checking for arm-linux-gnueabi-ranlib... (cached) arm-linux-gnueabi-ranlib
checking for arm-linux-gnueabi-strip... (cached) arm-linux-gnueabi-strip
checking if arm-linux-gnueabi-gcc supports -fno-rtti -fno-exceptions... no
checking for arm-linux-gnueabi-gcc option to produce PIC... -fPIC
checking if arm-linux-gnueabi-gcc PIC flag -fPIC works... yes
checking if arm-linux-gnueabi-gcc static flag -static works... yes
checking if arm-linux-gnueabi-gcc supports -c -o file.o... yes
checking whether the arm-linux-gnueabi-gcc linker (/usr/arm-linux-gnueabi/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... cross
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by arm-linux-gnueabi-g++... /usr/arm-linux-gnueabi/bin/ld
checking if the linker (/usr/arm-linux-gnueabi/bin/ld) is GNU ld... yes
checking whether the arm-linux-gnueabi-g++ linker (/usr/arm-linux-gnueabi/bin/ld) supports shared libraries... yes
checking for arm-linux-gnueabi-g++ option to produce PIC... -fPIC
checking if arm-linux-gnueabi-g++ PIC flag -fPIC works... yes
checking if arm-linux-gnueabi-g++ static flag -static works... yes
checking if arm-linux-gnueabi-g++ supports -c -o file.o... yes
checking whether the arm-linux-gnueabi-g++ linker (/usr/arm-linux-gnueabi/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dirent.h that defines DIR... no
checking for sys/ndir.h that defines DIR... no
checking for sys/dir.h that defines DIR... no
checking for ndir.h that defines DIR... no
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /usr/lib /lib /usr/lib/mesa /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... no
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... (cached) yes
checking for error_t... no
checking for argz_append... no
checking for argz_create_sep... no
checking for argz_insert... no
checking for argz_next... no
checking for argz_stringify... no
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... no
checking errno.h presence... yes
configure: WARNING: errno.h: present but cannot be compiled
configure: WARNING: errno.h:     check for missing prerequisite headers?
configure: WARNING: errno.h: see the Autoconf documentation
configure: WARNING: errno.h:     section "Present But Cannot Be Compiled"
configure: WARNING: errno.h: proceeding with the preprocessor's result
configure: WARNING: errno.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------ ##
configure: WARNING:     ## Report this to suzhe@tsinghua.org.cn ##
configure: WARNING:     ## ------------------------------------ ##
checking for errno.h... yes
checking for malloc.h... (cached) yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... no
checking for index... no
checking for strrchr... no
checking for rindex... no
checking for memcpy... no
checking for bcopy... no
checking for memmove... no
checking for strcmp... no
checking for closedir... no
checking for opendir... no
checking for readdir... no
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether arm-linux-gnueabi-g++ accepts -g... (cached) yes
checking dependency style of arm-linux-gnueabi-g++... (cached) gcc3
checking for arm-linux-gnueabi-gcc... (cached) arm-linux-gnueabi-gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether arm-linux-gnueabi-gcc accepts -g... (cached) yes
checking for arm-linux-gnueabi-gcc option to accept ISO C89... (cached) none needed
checking dependency style of arm-linux-gnueabi-gcc... (cached) gcc3
checking for doxygen... no
checking for dot... NO
checking for dot... no
dirname: missing operand
Try `dirname --help' for more information.
checking for perl... /usr/bin/perl
checking for xsltproc... /usr/bin/xsltproc
checking for /usr/share/sgml/docbook/xsl-stylesheets/html/tldp-html.xsl... configure: error: cannot check for file existence when cross compiling

```
Help me!!!

---

