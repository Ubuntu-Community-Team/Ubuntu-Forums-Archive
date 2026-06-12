---
title: "[SOLVED] Webkit web browser?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-06-20
I am looking for a web browser that can get 100/100 on acid3 test. I read a month or two ago that webkit could do that. I don't know where or how to go about it. Anyone know anything about it?

---

### Post by kernelhaxor on 2008-06-20
[http://webkit.org/](http://webkit.org/) Is that wht u r talkin abt?

It has a download link to download nightly builds but I can't find stable releases though

---

### Post by Hospadar on 2008-06-20
I think opera claims a high level of acid compatability, you might try that.  Also I know safari supposedly passes acid2, you could run the windows version through wine maybe.

---

### Post by Famicommander on 2008-06-20
Opera 9.5 does great on the Acid1 and Acid2 tests, and it outperforms its main competitors by a wide margin on the Acid3 test. 

From a technical standpoint, Opera is by far the most capable mainstream web browser:
[http://en.wikipedia.org/wiki/Comparison_of_web_browsers](http://en.wikipedia.org/wiki/Comparison_of_web_browsers)
[http://en.wikipedia.org/wiki/Opera_browser](http://en.wikipedia.org/wiki/Opera_browser)

I don't know a whole lot about webkit, but I do know that Opera is very well-supported and you can't do much better than it.

---

### Post by slughappy1 on 2008-06-21
Ok, when I was trying to install ( or build ) webkit I get this error.
```
jason@Tux:~$ WebKit/WebKitTools/Scripts/build-webkit
Unsupported platform, can't determine built library locations. at /home/jason/WebKit/WebKitTools/Scripts/webkitdirs.pm line 374.
jason@Tux:~$ 

```

---

### Post by slughappy1 on 2008-06-21
I changed how I was trying to go about it. I found [this]("http://trac.webkit.org/wiki/BuildingQtOnLinux#BuildingtheQtportonLinux") website. I followed the guide, but now I am stuck on Build Webkit. It says "Finally, set the QTDIR environment variable to Qt 4.x's installation path and make sure Qt 4.x's qmake is the first qmake in your PATH (typically by running export PATH=$QTDIR/bin:$PATH). If your qmake binary has a different name, e.g. when using Debian, use the --qmake= option to specify the name." But I don't know what that means. When I try and compile it I get this error ```
jason@Tux:~$ WebKit/WebKitTools/Scripts/build-webkit --qt
Can't exec "qmake": No such file or directory at /home/jason/WebKit/WebKitTools/Scripts/webkitdirs.pm line 736.
Use of uninitialized value in scalar chomp at /home/jason/WebKit/WebKitTools/Scripts/webkitdirs.pm line 736.
Calling 'qmake CONFIG+=qt-port -r OUTPUT_DIR=/home/jason/WebKit/WebKitBuild/Release /home/jason/WebKit/WebKit.pro CONFIG+=release CONFIG-=debug' in /home/jason/WebKit/WebKitBuild/Release

Can't exec "qmake": No such file or directory at /home/jason/WebKit/WebKitTools/Scripts/webkitdirs.pm line 856.
Failed to setup build environment using qmake!
jason@Tux:~$
``` What can I do to fix this?

---

### Post by lvlo on 2008-06-21
```
sudo apt-get install libqt4-dev
``` should help

---

### Post by spupy on 2008-06-21
I got Epiphany with WebKit. It scores 100/100 on Acid3. Here is the howto I used:
[http://fosswire.com/2007/12/02/compile-epiphany-from-source-to-use-webkit/](http://fosswire.com/2007/12/02/compile-epiphany-from-source-to-use-webkit/)

---

### Post by slughappy1 on 2008-06-24
Ok, I went to that website and started to guide. But now I get an error when I try and compile WebKit, something about autotools
```
jason@Tux:~/WebKit$ ./WebKitTools/Scripts/build-webkit --qmakearg=WEBKIT_INC_DIR=$PREFIX/include/WebKit --qmakearg=WEBKIT_LIB_DIR=$PREFIX/lib --gtk --qmake=qmake-qt4
Calling configure in /home/jason/WebKit/WebKitBuild/Release

configure.ac:65: installing `./compile'
configure.ac:25: installing `./install-sh'
configure.ac:25: installing `./missing'
GNUmakefile.am: installing `./depcomp'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
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
checking whether gcc and cc understand -c and -o together... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking if g++ supports -fvisibility=hidden -fvisibility-inlines-hidden... yes
checking for perl... /usr/bin/perl
checking for bison... /usr/bin/bison
checking for flex... /usr/bin/flex
checking for gperf... /usr/bin/gperf
checking for mv... /bin/mv
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for glib-mkenums... /usr/bin/glib-mkenums
configure: error: No C++ compiler found
Failed to setup build environment using 'autotools'!
jason@Tux:~/WebKit$ 
```

---

### Post by spupy on 2008-06-24
> **slughappy1 said:**
> Ok, I went to that website and started to guide. But now I get an error when I try and compile WebKit, something about autotools
```
configure: error: No C++ compiler found
Failed to setup build environment using 'autotools'!
jason@Tux:~/WebKit$ 
```

Maybe you need a... C++ compile? :) In Ubuntu you have to install the "build-essentials" package.

---

### Post by slughappy1 on 2008-07-03
So I installed build-essentials, but now I have a new one. ```
jason@Tux:~/webkit$ ./WebKitTools/Scripts/build-webkit --qmakearg=WEBKIT_INC_DIR=$PREFIX/include/WebKit --qmakearg=WEBKIT_LIB_DIR=$PREFIX/lib --gtk --qmake=qmake-qt4
Calling configure in /home/jason/webkit/WebKitBuild/Release

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
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
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking whether to build static libraries... no
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
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking if g++ supports -fvisibility=hidden -fvisibility-inlines-hidden... yes
checking for perl... /usr/bin/perl
checking for bison... /usr/bin/bison
checking for flex... /usr/bin/flex
checking for gperf... /usr/bin/gperf
checking for mv... /bin/mv
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for glib-mkenums... /usr/bin/glib-mkenums
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working volatile... yes
checking for ANSI C header files... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking the Unicode backend to use... icu
checking for icu-config... /usr/bin/icu-config
checking the target windowing system... x11
checking for Hildon UI extensions... no
checking the HTTP backend to use... curl
checking for GLOBALDEPS... yes
checking for WEBKITDEPS... configure: error: Package requirements (gtk+-2.0 >= 2.8
                  pango >= 1.0
                  cairo >= 1.4
                  libxml-2.0 >= 2.6) were not met:

No package 'gtk+-2.0' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WEBKITDEPS_CFLAGS
and WEBKITDEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Failed to setup build environment using 'autotools'!
jason@Tux:~/webkit$ 
```

---

