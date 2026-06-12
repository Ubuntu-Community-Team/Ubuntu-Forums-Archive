---
title: "ksqlanalyzer - problem when compiling"
date: 2006-04-04
forum: Programming Talk
---

### Post by ZiZe on 2006-04-04
Hello.

I work alot with sql server 2000 and found this query analyzer tool for linux, but i have som problems compiling it.

First i had some problems with the compiler and missing libraries. but when all was installed, i get another problem

first i run: ./configure --with-qt-dir=/usr/share/qt3
(without `--with-qt-dir=` configure fails)
```

zize@clain:/lager/download/apps/ksqlanalyzer$ ./configure --with-qt-dir=/usr/share/qt3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
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
checking for dlopen in -ldl... yes
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
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking if doc should be compiled... yes
checking if ksqlanalyzer should be compiled... yes
checking if po should be compiled... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/en/Makefile
config.status: creating ksqlanalyzer/Makefile
config.status: creating ksqlanalyzer/kwrite/Makefile
config.status: creating ksqlanalyzer/pix/Makefile
config.status: creating ksqlanalyzer/tds/Makefile
config.status: creating po/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands

```.

but when i run make i get alot of errors that i just cant make out.
```

zize@clain:/lager/download/apps/ksqlanalyzer$ make
cd . \
&& CONFIG_FILES= CONFIG_HEADERS=config.h \
/bin/sh ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/lager/download/apps/ksqlanalyzer'
Making all in ksqlanalyzer
make[2]: Entering directory `/lager/download/apps/ksqlanalyzer/ksqlanalyzer'
Making all in kwrite
make[3]: Entering directory `/lager/download/apps/ksqlanalyzer/ksqlanalyzer/kwrite'
/usr/share/qt3/bin/moc ./kwview.h -o kwview.moc
source='kwview.cpp' object='kwview.o' libtool=no \
depfile='.deps/kwview.Po' tmpdepfile='.deps/kwview.TPo' \
depmode=gcc3 /bin/sh ../../admin/depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wbad-function-cast -Wundef -Wall -W -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -O2 -fno-exceptions -fno-check-new -fexceptions  -c -o kwview.o `test -f kwview.cpp || echo './'`kwview.cpp
cc1plus: warning: command line option "-Wbad-function-cast" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from kwview.cpp:1:
kwview.h:6:21: error: qscrbar.h: No such file or directory
kwview.h:7:20: error: qiodev.h: No such file or directory
In file included from kwview.h:13,
                 from kwview.cpp:1:
kwdialog.h:7:20: error: qlined.h: No such file or directory
kwdialog.h:8:21: error: qchkbox.h: No such file or directory
kwdialog.h:9:22: error: qradiobt.h: No such file or directory
In file included from kwview.cpp:2:
kwdoc.h:5:19: error: qlist.h: No such file or directory
kwdoc.h:8:22: error: qfontmet.h: No such file or directory
In file included from kwdoc.h:16,
                 from kwview.cpp:2:
highlight.h:7:20: error: qcombo.h: No such file or directory
kwview.cpp:16:21: error: qmsgbox.h: No such file or directory
kwview.cpp:18:22: error: qfileinf.h: No such file or directory
kwview.cpp:26:22: error: qclipbrd.h: No such file or directory
kwdialog.h:29: error: ISO C++ forbids declaration of 'QComboBox' with no type
kwdialog.h:29: error: expected ';' before '*' token
kwdialog.h:30: error: ISO C++ forbids declaration of 'QComboBox' with no type
kwdialog.h:30: error: expected ';' before '*' token
kwdialog.h:32: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:32: error: expected ';' before '*' token
kwdialog.h:33: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:33: error: expected ';' before '*' token
kwdialog.h:34: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:34: error: expected ';' before '*' token
kwdialog.h:35: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:35: error: expected ';' before '*' token
kwdialog.h:36: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:36: error: expected ';' before '*' token
kwdialog.h:37: error: ISO C++ forbids declaration of 'QCheckBox' with no type
kwdialog.h:37: error: expected ';' before '*' token
kwdialog.h:60: error: ISO C++ forbids declaration of 'QLineEdit' with no type
kwdialog.h:60: error: expected ';' before '*' token
highlight.h:19: warning: 'class HlItem' has virtual functions but non-virtual destructor
highlight.h:29: warning: 'class HlItemWw' has virtual functions but non-virtual destructor
highlight.h:37: warning: 'class HlCharDetect' has virtual functions but non-virtual destructor
highlight.h:45: warning: 'class Hl2CharDetect' has virtual functions but non-virtual destructor
kwview.cpp: In member function 'virtual void KWriteView::focusInEvent(QFocusEvent*)':
kwview.cpp:729: error: invalid use of undefined type 'struct QClipboard'
/usr/share/qt3/include/qwindowdefs.h:81: error: forward declaration of 'struct QClipboard'
kwview.cpp: At global scope:
kwview.cpp:1043: warning: unused parameter 'dl'
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
make[3]: *** [kwview.o] Error 1
make[3]: Leaving directory `/lager/download/apps/ksqlanalyzer/ksqlanalyzer/kwrite'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/lager/download/apps/ksqlanalyzer/ksqlanalyzer'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/lager/download/apps/ksqlanalyzer'
make: *** [all] Error 2

```

im sure all libraries needed is installed, and right version.
homepage for til application is:
[www.kpage.de/en/](www.kpage.de/en/)

edit:
im running Kubuntu 5.10 with Qt 3.3.4 and KDE 3.4.3


Anyone have an idea what i need?

---

### Post by Sef on 2006-04-04
Did u download build-essential? If not, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by ZiZe on 2006-04-04
yes, built-essential is installed.
just cant figure it out :-k

---

### Post by hod139 on 2006-04-04
The errors are that make can't find a bunch of headers, e.g.
```

In file included from kwview.cpp:1:
kwview.h:6:21: error: qscrbar.h: No such file or directory
kwview.h:7:20: error: qiodev.h: No such file or directory 

``` 
which is most likely caused by a bad configure. The configure line should set up the paths for the includes, which means you are most likely configuring wrong. Looking at:
```
./configure --with-qt-dir=/usr/share/qt3
``` doesn't look right to me.  have you tried
```
./configure --with-qt-dir=usr/include/qt3/
```
Or there may be another configure option for setting the qt header path.  You can usually run
```
./configure --help
```
to find a list of all options.

---

### Post by theToolman on 2006-07-23
> **ZiZe said:**
>  ./configure --with-qt-dir=/usr/share/qt3


Hello; 
This gave me the exact same error; turned out that I needed the package "libqt3-compat-headers".  Once this was apt-got, the make worked correctly.

It did install it in a weird place that wasnt on my path tho; one of the config options should probably be set to install it somewhere better:

/usr/local/kde/bin/ksqanalyzer/

Running an old skool hoary install FYI.

---

### Post by theToolman on 2006-07-23
Reh it installs but still has a few problems; didnt put ksqlanalyzerui.rc where it was supposed to...

---

