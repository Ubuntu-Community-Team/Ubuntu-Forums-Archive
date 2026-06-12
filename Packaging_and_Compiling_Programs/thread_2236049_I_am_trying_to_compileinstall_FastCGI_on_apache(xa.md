---
title: "I am trying to compile/install FastCGI on apache(xampp)"
date: 2014-07-24
forum: Packaging and Compiling Programs
---

### Post by radibg2 on 2014-07-24
I downloaded it from here - [http://apache.igor.onlinedirect.bg//httpd/mod_fcgid/mod_fcgid-2.3.9.tar.gz(that](http://apache.igor.onlinedirect.bg//httpd/mod_fcgid/mod_fcgid-2.3.9.tar.gz(that) link is from apache.org website), then i unpacked, first i wrote sudo su, then ./configure it didn't found apxs i wrote **locate apxs** then it show me:
```
/home/radibg2/Downloads/mod_fcgid-2.3.9/Makefile.apxs
/home/radibg2/Downloads/mod_fcgid-2.3.9/configure.apxs
/home/radibg2/Downloads/mod_fcgid-2.3.9/build/Makefile.apxs
/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid/Makefile.apxs
/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid/modules.mk.apxs
/opt/lampp/bin/apxs
/opt/lampp/man/man1/apxs.1
/opt/lampp/manual/programs/apxs.html
/opt/lampp/manual/programs/apxs.html.en
/opt/lampp/manual/programs/apxs.html.fr
/opt/lampp/manual/programs/apxs.html.ko.euc-kr
/opt/lampp/manual/programs/apxs.html.tr.utf8

```After that i wrote **APXS=/opt/lampp/bin/apxs ./configure.apxs **it returned:
```
Configuring mod_fcgid for APXS in /opt/lampp/bin/apxs
Detecting features


Finished, run 'make' to compile mod_fcgid


Run 'make install' to install mod_fcgid
```
I wrote make and it returned:
```
Making all in modules/fcgid
make[1]: Entering directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
/opt/lampp/build/libtool --silent --mode=compile gcc -std=gnu99  -pthread  -I/opt/lampp/include/c-client -I/opt/lampp/include/libpng -I/opt/lampp/include/freetype2 -O3 -fPIC -L/opt/lampp/lib -I/opt/lampp/include -I/opt/lampp/include/ncurses -DFCGID_APXS_BUILD   -D_REENTRANT -D_GNU_SOURCE  -I/opt/lampp/include/c-client -I/opt/lampp/include/libpng -I/opt/lampp/include/freetype2 -O3 -fPIC -L/opt/lampp/lib -I/opt/lampp/include -I/opt/lampp/include/ncurses  -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid -I/home/radibg2/Downloads/mod_fcgid-2.3.9/include -I/opt/lampp/include -I. -I/opt/lampp/include/apr-1 -I/opt/lampp/include -prefer-pic -c mod_fcgid.c && touch mod_fcgid.slo
/opt/lampp/build/libtool: 1555: /opt/lampp/build/libtool: preserve_args+= --silent: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= gcc: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -std=gnu99: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -pthread: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/c-client: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/libpng: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/freetype2: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -O3: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -fPIC: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -L/opt/lampp/lib: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/ncurses: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -DFCGID_APXS_BUILD: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -D_REENTRANT: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -D_GNU_SOURCE: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/c-client: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/libpng: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/freetype2: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -O3: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -fPIC: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -L/opt/lampp/lib: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/ncurses: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I.: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/apr-1: not found
/opt/lampp/build/libtool: 2419: /opt/lampp/build/libtool: later+= -prefer-pic: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -c: not found
libtool: compile: you must specify a compilation command
libtool: compile: Try `libtool --help --mode=compile' for more information.
make[1]: *** [mod_fcgid.slo] Error 1
make[1]: Leaving directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
make: *** [all-recursive] Error 1

```
I wrote make install and it returned:
```
Making install in modules/fcgid
make[1]: Entering directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
make[2]: Entering directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
/opt/lampp/build/libtool --silent --mode=compile gcc -std=gnu99  -pthread  -I/opt/lampp/include/c-client -I/opt/lampp/include/libpng -I/opt/lampp/include/freetype2 -O3 -fPIC -L/opt/lampp/lib -I/opt/lampp/include -I/opt/lampp/include/ncurses -DFCGID_APXS_BUILD   -D_REENTRANT -D_GNU_SOURCE  -I/opt/lampp/include/c-client -I/opt/lampp/include/libpng -I/opt/lampp/include/freetype2 -O3 -fPIC -L/opt/lampp/lib -I/opt/lampp/include -I/opt/lampp/include/ncurses  -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid -I/home/radibg2/Downloads/mod_fcgid-2.3.9/include -I/opt/lampp/include -I. -I/opt/lampp/include/apr-1 -I/opt/lampp/include -prefer-pic -c mod_fcgid.c && touch mod_fcgid.slo
/opt/lampp/build/libtool: 1555: /opt/lampp/build/libtool: preserve_args+= --silent: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= gcc: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -std=gnu99: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -pthread: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/c-client: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/libpng: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/freetype2: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -O3: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -fPIC: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -L/opt/lampp/lib: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/ncurses: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -DFCGID_APXS_BUILD: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -D_REENTRANT: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -D_GNU_SOURCE: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/c-client: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/libpng: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/freetype2: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -O3: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -fPIC: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -L/opt/lampp/lib: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/ncurses: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/home/radibg2/Downloads/mod_fcgid-2.3.9/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I.: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include/apr-1: not found
/opt/lampp/build/libtool: 2419: /opt/lampp/build/libtool: later+= -prefer-pic: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -I/opt/lampp/include: not found
/opt/lampp/build/libtool: 1: eval: base_compile+= -c: not found
libtool: compile: you must specify a compilation command
libtool: compile: Try `libtool --help --mode=compile' for more information.
make[2]: *** [mod_fcgid.slo] Error 1
make[2]: Leaving directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/radibg2/Downloads/mod_fcgid-2.3.9/modules/fcgid'
make: *** [install-recursive] Error 1

```
Can you tell me how to install it?

---

