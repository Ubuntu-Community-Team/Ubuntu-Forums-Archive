---
title: "Another compiling problem"
date: 2011-05-15
forum: Packaging and Compiling Programs
---

### Post by kleinempfaenger on 2011-05-15
Hi,
again, a compiling problem. I know it is not an ubuntu problem, but as there is no support for compiling the program I'm talking about, as it is comercial, I dont know where to get help.
It is about QCad, which is in available in the USC. The problem is, that thes community version comes without some important shortcuts. To improve shortcuts, I have to download, modify and compile the source code.
So, I did that, installed QT3, set some variables (QTDIR and QMAKESPEC) and compiled with g++ (and linux-g++-32).
As far as I understand, it didnt come to an end and stopped with an error compiling libdxf.a.

[email]anita@anita-Aspire-one:~/Escritorio/qcad-2.0.5.0-1-community.src[/email]/scripts$ sh ./build_qcad.sh
build_qcad.sh
Usage: ./build_qcad.sh [options]
options:
  demo        build demo version
  debug       add debug menu
  cam         build CAM support if available
  scripting   build scripting support if available
  prof        build professional version
  noclean     don't clean (speeds up building if the options don't change)
  noconfig    don't run configure (speeds up building if the options don't change)
  noprepare   don't run prepare (speeds up building if the options don't change)
  notrans     don't generate translations
  distcc      use distcc for distributed compilation. DISTCC_HOSTS must be set.

QTDIR is: /usr/share/qt3
QMAKESPEC is: /usr/share/qt3/mkspecs/linux-g++-32
[: 48: x: unexpected operator
[: 48: Linux: unexpected operator
[: 48: x: unexpected operator
[: 48: Linux: unexpected operator
Platform is Linux
[: 121: x: unexpected operator
[: 121: xlinux: unexpected operator
[: 131: x: unexpected operator
Target is qcad
[: 148: x: unexpected operator
QMAKE_OPT: 
-------- Building fparser --------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for find... find
checking for makedepend... :
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
checking for ANSI C header files... yes

configure: creating ./config.status
config.status: creating Makefile

Run 'make depend' to create dependencies.

test -d ./include || mkdir -p ./include
( cd ./include; rm -f *.h; \
    for hf in `find ../src -name '*.h'`; do \
        if [ "x$OS" = "xWindows_NT" ]; then \
            cp "$hf" .; \
        else \
            ln -s "$hf" 2> /dev/null; \
        fi \
    done )
-------- Building dxflib --------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for find... find
checking for makedepend... :
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating test/Makefile

Run 'make depend' to create dependencies.

test -d ./include || mkdir -p ./include
( cd ./include; rm -f *.h; \
    for hf in `find ../src -name '*.h'`; do \
        if [ "x$OS" = "xWindows_NT" ]; then \
            cp "$hf" .; \
        else \
            ln -s "$hf" 2> /dev/null; \
        fi \
    done )
gcc -I./src -g -O2  -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DLINUX=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1  -c src/dl_writer_ascii.cpp -o src/dl_writer_ascii.o
In file included from src/dl_writer_ascii.h:35:0,
                 from src/dl_writer_ascii.cpp:34:
src/dl_writer.h: In member function ‘void DL_Writer::entityAttributes(const DL_Attributes&) const’:
src/dl_writer.h:337:54: error: ‘strcasecmp’ was not declared in this scope
src/dl_writer_ascii.cpp: In member function ‘virtual void DL_WriterA::dxfReal(int, double) const’:
src/dl_writer_ascii.cpp:72:40: error: ‘strlen’ was not declared in this scope
src/dl_writer_ascii.cpp:81:37: error: ‘strlen’ was not declared in this scope
src/dl_writer_ascii.cpp: In static member function ‘static void DL_WriterA::strReplace(char*, char, char)’:
src/dl_writer_ascii.cpp:147:24: error: ‘strlen’ was not declared in this scope
make: *** [src/dl_writer_ascii.o] Error 1
Building libdxf.a failed



What is the problem?
Thanks and greetings, kleinempfaenger

---

### Post by kleinempfaenger on 2011-05-16
Hallo.
Please, could anybody help compiling qcad.
Thanks, kl

---

### Post by mc4man on 2011-05-16
I would suggest maybe clicking on 'report abuse' and ask that this thread be moved to here
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)


As far as your first 2 errors you might want to try opening src/dl_writer_ascii.cpp and editing in under #include <stdio.h> a
#include <string.h>

But I see you'll get more errors that will need addressing as you go -  adding a
#include <stdlib.h>
to the respective .cpp, should take care of, though maybe other issues will arise (see debian patch - release_translations

You may find using the latest ubuntu source as your base a little easier and possibly better overall as reading the changelog I see it mentions fixing compile errors... and if your mods can work with a package build even better (patches appiled

Or maybe in the long run just purchase the full version if it includes what is missing, not very expensive

---

### Post by bapoumba on 2011-05-16
Moved to Packaging & Compiling Programs.

---

### Post by kleinempfaenger on 2011-05-24
Thanks mc4man. Changing src/dl_writer_ascii.cpp had effects.
But, I think, there are other errors. Last part says this:

-------- Building qcadlib --------
[: 227: xlinux: unexpected operator
make prepare
make[1]: se ingresa al directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
test -d ./include || mkdir -p ./include
( cd ./include; rm -f *.h; \
    for hf in `find ../src -name '*.h'`; do \
        if [ "x$OS" = "xWindows_NT" ]; then \
            cp "$hf" .; \
        else \
            ln -s "$hf" 2> /dev/null; \
        fi \
    done )
make[1]: se sale del directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
rm -f ./lib/libqcad.a
make ./lib/libqcad.a
make[1]: se ingresa al directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
make src/Makefile
make[2]: se ingresa al directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
make[2]: «src/Makefile» está actualizado.
make[2]: se sale del directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
cd src && make
make[2]: se ingresa al directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib/src»
g++ -c -m32 -pipe -pedantic -Wall -W -O2  -DRS_NO_COMPLEX_ENTITIES -DQT_NO_DEBUG -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/linux-g++-32 -I. -I../include -I../../dxflib/include -I../../fparser/include -I../../qcadcmd/include -I../../../../../include/qt3 -Imoc/ -o obj/rs_information.o information/rs_information.cpp
In file included from ../../../../../include/qt3/qptrcollection.h:44:0,
                 from ../../../../../include/qt3/qgdict.h:45,
                 from ../../../../../include/qt3/qdict.h:45,
                 from ../include/rs_dict.h:31,
                 from ../include/rs_entity.h:33,
                 from ../include/rs_atomicentity.h:31,
                 from ../include/rs_arc.h:30,
                 from ../include/rs_entitycontainer.h:31,
                 from information/rs_information.h:30,
                 from information/rs_information.cpp:27:
../../../../../include/qt3/qglobal.h:734:1: warning: ISO C++ 1998 does not support ‘long long’
../../../../../include/qt3/qglobal.h:735:1: warning: ISO C++ 1998 does not support ‘long long’
information/rs_information.cpp: In static member function ‘static bool RS_Information::isTrimmable(RS_Entity*, RS_Entity*)’:
information/rs_information.cpp:104:22: error: ‘abs’ was not declared in this scope
make[2]: *** [obj/rs_information.o] Error 1
make[2]: se sale del directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib/src»
make[1]: *** [lib/libqcad.a] Error 2
make[1]: se sale del directorio «/usr/local/src/qcad-2.0.5.0-1-community.src/qcadlib»
make: *** [all] Error 2
Building qcadlib failed


You wrote:
"You may find using the latest ubuntu source as your base a little easier  and possibly better overall as reading the changelog I see it mentions  fixing compile errors... and if your mods can work with a package build  even better (patches appiled"

I would like to do what you mention, but I dont know where to find it. Could you please show me?


Thanks, kl

---

