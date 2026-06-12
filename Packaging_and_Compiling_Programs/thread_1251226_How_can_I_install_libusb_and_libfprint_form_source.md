---
title: "How can I install libusb and libfprint form source code?"
date: 2009-08-27
forum: Packaging and Compiling Programs
---

### Post by MaikoID on 2009-08-27
Hi,

I'm trying to install an application called [fprint_demo]("http://reactivated.net/fprint/wiki/Fprint_demo") without install any .deb package, and this application is dependent from three libs: (faster to install)[libusb]("http://www.libusb.org/"), (slow)[imagemagick]("http://imagemagick.org/script/index.php"), (faster)[libfprint]("http://reactivated.net/fprint/wiki/Libfprint").

I will put all the installed things in /opt/manual and the fonts in /opt/install, I don't have and I don't want install the package libusb-dev.

I started installing the libusb:
```

mkdir -r /opt/manual
cd /opt/install/libusb-1.0.2/
 ./configure --prefix=/opt/manual --enable-debug-log
.
.
.configure: creating ./config.status
config.status: creating libusb-1.0.pc
config.status: creating Makefile
config.status: creating libusb/Makefile
config.status: creating examples/Makefile
config.status: creating doc/Makefile
config.status: creating doc/doxygen.cfg
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
(no errors)
make
.
.
.
(no errors)
sudo checkinstall -D
.
.
.
**********************************************************************

 Done. The new package has been installed and saved to

 /opt/install/libusb-1.0.2/libusb_1.0.2-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r libusb

**********************************************************************
ls -lhR /opt/manual/
/opt/manual/:
total 8,0K
drwxr-xr-x 3 root root 4,0K 2009-08-27 11:48 include
drwxr-xr-x 3 root root 4,0K 2009-08-27 11:48 lib

/opt/manual/include:
total 4,0K
drwxr-xr-x 2 root root 4,0K 2009-08-27 11:48 libusb-1.0

/opt/manual/include/libusb-1.0:
total 44K
-rw-r--r-- 1 root root 41K 2009-08-27 11:48 libusb.h

/opt/manual/lib:
total 264K
-rw-r--r-- 1 root root 201K 2009-08-27 11:48 libusb-1.0.a
-rwxr-xr-x 1 root root  955 2009-08-27 11:48 libusb-1.0.la
lrwxrwxrwx 1 root root   19 2009-08-27 11:48 libusb-1.0.so -> libusb-1.0.so.0.0.0
lrwxrwxrwx 1 root root   19 2009-08-27 11:48 libusb-1.0.so.0 -> libusb-1.0.so.0.0.0
-rwxr-xr-x 1 root root  50K 2009-08-27 11:48 libusb-1.0.so.0.0.0
drwxr-xr-x 2 root root 4,0K 2009-08-27 11:48 pkgconfig

/opt/manual/lib/pkgconfig:
total 4,0K
-rw-r--r-- 1 root root 255 2009-08-27 11:48 libusb-1.0.pc

```then I create the file manual.conf in /etc/ld.so.conf.d/
```

sudo gedit /etc/ld.so.conf.d/manual.conf

```and put this line
/opt/manual/lib
```

cat /etc/ld.so.conf.d/manual.conf
/opt/manual/lib

```Then I update the ldconfig
```

sudo ldconfig -v
.
.
.
/opt/manual/lib:
    libusb-1.0.so.0 -> libusb-1.0.so.0.0.0
.
.
.

```ok until here? next post I will show the Imagemagick install.

---

### Post by MaikoID on 2009-08-27
Imagemagick install
```

cd /opt/install/ImageMagick-6.5.5-2/
./configure --prefix=/opt/manual --with-perl=no
.
.
.
Options used to compile and link:
  PREFIX          = /opt/manual
  EXEC-PREFIX     = /opt/manual
  VERSION         = 6.5.5
  CC              = gcc -std=gnu99
  CFLAGS          = -fopenmp -g -O2 -Wall -W -pthread
  MAGICK_CFLAGS   = -fopenmp -g -O2 -Wall -W -pthread
  CPPFLAGS        = -I/opt/manual/include/ImageMagick
  PCFLAGS         = -fopenmp
  DEFS            = -DHAVE_CONFIG_H
  LDFLAGS         = -lfreetype -lz
  MAGICK_LDFLAGS  = -L/opt/manual/lib -lfreetype -lz
  LIBS            = -lMagickCore -llcms -lfreetype -ljpeg -lfontconfig -lXext -lSM -lICE -lX11 -lXt -lz -lm -lgomp -lpthread -lltdl
  CXX             = g++
  CXXFLAGS        = -g -O2 -Wall -W -pthread

(no erros)
make
(12 minutes later)
sudo checkinstall -D
**********************************************************************

 Done. The new package has been installed and saved to

 /opt/install/ImageMagick-6.5.5-2/imagemagick-6.5.5_2-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r imagemagick-6.5.5

**********************************************************************

```Then
```

sudo ldconfig -v
.
.
.
/opt/manual/lib:
    libMagick++.so.2 -> libMagick++.so.2.0.0
    libMagickWand.so.2 -> libMagickWand.so.2.0.0
    libusb-1.0.so.0 -> libusb-1.0.so.0.0.0
    libMagickCore.so.2 -> libMagickCore.so.2.0.0
.
.
.

```

next step libfprint T_T

---

### Post by MaikoID on 2009-08-27
libfprint

```

 cd /opt/install/libfprint-0.0.6/
./configure --prefix=/opt/manual/ --enable-debug-log 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
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
checking for inline... inline
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBUSB... configure: error: Package requirements ("libusb") were not met:

No package 'libusb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBUSB_CFLAGS
and LIBUSB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```Why this lib can't find where my libusb are installed ? ldconfig doesn't do that? How can I configure pkg-config to search for .pc files on /opt/manual/lib/pkg-config ??

I have tried it as the [documentation]("http://reactivated.net/fprint/wiki/Installation") says
```

export PKG_CONFIG_PATH=/opt/manual/lib/pkgconfig/:$PKG_CONFIG_PATH

```but when I run ./configure the error persist.
Bye!

---

### Post by MaikoID on 2009-08-28
I found the solution to compile Libfprint.

```

export PKG_CONFIG_PATH=/opt/manual/lib/pkgconfig/:$PKG_CONFIG_PATH
echo $PKG_CONFIG_PATH
/opt/manual/lib/pkgconfig/:

```then

```

pkg-config --cflags libusb-1.0 --libs libusb-1.0
-I/opt/manual/include/libusb-1.0  -L/opt/manual/lib -lusb-1.0  
 ./configure --prefix=/opt/manual --enable-debug-log LIBUSB_CFLAGS=-I/opt/manual/include/libusb-1.0  LIBUSB_LIBS='-L/opt/manual/lib -lusb-1.0'
.
.
.
checking pkg-config is at least version 0.9.0... yes
checking for LIBUSB... yes
checking for CRYPTO... yes
checking for GLIB... yes
checking for IMAGEMAGICK... yes
configure: creating ./config.status
config.status: creating libfprint.pc
config.status: creating Makefile
config.status: creating libfprint/Makefile
config.status: creating examples/Makefile
config.status: creating doc/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
(no errors)

```Why ImageMagick is found and libusb isn't I never you know rsrs.

then more one critical error..

```

make
make  all-recursive
make[1]: Entrando no diretório `/opt/install/libfprint-0.0.6'
Making all in libfprint
make[2]: Entrando no diretório `/opt/install/libfprint-0.0.6/libfprint'
/bin/sh ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -fvisibility=hidden -I./nbis/include -I/opt/manual/include/libusb-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -fopenmp -I/opt/manual/include/ImageMagick    -std=gnu99 -fgnu89-inline -Wall -Wundef -Wunused -Wstrict-prototypes -Werror-implicit-function-declaration -Wno-pointer-sign -Wshadow -g -O2 -MT libfprint_la-core.lo -MD -MP -MF .deps/libfprint_la-core.Tpo -c -o libfprint_la-core.lo `test -f 'core.c' || echo './'`core.c
 gcc -DHAVE_CONFIG_H -I. -I.. -fvisibility=hidden -I./nbis/include -I/opt/manual/include/libusb-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -fopenmp -I/opt/manual/include/ImageMagick -std=gnu99 -fgnu89-inline -Wall -Wundef -Wunused -Wstrict-prototypes -Werror-implicit-function-declaration -Wno-pointer-sign -Wshadow -g -O2 -MT libfprint_la-core.lo -MD -MP -MF .deps/libfprint_la-core.Tpo -c core.c  -fPIC -DPIC -o .libs/libfprint_la-core.o
core.c:25:17: error: usb.h: Arquivo ou diretório inexistente
In file included from core.c:27:
fp_internal.h:67: error: expected specifier-qualifier-list before ‘usb_dev_handle’
fp_internal.h:79: error: expected specifier-qualifier-list before ‘usb_dev_handle’
core.c: In function ‘find_supporting_driver’:
core.c:364: error: dereferencing pointer to incomplete type
core.c:365: error: dereferencing pointer to incomplete type
core.c: In function ‘fp_discover_devs’:
core.c:418: warning: implicit declaration of function ‘usb_find_busses’
core.c:419: warning: implicit declaration of function ‘usb_find_devices’
core.c:426: warning: implicit declaration of function ‘usb_get_busses’
core.c:426: warning: assignment makes pointer from integer without a cast
core.c:426: error: dereferencing pointer to incomplete type
core.c:427: error: dereferencing pointer to incomplete type
core.c:427: error: dereferencing pointer to incomplete type
core.c: In function ‘fp_dev_open’:
core.c:584: error: ‘usb_dev_handle’ undeclared (first use in this function)
core.c:584: error: (Each undeclared identifier is reported only once
core.c:584: error: for each function it appears in.)
core.c:584: error: ‘udevh’ undeclared (first use in this function)
core.c:584: warning: implicit declaration of function ‘usb_open’
core.c:592: error: ‘struct fp_dev’ has no member named ‘udev’
core.c:593: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:599: warning: implicit declaration of function ‘usb_close’
core.c: In function ‘do_close’:
core.c:615: error: ‘struct fp_dev’ has no member named ‘udev’
core.c: In function ‘fp_dev_get_nr_enroll_stages’:
core.c:655: error: ‘struct fp_dev’ has no member named ‘nr_enroll_stages’
core.c: In function ‘fp_dev_get_devtype’:
core.c:665: error: ‘struct fp_dev’ has no member named ‘devtype’
core.c: In function ‘fp_dev_supports_print_data’:
core.c:677: error: ‘struct fp_dev’ has no member named ‘devtype’
core.c: In function ‘fp_dev_supports_dscv_print’:
core.c:692: error: ‘struct fp_dev’ has no member named ‘devtype’
core.c: In function ‘dev_to_img_dev’:
core.c:730: error: ‘struct fp_dev’ has no member named ‘priv’
core.c: In function ‘fp_enroll_finger_img’:
core.c:889: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:892: error: ‘struct fp_dev’ has no member named ‘nr_enroll_stages’
core.c:900: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:903: error: ‘struct fp_dev’ has no member named ‘nr_enroll_stages’
core.c:904: error: ‘struct fp_dev’ has no member named ‘nr_enroll_stages’
core.c:906: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:909: error: ‘struct fp_dev’ has no member named ‘nr_enroll_stages’
core.c:915: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:927: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:931: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:947: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c:951: error: ‘struct fp_dev’ has no member named ‘__enroll_stage’
core.c: In function ‘fp_init’:
core.c:1123: warning: implicit declaration of function ‘usb_init’
make[2]: ** [libfprint_la-core.lo] Erro 1
make[2]: Saindo do diretório `/opt/install/libfprint-0.0.6/libfprint'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/opt/install/libfprint-0.0.6'
make: ** [all] Erro 2

```The make is looking for a header called usb.h

```

find /opt/install/libusb-1.0.2/ /opt/manual/include/ -iname "usb.h"
(nothing)

```What I can do now?

---

### Post by MaikoID on 2009-08-28
I found the solution but isn't the best solution..
I downloaded all libusb-x.x.x from the site [www.libusb.org]("http://www.libusb.org"), and anyone of them does not had the "usb.h" header. Then I got an ideia, I download the .deb package to see if it had the file "usb.h"
```

sudo apt-get install -d libusb-dev
sudo dpkg -x /var/cache/apt/archives/libusb-dev_2%3a0.1.12-13_i386.deb ~/libusb-dev
find /home/maiko/libusb-dev/ -iname "usb.h"
/home/maiko/libusb-dev/usr/include/usb.h

```Omg! Why ?!?!??!?!

not even knowing why

```

sudo cp -a /home/maiko/libusb-dev/usr/include/usb.h /opt/manual/include/libusb-1.0/
make
.
.
.
Making all in doc
make[2]: Entrando no diretório `/opt/install/libfprint-0.0.6/doc'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/opt/install/libfprint-0.0.6/doc'
make[2]: Entrando no diretório `/opt/install/libfprint-0.0.6'
make[2]: Saindo do diretório `/opt/install/libfprint-0.0.6'
make[1]: Saindo do diretório `/opt/install/libfprint-0.0.6'
(no errors)
sudo checkinstall -D
**********************************************************************

 Done. The new package has been installed and saved to

 /opt/install/libfprint-0.0.6/libfprint_0.0.6-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r libfprint

**********************************************************************

```T_T

---

### Post by MaikoID on 2009-08-28
Fprint - finally
```

sudo ldconfig
./configure --prefix=/opt/manual
.
.
.
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FPRINT... yes
checking for GTK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
(no errors)
make
Making all in src
make[1]: Entrando no diretório `/opt/install/fprint_demo-0.4/src'
gcc -DPACKAGE_NAME=\"fprint_demo\" -DPACKAGE_TARNAME=\"fprint_demo\" -DPACKAGE_VERSION=\"0.4\" -DPACKAGE_STRING=\"fprint_demo\ 0.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fprint_demo\" -DVERSION=\"0.4\" -I.    -I/opt/manual/include/libfprint   -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -MT fprint_demo-main.o -MD -MP -MF .deps/fprint_demo-main.Tpo -c -o fprint_demo-main.o `test -f 'main.c' || echo './'`main.c
main.c:22:30: error: libfprint/fprint.h: Arquivo ou diretório inexistente
In file included from main.c:24:
fprint_demo.h:31: warning: ‘enum fp_finger’ declared inside parameter list
fprint_demo.h:31: warning: its scope is only this definition or declaration, which is probably not what you want
.
.
.
(more errors)

```Noooo!

I found this solution, in the gcc line what give the error says:
main.c:22:30: error: libfprint/fprint.h: Arquivo ou diretório inexistente (file not found)
```

gcc -DPACKAGE_NAME=\"fprint_demo\" -DPACKAGE_TARNAME=\"fprint_demo\" -DPACKAGE_VERSION=\"0.4\" -DPACKAGE_STRING=\"fprint_demo\ 0.4\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fprint_demo\" -DVERSION=\"0.4\" -I.    _**-I/opt/manual/include/libfprint**_   -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -MT fprint_demo-main.o -MD -MP -MF .deps/fprint_demo-main.Tpo -c -o fprint_demo-main.o `test -f 'main.c' || echo './'`main.c

```But in code the include is libfprint/fprint.h Then modify the configure to
```

./configure --prefix=/opt/manual FPRINT_CFLAGS=-I/opt/manual/include/
make
gcc -I/opt/manual/include/ -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2   -o fprint_demo fprint_demo-main.o fprint_demo-enroll.o fprint_demo-img.o fprint_demo-verify.o fprint_demo-identify.o -L/opt/manual/lib -lfprint   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   
/opt/manual/lib/libfprint.so: undefined reference to `usb_close'
/opt/manual/lib/libfprint.so: undefined reference to `usb_get_busses'
/opt/manual/lib/libfprint.so: undefined reference to `usb_set_altinterface'
.
.
.
(more errors)

```Grrr!

What is the problem ?

---

