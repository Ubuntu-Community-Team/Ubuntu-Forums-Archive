---
title: "error: C compiler cannot create executables"
date: 2013-02-22
forum: Packaging and Compiling Programs
---

### Post by nmajid2 on 2013-02-22
I'm trying to run ./configure and I get following message from config.log:

configure:2926: checking for a BSD-compatible install
configure:2994: result: /usr/bin/install -c
configure:3005: checking whether build environment is sane
configure:3055: result: yes
configure:3104: checking for mipsel-openwrt-linux-strip
configure:3131: result: mipsel-openwrt-linux-uclibc-strip
configure:3196: checking for a thread-safe mkdir -p
configure:3235: result: /bin/mkdir -p
configure:3248: checking for gawk
configure:3264: found /usr/bin/gawk
configure:3275: result: gawk
configure:3286: checking whether make sets $(MAKE)
configure:3308: result: yes
configure:3439: checking whether to enable maintainer-specific portions of Makefiles
configure:3448: result: no
configure:3470: checking for mipsel-openwrt-linux-gcc
configure:3497: result: mipsel-openwrt-linux-uclibc-gcc
configure:3766: checking for C compiler version
configure:3775: mipsel-openwrt-linux-uclibc-gcc --version >&5
mipsel-openwrt-linux-uclibc-gcc (GCC) 3.4.6 (OpenWrt-2.0)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3786: $? = 0
configure:3775: mipsel-openwrt-linux-uclibc-gcc -v >&5
Reading specs from /home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/bin/../lib/gcc/mipsel-openwrt-linux-uclibc/3.4.6/specs
Configured with: /home/jow/devel/openwrt/10.03.1/brcm-2.4/build_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/gcc-3.4.6/configure --prefix=/home/jow/devel/openwrt/10.03.1/brcm-2.4/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr --build=i386-redhat-linux --host=i386-redhat-linux --target=mipsel-openwrt-linux-uclibc --with-gnu-ld --enable-target-optspace --disable-libgomp --disable-libmudflap --disable-multilib --disable-nls --with-float=soft --disable-libssp --disable-__cxa_atexit --enable-languages=c,c++ --enable-shared --enable-threads --with-slibdir=/home/jow/devel/openwrt/10.03.1/brcm-2.4/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/lib --disable-tls
Thread model: posix
gcc version 3.4.6 (OpenWrt-2.0)
configure:3786: $? = 0
configure:3775: mipsel-openwrt-linux-uclibc-gcc -V >&5
mipsel-openwrt-linux-uclibc-gcc: `-V' option must have argument
configure:3786: $? = 1
configure:3775: mipsel-openwrt-linux-uclibc-gcc -qversion >&5
mipsel-openwrt-linux-uclibc-gcc: unrecognized option `-qversion'
mipsel-openwrt-linux-uclibc-gcc: no input files
configure:3786: $? = 1
configure:3806: checking whether the C compiler works
configure:3828: mipsel-openwrt-linux-uclibc-gcc -Os -pipe -mips32 -mtune=mips32 -funit-at-a-time -fhonour-copts -msoft-float -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libiconv-stub/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libintl-stub/include  -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libiconv-stub/include -I/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libintl-stub/include  -L/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib -L/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/lib -L/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/lib -L/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/lib -L/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libiconv-stub/lib -L/home/root86/OPENWRT_SDK_HOME/staging_dir/target-mipsel_uClibc-0.9.30.1/usr/lib/libintl-stub/lib  conftest.c  >&5
/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/bin/../lib/gcc/mipsel-openwrt-linux-uclibc/3.4.6/../../../../mipsel-openwrt-linux-uclibc/bin/ld: warning: ld-uClibc.so.0, needed by /home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/lib/libc.so, not found (try using -rpath or -rpath-link)
/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/lib/libc.so: undefined reference to `_dl_app_init_array'
/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/lib/libc.so: undefined reference to `_dl_loaded_modules'
/home/root86/OPENWRT_SDK_HOME/staging_dir/toolchain-mipsel_gcc-3.4.6_uClibc-0.9.30.1/usr/lib/libc.so: undefined reference to `_dl_app_fini_array'
collect2: ld returned 1 exit status
configure:3832: $? = 1
configure:3870: result: no
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "glib"
| #define PACKAGE_TARNAME "glib"
| #define PACKAGE_VERSION "2.26.1"
| #define PACKAGE_STRING "glib 2.26.1"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=glib"
| #define PACKAGE_URL ""
| #define GLIB_MAJOR_VERSION 2
| #define GLIB_MINOR_VERSION 26
| #define GLIB_MICRO_VERSION 1
| #define GLIB_INTERFACE_AGE 1
| #define GLIB_BINARY_AGE 2601
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3875: error: in `/home/root86/OPENWRT_SDK_HOME/build_dir/target-mipsel_uClibc-0.9.30.1/glib-2.26.1':
configure:3877: error: C compiler cannot create executables
See `config.log' for more details



I've installed  sudo apt-get install build-essential and sudo apt-get update but it didn't help.

---

### Post by melfnt on 2013-02-24
Try to reinstall glibc

---

### Post by schragge on 2013-03-02
@**melfnc**
glibc? AFAICS, the software is clearly labeled as using uClibc.

@**nmajid2**
Did you install all the prerequisites as [explained on the OpenWrt Wiki](http://wiki.openwrt.org/doc/howto/buildroot.exigence#examples.of.package.installations)?

---

