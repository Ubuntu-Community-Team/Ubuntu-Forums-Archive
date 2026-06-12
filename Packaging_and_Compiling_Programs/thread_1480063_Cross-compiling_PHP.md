---
title: "Cross-compiling PHP"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by kentb12 on 2010-05-11
Hi

I'm a bit of a newbie with this stuff, so I'm not 100% sure where to post this.

Anyway I have a mini arm based PC for which I am trying to compile a php binary in cgi-mode, which supports sqlite.

I am trying to cross compile from a Ubuntu PC.

My code is as follows (from the unzipped PHP directory):

$ export CC=/usr/local/arm/3.4.1/bin/arm-linux-gcc 
$ export CXX=/usr/local/arm/3.4.1/bin/arm-linux-cpp
$ ./configure --host=i386-linux-gnu --prefix=/usr/home/ben/Desktop/php_bin --enable-ftp --target=arm --without-pear --disable-simplexml --disable-mbregex --enable-sockets --enable-pdo --with-pdo-sqlite --with-sqlite3 --disable-all
$ make
$ make install

It runs through the ./configure fine until the make command, where it falls over with the following error:

.....Zend/zend_objects_API.lo Zend/zend_default_classes.lo Zend/zend_execute.lo sapi/cgi/cgi_main.lo sapi/cgi/fastcgi.lo 
main/internal_functions.lo -lcrypt -lcrypt -lrt -lm -lcrypt -lcrypt  -o sapi/cgi/php-cgi 
ext/date/lib/parse_date.o: could not read symbols: 
Input/output error collect2: ld returned 1 exit status
make: *** [sapi/cgi/php-cgi] Error 1

I went into to php-5.3.2/ext/date/lib and sure enough the parse_date.o file hangs the OS when I try and open it.

I re-downloaded the php 5.3.2 tarball, (thinking it could be a corrupt download) and php-5.3.2/ext/date/lib/parse_date.o doesn't exist, and I get the same error anyway when I try and re-compile.

I've been researching online a bit and .o files are made during installations....

If anyone can see what I'm doing wrong (and point me in the right direction) I'd be eternally grateful!

---

