---
title: "QT headers not found."
date: 2008-09-13
forum: Packaging and Compiling Programs
---

### Post by Ephemeral on 2008-09-13
Hello,

I am trying to install v4lgrav-0.2.2, but during the ./config I get the following error :

```
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```

I have tried everything I could think of and installed many QT libraries, headers and all sorts of other things that looked like they could help.

I also searched a bit, and found a command to show all the QT stuff, so I'll give you my output

```
sudo apt-cache search libqt | grep mt
[sudo] password for eternal: 
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)
libqt3-mt-mysql - MySQL database driver for Qt3 (Threaded)
libqt3-mt-odbc - ODBC database driver for Qt3 (Threaded)
libqt3-mt-psql - PostgreSQL database driver for Qt3 (Threaded)
libqt3-mt-sqlite - SQLite database driver for Qt3 (Threaded)

```


Any ideas?

Cheers,
Mark

---

### Post by InfinityCircuit on 2008-09-14
libqt3-mt-dev - Qt development files (Threaded)

This is what you want.

---

### Post by Ephemeral on 2008-09-15
> **InfinityCircuit said:**
> libqt3-mt-dev - Qt development files (Threaded)

This is what you want.

That package is already installed :(

Any other suggestions?

---

### Post by InfinityCircuit on 2008-09-15
```
x40:/home/dmoerner# aptitude search ~nqt~Wdev
p   libace-qtreactor-dev              - ACE-GUI reactor integration for Qt developme
p   libavahi-qt3-dev                  - Development headers for the Avahi Qt 3 integ
p   libavahi-qt4-dev                  - Development headers for the Avahi Qt 4 integ
p   libdbus-qt-1-dev                  - simple interprocess messaging system (Qt int
p   libpoppler-qt-dev                 - PDF rendering library -- development files (
p   libpoppler-qt4-dev                - PDF rendering library -- development files (
p   libqt3-mt-dev                     - Qt development files (Threaded)             
p   libqt4-dev                        - Qt 4 development files                      
p   libqt4-opengl-dev                 - Qt 4 OpenGL library development files       
p   libqwt5-qt3-dev                   - Qt3 widgets library for technical applicatio
p   libqwt5-qt4-dev                   - Qt4 widgets library for technical applicatio
p   libqwtplot3d-qt3-dev              - 3D plotting library based on Qt3/OpenGL (dev
p   libqwtplot3d-qt4-dev              - 3D plotting library based on Qt4/OpenGL (dev
p   libsmokeqt-dev                    - SMOKE Binding Library to Qt - Development Fi
p   libsmokeqt4-dev                   - Smoke library for Qt4                       
v   libsoqt-dev                       -                                             
p   libsoqt-dev-common                - Qt GUI component toolkit for Inventor - comm
p   libsoqt3-dev                      - Qt3 GUI component toolkit for Inventor - dev
p   libsoqt4-dev                      - Qt4 GUI component toolkit for Inventor - dev
p   libstrigiqtdbusclient-dev         - development files for libstrigiqtdbusclient 
p   libsvnqt-dev                      - Qt wrapper library for subversion (developme
p   libtao-qtresource-dev             - TAO-GUI reactor integration for Qt developme
v   libtulip-qt-dev                   -                                             
p   libtulip-qt4-3.0-dev              - Tulip graph library - Qt/OpenGL GUI developm
p   libvtk5-qt3-dev                   - Visualization Toolkit - A high level 3D visu
p   libvtk5-qt4-dev                   - Visualization Toolkit - A high level 3D visu
p   pyqt4-dev-tools                   - Development tools for PyQt4                 
p   python-qt-dev                     - Qt bindings for Python - Development files  
p   python-qt4-dev                    - Development files for PyQt4                 
p   qt3-apps-dev                      - Qt3 Developer applications development files
p   qt3-dev-tools                     - Qt3 development tools                       
p   qt3-dev-tools-compat              - Conversion utilities for Qt3 development    
p   qt3-dev-tools-embedded            - Tools to develop embedded Qt applications   
p   qt4-dev-tools                     - Qt 4 development tools
```

qt3-dev-tools looks like a possible candidate, alongwith qt3-apps-dev.

---

### Post by Ephemeral on 2008-09-16
Installed both, still the same error.
I read somewhere about files that need to be moved to the right directory or something like that, any idea?

---

### Post by Partyboi2 on 2008-09-17
try this:
```
./configure --with-qt-includes=/usr/include/qt3 
```

---

### Post by Ephemeral on 2008-10-04
> **Partyboi2 said:**
> try this:
```
./configure --with-qt-includes=/usr/include/qt3 
```

Hello, sorry for long time response :p

Anyways, here is what I get :

```
eternal@eternal-desktop:~/v4lgrab-0.2.2$ ./configure --with-qt-includes=/usr/include/qt3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking for nasm... /usr/bin/nasm
checking for msgfmt... msgfmt
checking for gmsgfmt... msgfmt
found msgfmt program is not GNU msgfmt; ignore it
checking for xgettext... :
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
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
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking for vsnprintf... yes
checking for snprintf... yes
not using lib directory suffix
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... libraries /usr/lib, headers /usr/include/qt3 using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/bin/moc
checking for uic... /usr/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking semaphore.h usability... yes
checking semaphore.h presence... yes
checking for semaphore.h... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking POSIX termios... yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
checking for struct v4l2_capability.type... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking for sdl-config... /usr/bin/sdl-config
checking for avifile-config... /usr/bin/avifile-config
checking for doxygen... no
configure: Doxygen not found, so API documentation could not build.
configure: creating ./config.status
config.status: creating Makefile
config.status: creating docs/Makefile
config.status: creating contrib/Makefile
config.status: creating src/Makefile
config.status: creating src/buffer/Makefile
config.status: creating src/video/Makefile
config.status: creating src/video/v4l/Makefile
config.status: creating src/video/v4l2/Makefile
config.status: creating src/dsp/Makefile
config.status: creating src/settings/Makefile
config.status: creating src/mixer/Makefile
config.status: creating src/sdl/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/asm/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands

Summary:
nasm   :  /usr/bin/nasm 
avifile:  CFLAGS=-I/usr/include/avifile-0.7 & LDFLAGS=-laviplay -ldts -lm -lz 
sdl    :  CFLAGS=-I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT & LDFLAGS=-L/usr/lib -lSDL 
Doxygen:  no 

DSP extensions: 
MMX SSE SSE2 

Video4Linux2 interface not found.
eternal@eternal-desktop:~/v4lgrab-0.2.2$ make
Making all in src
make[1]: Entering directory `/home/eternal/v4lgrab-0.2.2/src'
make  all-recursive
make[2]: Entering directory `/home/eternal/v4lgrab-0.2.2/src'
Making all in buffer
make[3]: Entering directory `/home/eternal/v4lgrab-0.2.2/src/buffer'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src -I/usr/include/kde -I/usr/include/qt3 -DDEBUG_PREFIX='"DBG_BUFFER: "' -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -O2 -fno-check-new -fno-common  -MT list.o -MD -MP -MF ".deps/list.Tpo" \
	  -c -o list.o `test -f 'list.cpp' || echo './'`list.cpp; \
	then mv ".deps/list.Tpo" ".deps/list.Po"; \
	else rm -f ".deps/list.Tpo"; exit 1; \
	fi
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from ../../src/v4lgrab.h:102,
                 from list.cpp:2:
/usr/include/avifile/except.h:4:2: warning: #warning Use #include "avm_except.h" instead
In file included from ../../src/v4lgrab.h:103,
                 from list.cpp:2:
/usr/include/avifile/creators.h:4:2: warning: #warning Use #include "avm_creators.h" instead
In file included from ../../src/v4lgrab.h:138,
                 from list.cpp:2:
../../src/tools.h:46:5: warning: "HAVE_MMX2" is not defined
In file included from ../../src/v4lgrab.h:138,
                 from list.cpp:2:
../../src/tools.h:34: error: extra &#8216;;&#8217;
../../src/tools.h:42: warning: unused parameter &#8216;frame&#8217;
../../src/tools.h:42: warning: unused parameter &#8216;width&#8217;
../../src/tools.h:42: warning: unused parameter &#8216;height&#8217;
../../src/tools.h:50: error: extra &#8216;;&#8217;
make[3]: *** [list.o] Error 1
make[3]: Leaving directory `/home/eternal/v4lgrab-0.2.2/src/buffer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/eternal/v4lgrab-0.2.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/eternal/v4lgrab-0.2.2/src'
make: *** [all-recursive] Error 1
eternal@eternal-desktop:~/v4lgrab-0.2.2$ 

```

So the configuration works, but says I don't have Video4Linux2 and then the make fails.
Any ideas?

*Edit* : I did a quick research, and this is what I found :

```
v4l2 on 2.6.x kernels

kernel 2.6.x already has everything included. Just enable the config options you need (i2c, video4linux and the actual driver), compile your kernel and you are done.

If you run into trouble you can check if there are updates with fixes in the patch directory.
```

I am using a 2.6 kernel, how can I enable i2c, video4linux and my eyetoy driver?

---

