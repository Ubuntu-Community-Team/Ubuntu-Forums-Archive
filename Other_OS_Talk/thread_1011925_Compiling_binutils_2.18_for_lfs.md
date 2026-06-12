---
title: "Compiling binutils 2.18 for lfs"
date: 2008-12-15
forum: Other OS Talk
---

### Post by fghj. on 2008-12-15
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc -B/usr/bin/
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc -B/usr/bin/ accepts -g... yes
checking for gcc -B/usr/bin/ option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gnatbind... gnatbind
checking for gnatmake... gnatmake
checking whether compiler driver understands Ada... yes
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for bison... bison -y
checking for bison... bison
checking for gm4... no
checking for gnum4... no
checking for m4... m4
checking for flex... flex
checking for flex... flex
checking for makeinfo... makeinfo
checking for expect... expect
checking for runtest... no
checking for ar... ar
checking for as... as
checking for dlltool... no
checking for ld... (cached) /usr/bin/ld
checking for lipo... no
checking for nm... nm
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking for windmc... no
checking for objcopy... objcopy
checking for objdump... objdump
checking for cc... cc
checking for c++... c++
checking for gcc... gcc
checking for gcj... gcj
checking for gfortran... gfortran
checking for ar... ar
checking for as... as
checking for dlltool... no
checking for ld... ld
checking for lipo... no
checking for nm... nm
checking for objdump... objdump
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking for windmc... no
checking where to find the target ar... just compiled
checking where to find the target as... just compiled
checking where to find the target cc... host tool
checking where to find the target c++... host tool
checking where to find the target c++ for libstdc++... host tool
checking where to find the target dlltool... just compiled
checking where to find the target gcc... host tool
checking where to find the target gcj... host tool
checking where to find the target gfortran... host tool
checking where to find the target ld... just compiled
checking where to find the target lipo... host tool
checking where to find the target nm... just compiled
checking where to find the target objdump... just compiled
checking where to find the target ranlib... just compiled
checking where to find the target strip... just compiled
checking where to find the target windres... just compiled
checking where to find the target windmc... just compiled
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether -fkeep-inline-functions is supported... yes
configure: creating ./config.status
config.status: creating Makefile




cd .. \
	  && CONFIG_FILES=po/Makefile.in:po/Make-in \
	     CONFIG_HEADERS= /bin/bash ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing bfd_stdint.h commands
config.status: executing default commands
make[3]: Leaving directory `/media/lfs/sources/binutils-build/bfd/po'
make[3]: Entering directory `/media/lfs/sources/binutils-build/bfd/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/media/lfs/sources/binutils-build/bfd/po'
make[3]: Entering directory `/media/lfs/sources/binutils-build/bfd'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/media/lfs/sources/binutils-build/bfd'
make[2]: *** [info-recursive] Error 1
make[2]: Leaving directory `/media/lfs/sources/binutils-build/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/media/lfs/sources/binutils-build'
make: *** [all] Error 2

---

### Post by LinuxGuy1234 on 2008-12-15
Try binutils 2.17 from the LFS 6.3 book. Use it when you install Binutils.

---

### Post by nina060609 on 2008-12-16
Changzhou Pu River Co., Ltd. specializing in the production of stainless steel [stainless steel pipe](http://www.pjsteelpipe.com), [stainless steel tube](http://www.pjsteelpipe.com), [seamless steel piping](http://www.pjsteelpipe.com), [seamless pipe](http://www.pjsteelpipe.com)  ,[seamless pipe](http://www.pjsteelpipe.com/)

---

