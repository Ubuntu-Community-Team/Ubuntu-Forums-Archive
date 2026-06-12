---
title: "wma plugin for beep media player"
date: 2005-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by daniel49 on 2005-10-20
have followed the tips for how to do this but its not working for me.
seems to get errors on make command for some reason.

tips: [http://ubuntuforums.org/archive/index.php/t-33213.html](http://ubuntuforums.org/archive/index.php/t-33213.html)

All of the commands below should be typed from a terminal. Applications->System Tools->Terminal

If you don't have the beep media player you can get it via synaptic or:

sudo apt-get install beep-media-player

First download the beep development files:

sudo apt-get install beep-media-player-dev

Download the WMA plugin:
wget [http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz](http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz)

Extract the files
tar -xvzf bmp-wma-0.1.1.tar.gz

Build and install the plugin

cd bmp-wma-0.1.1

./configure

make

sudo make install

That's it! You can now play WMA with Beep Media Player, keep in mind that it still cannot play WMA files with DRM.

Let me repeat this, BEEP CANNOT PLAY WMA FILES WITH DRM! It will open the file and show the title in the window but it will not play it.



******************************************************************



output:
dan@ubuntu:~$ wget [http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz](http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz)
--09:42:32--  [http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz](http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz)
           => `bmp-wma-0.1.1.tar.gz'
Resolving download.berlios.de... 195.37.77.141
Connecting to download.berlios.de|195.37.77.141|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 469,872 (459K) [application/x-gzip]
bmp-wma-0.1.1.tar.gz has sprung into existence.
Retrying.

--09:43:23--  [http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz](http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz)
  (try: 2) => `bmp-wma-0.1.1.tar.gz.1'
Connecting to download.berlios.de|195.37.77.141|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 469,872 (459K) [application/x-gzip]

100%[====================================>] 469,872        3.91K/s    ETA 00:00

09:44:53 (11.93 KB/s) - `bmp-wma-0.1.1.tar.gz.1' saved [469872/469872]

dan@ubuntu:~$ tar -xvzf bmp-wma-0.1.1.tar.gz
bmp-wma-0.1.1
bmp-wma-0.1.1/README
bmp-wma-0.1.1/configure.in
bmp-wma-0.1.1/aclocal.m4
bmp-wma-0.1.1/Makefile.am
bmp-wma-0.1.1/Makefile.in
bmp-wma-0.1.1/config.h.in
bmp-wma-0.1.1/configure
bmp-wma-0.1.1/AUTHORS
bmp-wma-0.1.1/COPYING
bmp-wma-0.1.1/ChangeLog
bmp-wma-0.1.1/INSTALL
bmp-wma-0.1.1/NEWS
bmp-wma-0.1.1/compile
bmp-wma-0.1.1/config.guess
bmp-wma-0.1.1/config.rpath
bmp-wma-0.1.1/config.sub
bmp-wma-0.1.1/depcomp
bmp-wma-0.1.1/install-sh
bmp-wma-0.1.1/ltconfig
bmp-wma-0.1.1/ltmain.sh
bmp-wma-0.1.1/missing
bmp-wma-0.1.1/mkinstalldirs
bmp-wma-0.1.1/bootstrap
bmp-wma-0.1.1/src
bmp-wma-0.1.1/src/Makefile.am
bmp-wma-0.1.1/src/Makefile.in
bmp-wma-0.1.1/src/bmp-wma.c
bmp-wma-0.1.1/src/iir.c
bmp-wma-0.1.1/src/iir.h
bmp-wma-0.1.1/src/libffwma
bmp-wma-0.1.1/src/libffwma/Makefile.am
bmp-wma-0.1.1/src/libffwma/Makefile.in
bmp-wma-0.1.1/src/libffwma/allcodecs.c
bmp-wma-0.1.1/src/libffwma/allformats.c
bmp-wma-0.1.1/src/libffwma/asf.c
bmp-wma-0.1.1/src/libffwma/avcodec.h
bmp-wma-0.1.1/src/libffwma/avformat.h
bmp-wma-0.1.1/src/libffwma/avi.h
bmp-wma-0.1.1/src/libffwma/avio.c
bmp-wma-0.1.1/src/libffwma/avio.h
bmp-wma-0.1.1/src/libffwma/aviobuf.c
bmp-wma-0.1.1/src/libffwma/bswap.h
bmp-wma-0.1.1/src/libffwma/common.c
bmp-wma-0.1.1/src/libffwma/common.h
bmp-wma-0.1.1/src/libffwma/cutils.c
bmp-wma-0.1.1/src/libffwma/dsputil.c
bmp-wma-0.1.1/src/libffwma/dsputil.h
bmp-wma-0.1.1/src/libffwma/fft.c
bmp-wma-0.1.1/src/libffwma/file.c
bmp-wma-0.1.1/src/libffwma/futils.c
bmp-wma-0.1.1/src/libffwma/mdct.c
bmp-wma-0.1.1/src/libffwma/os_support.c
bmp-wma-0.1.1/src/libffwma/os_support.h
bmp-wma-0.1.1/src/libffwma/parser.c
bmp-wma-0.1.1/src/libffwma/simple_idct.c
bmp-wma-0.1.1/src/libffwma/simple_idct.h
bmp-wma-0.1.1/src/libffwma/utils.c
bmp-wma-0.1.1/src/libffwma/wmadata.h
bmp-wma-0.1.1/src/libffwma/wmadec.c
bmp-wma-0.1.1/src/wma123
bmp-wma-0.1.1/src/wma123/Makefile.am
bmp-wma-0.1.1/src/wma123/Makefile.in
bmp-wma-0.1.1/src/wma123/wma123.c
bmp-wma-0.1.1/src/wma123/wma123.h
bmp-wma-0.1.1/src/wma123/playlist.c
bmp-wma-0.1.1/src/wma123/playlist.h
dan@ubuntu:~$ cd bmp-wma-0.1.1
dan@ubuntu:~/bmp-wma-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking for ranlib... (cached) ranlib
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
checking whether to build static libraries... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for bmp >= 0.9.7... yes
checking BEEP_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0
checking BEEP_LIBS... -lbeep -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for gtk+-2.0 >= 2.4.0... yes
checking GTK_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for ANSI C header files... (cached) yes
checking OS.h usability... no
checking OS.h presence... no
checking for OS.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking for inttypes.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for bzero... yes
checking for floor... no
checking for gettimeofday... yes
checking for localtime_r... yes
checking for memmove... yes
checking for memset... yes
checking for pow... no
checking for rint... no
checking for sqrt... no
checking for strcasecmp... yes
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... yes
checking for lrintf... no
checking for localtime_r... (cached) yes
checking whether to include x86 specific optimization code... no
checking whether to include verbose debugging code... no
checking whether to include wma123... no

 bmp-wma version 0.1.1 configured successfully.

Using '/usr/local' for installation.
Using 'gcc' for C compiler.
Building with '-g -O2 ' for C compiler flags.
Building with '' for linker flags.

configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/libffwma/Makefile
config.status: creating src/wma123/Makefile
config.status: creating config.h
config.status: executing depfiles commands
dan@ubuntu:~/bmp-wma-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/dan/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/dan/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/dan/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
In file included from avcodec.h:14,
                 from allcodecs.c:21:
common.h:72: error: array type has incomplete element type
common.h:74: error: array type has incomplete element type
make[3]: *** [libffwma_a-allcodecs.o] Error 1
make[3]: Leaving directory `/home/dan/bmp-wma-0.1.1/src/libffwma'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dan/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dan/bmp-wma-0.1.1'
make: *** [all] Error 2
dan@ubuntu:~/bmp-wma-0.1.1$


any helpful suggestions appreciated
Dan

---

### Post by Darrena on 2005-10-22
You can grab a .deb from:
[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

It is in Breezy-extras section

---

### Post by St3althcAt on 2005-10-24
Thank you man! I was looking forward anxiously to listen to wma files on any media player, downloaded Beep, liked it and then this .deb with the codec and finally done! No longer I need to hear .wma on mplayer or xine.

---

### Post by metalelf0 on 2006-03-31
I had the same problem. Solved it by editing the file src/libffwma/common.h and commented the two lines (72 and 74) causing the problem, just by adding // before each line.

```
72 // extern const struct AVOption avoptions_common[3];
73 #endif
74 // extern const struct AVOption avoptions_workaround_bug[11];
```

It's working, for me, I hope I didn't remove anything critical :)

Bye

---

### Post by flapane on 2006-05-03
same problem here, but I am 64bit, that deb is 32bit

---

### Post by dennis4 on 2006-10-30
> **metalelf0 said:**
> I had the same problem. Solved it by editing the file src/libffwma/common.h and commented the two lines (72 and 74) causing the problem, just by adding // before each line.

```
72 // extern const struct AVOption avoptions_common[3];
73 #endif
74 // extern const struct AVOption avoptions_workaround_bug[11];
```

It's working, for me, I hope I didn't remove anything critical :)

Bye

Works like a charm!! thx :)

---

