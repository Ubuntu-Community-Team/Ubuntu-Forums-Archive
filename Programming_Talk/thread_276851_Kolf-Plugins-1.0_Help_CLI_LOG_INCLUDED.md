---
title: "Kolf-Plugins-1.0 Help CLI LOG INCLUDED"
date: 2006-10-13
forum: Programming Talk
---

### Post by Krispy101 on 2006-10-13
Hey, I'm trying to install Kolf Plugins, after succesfully installing kolf, but was wondering why this error happens, and how to fix it??

Below is the CLI log, and below that is config.log:


I hope you guys can help, thanks, in anticipation, Kris

**BEGIN CLI LOG**

kris@Kris-Ubuntu:~/kolf-plugins-1.0$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix...
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wbad-function-cast... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -frepo... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output...
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... no
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
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
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking for CoreAudio/CoreAudio.h... no
checking for res_init... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for char... yes
checking size of char... 1
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for Xinerama... no
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

**END CLI LOG**

Thanks, in anticipation, Kris

P.S. Config.log is in next post

---

### Post by Krispy101 on 2006-10-13
Config.log link below.. click on free, then download now

[Config.log in a  text file]("http://rapidshare.de/files/36618545/config.txt.html")

---

### Post by duff on 2006-10-13
you need the libqt3-dev package installed.

---

### Post by Krispy101 on 2006-10-13
Now this comes up :(

when i try and install libqt3-dev

kris@Kris-Ubuntu:~$ sudo apt-get install libqt3-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Package libqt3-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  qt3-qtconfig qt3-linguist qt3-dev-tools-embedded qt3-dev-tools-compat
  qt3-designer qt3-assistant qt3-dev-tools qt3-apps-dev libqt3-mt-dev
  libqt3-headers libqt3-compat-headers
E: Package libqt3-dev has no installation candidate

---

### Post by Krispy101 on 2006-10-13
BUMP please reply ASAP please :( *whines*

---

### Post by duff on 2006-10-14
Uh, it tells you that those packages replace libqt3-dev...so install them.

---

### Post by Krispy101 on 2006-10-14
Yes, I installed them, They still didn't work.....

---

