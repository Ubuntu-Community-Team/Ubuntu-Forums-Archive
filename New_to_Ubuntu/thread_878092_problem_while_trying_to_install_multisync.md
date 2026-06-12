---
title: "problem while trying to install multisync"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by sn0m on 2008-08-02
Trying to install multisync, but got stuck.
This is the output from command line.
Any idea what am I doing wrong?

sn0m@sn0m-laptop:~/Desktop$ ls
multisync-0.82  multisync-0.82-1.tar  untitled folder
sn0m@sn0m-laptop:~/Desktop$ cd multisync-0.82
sn0m@sn0m-laptop:~/Desktop/multisync-0.82$ ls
ABOUT-NLS     configure     intl         mkinstalldirs         po
aclocal.m4    configure.in  ltmain.sh    multisync.desktop.in  post-install
AUTHORS       COPYING       macros       multisync.glade       README
autogen.sh    depcomp       makeall      multisync.glade2      specs
ChangeLog     doc           makeallroot  multisync.glade2p     src
config.guess  include       Makefile.am  NEWS                  stamp-h.in
config.h.in   INSTALL       Makefile.in  pixmaps               syncengine
config.sub    install-sh    missing      plugins
sn0m@sn0m-laptop:~/Desktop/multisync-0.82$ sudo ./configure 
[sudo] password for sn0m: 
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
sn0m@sn0m-laptop:~/Desktop/multisync-0.82$ 
sn0m@sn0m-laptop:~/Desktop/multisync-0.82$ 


Kind regards
Sokol

---

### Post by eightmillion on 2008-08-02
Try running '**./autogen.sh**' first.

---

### Post by sn0m on 2008-08-04
Hi mate thanks for your reply.
This is what I get:

sn0m@sn0m-laptop:~$ cd ~/Desktop/multisync
sn0m@sn0m-laptop:~/Desktop/multisync$ ls
ABOUT-NLS       config.sub    install-sh     missing               po
aclocal.m4      configure     intl           mkinstalldirs         post-install
AUTHORS         configure.in  libtool        multisync.desktop.in  README
autogen.sh      COPYING       ltmain.sh      multisync.glade       specs
autom4te.cache  CVS           makeall        multisync.glade2      src
ChangeLog       depcomp       makeallroot    multisync.glade2p     stamp-h.in
config.guess    doc           Makefile.am    NEWS
config.h.in     include       Makefile.in    pixmaps
config.log      INSTALL       makesourcetar  plugins
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo ./autogen.sh
configure.in:37: warning: macro `AM_ICONV' not found in library
configure.in:15: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:37: error: possibly undefined macro: AM_ICONV
autoreconf: /usr/bin/autoconf failed with exit status: 1
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for bison... no
checking for byacc... no
./configure: line 5576: AC_PROG_LIBTOOL: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (libgnomeui-2.0 libbonobo-2.0 glib-2.0 gconf-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'libbonobo-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

sn0m@sn0m-laptop:~/Desktop/multisync$ sudo make install
make: *** No rule to make target `install'. Stop.
sn0m@sn0m-laptop:~/Desktop/multisync$ 


?don't know what am i doing wrong...
Ta
Sokol

---

### Post by Ptero-4 on 2008-08-04
install gnome-core-devel from aptitude or synaptic.

---

### Post by sn0m on 2008-08-05
Hi mate, thnks for your help.
This is the outcome after installing the gnome-core-devel

Building tag database... Done             
sn0m@sn0m-laptop:~$ cd Desktop
sn0m@sn0m-laptop:~/Desktop$ ls
experimental  multisync  multisync-cvs-snapshot.tar.gz  untitled folder
sn0m@sn0m-laptop:~/Desktop$ 
sn0m@sn0m-laptop:~/Desktop$ cd multisync
sn0m@sn0m-laptop:~/Desktop/multisync$ ls
ABOUT-NLS       config.sub    install-sh     missing               po
aclocal.m4      configure     intl           mkinstalldirs         post-install
AUTHORS         configure.in  libtool        multisync.desktop.in  README
autogen.sh      COPYING       ltmain.sh      multisync.glade       specs
autom4te.cache  CVS           makeall        multisync.glade2      src
ChangeLog       depcomp       makeallroot    multisync.glade2p     stamp-h.in
config.guess    doc           Makefile.am    NEWS
config.h.in     include       Makefile.in    pixmaps
config.log      INSTALL       makesourcetar  plugins
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for bison... no
checking for byacc... no
./configure: line 5576: AC_PROG_LIBTOOL: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
./configure: line 5819: AM_ICONV: command not found
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/libversit/Makefile
config.status: WARNING:  src/libversit/Makefile.in seems to ignore the --datarootdir setting
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating specs/multisync.spec
config.status: creating multisync.desktop
config.status: creating config.h
config.status: executing depfiles commands
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo ./autogen.sh
configure.in:37: required file `./config.rpath' not found
configure.in: installing `./ylwrap'
autoreconf: automake failed with exit status: 1
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for bison... no
checking for byacc... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/libversit/Makefile
config.status: WARNING:  src/libversit/Makefile.in seems to ignore the --datarootdir setting
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating specs/multisync.spec
config.status: creating multisync.desktop
config.status: creating config.h
config.status: executing depfiles commands
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo make
make  all-recursive
make[1]: Entering directory `/home/sn0m/Desktop/multisync'
Making all in src
make[2]: Entering directory `/home/sn0m/Desktop/multisync/src'
Making all in libversit
make[3]: Entering directory `/home/sn0m/Desktop/multisync/src/libversit'
yacc  -pversit_ `test -f 'vcc.y' || echo './'`vcc.y
/bin/bash: yacc: command not found
make[3]: *** [vcc.c] Error 127
make[3]: Leaving directory `/home/sn0m/Desktop/multisync/src/libversit'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sn0m/Desktop/multisync/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sn0m/Desktop/multisync'
make: *** [all] Error 2
sn0m@sn0m-laptop:~/Desktop/multisync$ sudo make install
Making install in src
make[1]: Entering directory `/home/sn0m/Desktop/multisync/src'
Making install in libversit
make[2]: Entering directory `/home/sn0m/Desktop/multisync/src/libversit'
yacc  -pversit_ `test -f 'vcc.y' || echo './'`vcc.y
/bin/bash: yacc: command not found
make[2]: *** [vcc.c] Error 127
make[2]: Leaving directory `/home/sn0m/Desktop/multisync/src/libversit'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sn0m/Desktop/multisync/src'
make: *** [install-recursive] Error 1
sn0m@sn0m-laptop:~/Desktop/multisync$ 


Ta
Sokol

---

### Post by dca on 2008-08-05
Isn't multisync available from the repos instead of doing all this?  Click on the 'Applications' menu, select 'Add/Remove Software', select 'All Available Apps' from drop-down menu and type 'multisync' as your search string and it should show up...

---

### Post by eightmillion on 2008-08-05
I just built this program on a fresh ubuntu virtual machine. I had to install **libgnomeui-dev** and **libtool**. Make sure those are installed and then run **./autogen.sh **again. There were a few warnings, but it compiled fine.

---

### Post by sn0m on 2008-08-06
dcr, thanks for your reply, i have done that but when i tried to sync my phone contacts and calendar with it, it get stuck at waiting for change....
Therefore decided to have a go at compiling it myself from the official website. I believe that's the fun of using linux, you can do stuff with your machine rather then given to you in a plate...
Regards
Sokol

---

