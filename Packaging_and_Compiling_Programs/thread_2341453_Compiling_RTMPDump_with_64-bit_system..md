---
title: "Compiling RTMPDump with 64-bit system."
date: 2016-10-28
forum: Packaging and Compiling Programs
---

### Post by ron998 on 2016-10-28
Hi
With my 32-bit system it is was easy to compile RTMPDump from git.
```
$ git clone --depth 1 git://repo.or.cz/rtmpdump.git
$ cd rtmpdump
$ make SHARED= VERSION="v2.4"
$ sudo checkinstall --pkgname rtmpdump --pkgversion "2.4+git$(date +%Y%m%d)" --backup=no --fstrans=no --default; sudo ldconfig
```

But with my 64-bit system there is a problem.
When I run the last (checkinstall) command it gives errors...

```
make[1]: Entering directory '/home/user/rtmpdump/librtmp'
gcc -shared -Wl,-soname,librtmp.so.1  -o librtmp.so.1 rtmp.o log.o amf.o hashswf.o parseurl.o  -lssl -lcrypto -lz 
/usr/bin/ld: rtmp.o: relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
rtmp.o: error adding symbols: Bad value
collect2: error: ld returned 1 exit status
Makefile:92: recipe for target 'librtmp.so.1' failed
make[1]: *** [librtmp.so.1] Error 1
make[1]: Leaving directory '/home/user/rtmpdump/librtmp'
Makefile:76: recipe for target 'librtmp/librtmp.a' failed
make: *** [librtmp/librtmp.a] Error 2

****  Installation failed. Aborting package creation
```

Google results seem to indicate that "-fPIC" needs to be passed to the compiler.
This could be done during the ./configure stage, but there is no ./configure stage for RTMPDump.
Currently I'm using RTMPDump from the repo, but I'd like to compile it myself to add some KSV patches.

Any ideas how to build this package with 64-bit *buntu-16.04.

```
$ cat /etc/issue
Linux Mint 18 Sarah
```

---

### Post by ron998 on 2016-10-29
It compiles OK if I don't use "**SHARED=**" in the make command.

```
$ make VERSION="v2.4\ KSV-2015-12-14"
```

```
Installing with make install...

========================= Installation results ===========================
make[1]: Entering directory '/home/user/rtmpdump/librtmp'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/user/rtmpdump/librtmp'
mkdir -p /usr/local/bin /usr/local/sbin /usr/local/man/man1 /usr/local/man/man8
cp rtmpdump /usr/local/bin
cp rtmpgw rtmpsrv rtmpsuck /usr/local/sbin
cp rtmpdump.1 /usr/local/man/man1
cp rtmpgw.8 /usr/local/man/man8
make[1]: Entering directory '/home/user/rtmpdump/librtmp'
sed -e "s;@prefix@;/usr/local;" -e "s;@libdir@;/usr/local/lib;" \
    -e "s;@VERSION@;v2.4;" \
    -e "s;@CRYPTO_REQ@;libssl,libcrypto;" \
    -e "s;@PUBLIC_LIBS@;;" \
    -e "s;@PRIVATE_LIBS@;-lm;" librtmp.pc.in > librtmp.pc
mkdir -p /usr/local/include/librtmp /usr/local/lib/pkgconfig /usr/local/man/man3 /usr/local/lib
cp amf.h http.h log.h rtmp.h /usr/local/include/librtmp
cp librtmp.a /usr/local/lib
cp librtmp.pc /usr/local/lib/pkgconfig
cp librtmp.3 /usr/local/man/man3
cp librtmp.so.1 /usr/local/lib
cd /usr/local/lib; ln -sf librtmp.so.1 librtmp.so
make[1]: Leaving directory '/home/user/rtmpdump/librtmp'

======================== Installation successful ==========================
```

```
$ rtmpdump
RTMPDump v2.4 KSV-2015-12-14
```

---

