---
title: "building gedit from source"
date: 2015-04-19
forum: Programming Talk
---

### Post by theperfectpunk on 2015-04-19
I am having some problems with gedit 3.10.4 for which i also filed a bug at bugzilla. The developer had advised me to check if the problem persists in the latest version of gedit.
I downloaded the latest source fired ./configure and got output as
```
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.21... 0.21 found
checking for perl... /usr/bin/perl
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... file_magic ELF [0-9][0-9]*-bit [LM]SB (shared object|dynamic lib )
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for dlfcn.h... yes
checking for file... /usr/bin/file
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for ranlib... (cached) ranlib
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
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
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for argz.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for LC_MESSAGES... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  az ca cs da de el es et eu fi fr ga gl hu it ja ko lt lv ms nl nn no pl pt pt_BR ru sv sk sl ta tr uk vi wa zh_TW zh_CN
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 >= 1.116.1 libglade-2.0 >= 1.99.11
                         libgnomeprintui-2.0 >= 1.113.0 ... Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found Package libgnomeprintui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeprintui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeprintui-2.0' found
```

Both the packages libgnomeui and libgnomeprintui don't exist in ubuntu repo after introduction of unity anymore. Is there any solution or any other way to go about this problem?

---

### Post by steeldriver on 2015-04-19
What version of Ubuntu are you using? the libgnomeui-dev package appears to be available in 14.04

```

$ apt-cache policy libgnomeui-dev
libgnomeui-dev:
  Installed: (none)
  Candidate: 2.24.5-3
  Version table:
     2.24.5-3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by mc4man on 2015-04-19
The "latest" version of gedit would not be looking for those packages so what exactly are you trying to build?
libgnomeui & libglade-2.0 are in 14.04, libgnomeprintui was dropped some time ago.

Do note that on a default 14.04 you will not be able to build the actual latest gedit (3.16.x) anyway..

---

