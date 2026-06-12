---
title: "Can't Compile/Install Libusb 1.0.9"
date: 2016-01-05
forum: Packaging and Compiling Programs
---

### Post by carlm3 on 2016-01-05
Hello Everyone.

I can't compile downloaded version of libusb 1.0.9 which is needed for my other program. I am using root through terminal, and I used ./configure as it says in the instructions, and it seems to configure correctly, but when I use "make" and "make install" it doesnt seem to install it. My Ubuntu is on a fresh DVD install of the latest version Ubuntu 15.10


root@Ubuntu-PC:/home/carl/Desktop/libusb-1.0.9# make
make  all-recursive
make[1]: Entering directory '/home/carl/Desktop/libusb-1.0.9'
Making all in libusb
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9/libusb'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/libusb'
Making all in doc
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9'
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9'
make[1]: Leaving directory '/home/carl/Desktop/libusb-1.0.9'
root@Ubuntu-PC:/home/carl/Desktop/libusb-1.0.9# make install
Making install in libusb
make[1]: Entering directory '/home/carl/Desktop/libusb-1.0.9/libusb'
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9/libusb'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libusb-1.0.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libusb-1.0.so.0.1.0 /usr/local/lib/libusb-1.0.so.0.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libusb-1.0.so.0.1.0 libusb-1.0.so.0 || { rm -f libusb-1.0.so.0 && ln -s libusb-1.0.so.0.1.0 libusb-1.0.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libusb-1.0.so.0.1.0 libusb-1.0.so || { rm -f libusb-1.0.so && ln -s libusb-1.0.so.0.1.0 libusb-1.0.so; }; })
libtool: install: /usr/bin/install -c .libs/libusb-1.0.lai /usr/local/lib/libusb-1.0.la
libtool: install: /usr/bin/install -c .libs/libusb-1.0.a /usr/local/lib/libusb-1.0.a
libtool: install: chmod 644 /usr/local/lib/libusb-1.0.a
libtool: install: ranlib /usr/local/lib/libusb-1.0.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include/libusb-1.0" || /bin/mkdir -p "/usr/local/include/libusb-1.0"
 /usr/bin/install -c -m 644 libusb.h '/usr/local/include/libusb-1.0'
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/libusb'
make[1]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/libusb'
Making install in doc
make[1]: Entering directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[2]: Nothing to be done for 'install-exec-am'.
make[2]: Nothing to be done for 'install-data-am'.
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[1]: Leaving directory '/home/carl/Desktop/libusb-1.0.9/doc'
make[1]: Entering directory '/home/carl/Desktop/libusb-1.0.9'
make[2]: Entering directory '/home/carl/Desktop/libusb-1.0.9'
make[2]: Nothing to be done for 'install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 libusb-1.0.pc '/usr/local/lib/pkgconfig'
make[2]: Leaving directory '/home/carl/Desktop/libusb-1.0.9'
make[1]: Leaving directory '/home/carl/Desktop/libusb-1.0.9'
root@Ubuntu-PC:/home/carl/Desktop/libusb-1.0.9#

---

