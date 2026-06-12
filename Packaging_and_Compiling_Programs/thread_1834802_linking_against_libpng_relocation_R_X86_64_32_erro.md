---
title: "linking against libpng: relocation R_X86_64_32 error"
date: 2011-08-28
forum: Packaging and Compiling Programs
---

### Post by Cyrille37 on 2011-08-28
Hi,

I try to make PHP 5.3.x with the use of libpng installed on the system (./configure ... --with-png-dir ...).

But at make time it failed with:
```
/usr/bin/ld: skipping incompatible /usr/lib/libpng.so when searching for -lpng
/usr/bin/ld: /usr/lib/libpng.a(libpng12_la-png.o): **relocation R_X86_64_32** against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libpng.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libphp5.la] Erreur 1
```I'm using XUbuntu 11.04 and all stuff come from the package manager expect the php source code that I would like to compile, so the libpng package is: **libpng12-dev** (1.2.44-1ubuntu3.1)

What's wrong with this libpng package ?

Thanks
Cyrille.

---

### Post by Bachstelze on 2011-08-28
Couldn't reproduce. Please give your exact configure line.

---

### Post by Cyrille37 on 2011-08-29
Hello and Thanks,

Here it is my Php 5.3.8 configure and build command :

./configure \
    --prefix=${InstallPath}/php5 \
    --with-apxs2=${InstallPath}/apache/bin/apxs \
    --with-openssl \
    --with-mcrypt \
    --with-mysql=mysqlnd \
    --with-mysqli=mysqlnd \
    --enable-sqlite-utf8 \
    --with-libxml-dir \
    --with-xsl \
    --enable-soap \
    --enable-mbstring \
    --enable-intl \
    --with-jpeg-dir \
    --with-png-dir \
    --with-gd \
    --enable-gd-native-ttf \
    --with-zlib \
    --enable-zip \
&& make && make install

For all dependencies I've installed each library's development version with the Synaptic package manager (main, universe, restricted, multiverse).

Cheers
Cyrille

---

