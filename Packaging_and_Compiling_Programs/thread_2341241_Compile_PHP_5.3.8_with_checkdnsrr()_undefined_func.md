---
title: "Compile PHP 5.3.8 with checkdnsrr() undefined function"
date: 2016-10-26
forum: Packaging and Compiling Programs
---

### Post by admtwins on 2016-10-26
In Ubuntu 14.04 Server I compiled php-5.3.8 from source code, because some sites on this hosting can't work with php 5.5 or greater. Here is configure parameters:
```
./configure --prefix=/opt/php-5.3.8 --with-pdo-mysql --with-zlib-dir --with-freetype-dir --enable-mbstring --with-libxml-dir=/usr --enable-soap --enable-calendar --with-curl --with-mcrypt --with-zlib --with-gd  --disable-rpath --enable-inline-optimization --with-bz2 --with-zlib --enable-sockets --enable-sysvsem --enable-sysvshm --enable-pcntl --enable-mbregex --with-mhash --enable-zip --with-pcre-regex --with-mysql  --with-mysqli --with-jpeg-dir=/usr --with-png-dir=/usr --enable-gd-native-ttf --with-openssl --with-fpm-user=www-data --with-fpm-group=www-data --with-libdir=/lib/x86_64-linux-gnu --enable-ftp  --with-kerberos --with-gettext --enable-fpm --with-imap-ssl --with-imap
```


All works fine, but when I try use checkdnsrr() function in error.log I can see:
```
2016/10/26 11:05:18 [error] 14824#0: *8696 FastCGI sent in stderr: "PHP Fatal error:  Call to undefined function checkdnsrr()
```


Bind server is installed, libbidn-dev and libbind9-90 are installed.


How can I compile php-5.3.8 with checkdnsrr() and other dns functions?

---

