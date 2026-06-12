---
title: "Compiling Gaim - Issues"
date: 2006-06-22
forum: Programming Talk
---

### Post by Shigun on 2006-06-22
Ok, so I try to compile Gaim, the 2_0_0 branch from the SVN.  Got the automake packages and all, but when I go to compile, I get this:

```
eric@Unryu:~/Gaim/2.0-compile$ ./autogen.sh
Generating configuration files for Gaim, please wait....

Running libtoolize, please ignore non-fatal messages....
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
You should add the contents of '/usr/share/aclocal/intltool.m4' to 'aclocal.m4'.aclocal: configure.ac: 50: macro `AM_GLIB_GNU_GETTEXT' not found in library
```

I also tried getting the sourcecode from the website, the latest beta (V3), and configuring it so I could compile, but with that, I get this:

```
eric@Unryu:~/Gaim/gaim-2.0.0beta3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
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
checking whether to build static libraries... no
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for catalogs to be installed...  am az bg bn bs ca ca_ES@valencian cs da de el en_AU en_CA en_GB es et fa fi fr gl gu he hi hu it ja ka ko ku lt mk my_MM nb nl nn pa pl pt_BR pt ro ru sk sl sq sr sr@Latn sv ta te tr uk vi xh zh_CN zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MEANWHILE... no
checking for HOWL... no
checking howl.h usability... no
checking howl.h presence... no
checking for howl.h... no
checking for sw_discovery_init in -lhowl... no
checking for SILC... no
checking for SILC... no
checking for GADU... no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GLIB is incorrectly installed.configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.

```

With Gentoo, I never had an issue of the sort, so I am kind of lost on how to go about resolving it.  I looked for GLib within Synaptic, with no luck on anything that seemed like it was what I needed.  Anybody have some thoughts?

---

### Post by weijie90 on 2006-06-22
try sudo apt-get install libglib1.2-dev

if you run into such ./compile problems, run sudo apt-cache search <name of missing stuff> and install the dev package- i.e. libglib1.2-dev

---

### Post by hod139 on 2006-06-22
[quote=weijie90]try sudo apt-get install libglib1.2-dev
[/quote] 
Not quite,
Configure states```
GLib 2.0 is required to build Gaim
```

so you need the libglib2.0-dev package.

---

