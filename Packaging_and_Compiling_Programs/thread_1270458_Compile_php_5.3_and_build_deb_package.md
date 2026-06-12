---
title: "Compile php 5.3 and build deb package"
date: 2009-09-19
forum: Packaging and Compiling Programs
---

### Post by Jordanwb on 2009-09-19
What I want to do is compile PHP 5.3 and make it a deb package. I have these two pages:

[Compile PHP]("http://www.phpcult.com/blog/2009/08/building-php-5-3-packages-on-ubuntu-9-04-jaunty-for-apache-2/") and [Build deb]("http://ubuntuforums.org/showthread.php?t=857404"), but I don't know how to combine the two. Is this correct?
```

#apt-get install mysql-client mysql-client-5.0  mysql-common mysql-server mysql-server-5.0 mysql-server-core-5.0 libtidy-dev curl libcurl4-openssl-dev libcurl3 libcurl3-gnutls zlib1g zlib1g-dev libxslt1-dev libzip-dev libzip1 libxml2 libsnmp-base libsnmp15 libxml2-dev libsnmp-dev libjpeg62 libjpeg62-dev libpng12-0 libpng12-dev zlib1g zlib1g-dev libfreetype6 libfreetype6-dev libbz2-dev libxpm-dev libmcrypt-dev libmcrypt4 devscripts build-essential fakeroot
#mkdir ~/srcs
#cd ~/srcs
#wget http://us3.php.net/get/php-5.3.0.tar.gz/from/this/mirror
#tar xvfz php-5-3-0.tar.gz
#cd php-5.3.0
#apt-get build-dep php_5_3
#debuild -us -uc

```

---

### Post by Bachstelze on 2009-09-20
php5 is a very complicated package, since the source package is split into a lot of binary packages. I suggest you download the source package for php5 from the repos, and have a look at how it's done. Of course, you must already ve familiar with building simpler packages, or it will look like gibberish to you.

---

### Post by Jordanwb on 2009-09-20
I have used Gentoo for a while so I am familiar with configuring and compiling packages, as well as fixing unmet dependencies. I had found that XAMPP comes with PHP 5.3 by default, so I'll stick that on a virtual machine instead of messing and potentially bricking a working install.

---

