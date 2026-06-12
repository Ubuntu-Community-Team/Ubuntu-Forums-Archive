---
title: "Compiling PHP - MySQL Header Issue"
date: 2011-08-14
forum: Packaging and Compiling Programs
---

### Post by isthisyournacho on 2011-08-14
I am trying to get PHP 5.3 and 5.2 to run concurrently.  Here is my configure line:

./configure --prefix=/opt/php5.2 --with-config-file-path=/opt/php5.2 --with-mysqli --with-mysql=/usr/local/mysql --with-curl --with-gd --with-jpeg --with-jpeg-dir --enable-cli --enable-fastcgi --enable-discard-path --enable-force-cgi-redirect

And I am getting the error:

configure: error: Cannot find MySQL header files under /usr/local/mysql.
Note that the MySQL client library is not bundled anymore!

I have attempted to install the MySQL Client Development Libraries, but to no avail:

root@L3map02:/home/doug/php-5.2.17# apt-get install libmysqlclient-dev=5.1.41-3ubuntu12.10

The following packages have unmet dependencies:
  libmysqlclient-dev: Depends: libmysqlclient16 (= 5.1.41-3ubuntu12.10) but 5.1.57-1~dotdeb.1 is to be installed
E: Broken packages

root@L3map02:/home/doug/php-5.2.17# apt-get install libmysqlclient15-dev
The following packages have unmet dependencies:
  libmysqlclient-dev: Depends: libmysqlclient16 (= 5.1.41-3ubuntu12.10) but 5.1.57-1~dotdeb.1 is to be installed
E: Broken packages

root@L3map02:/home/doug/php-5.2.17# apt-get install libmysqlclient-dev
The following packages have unmet dependencies:
  libmysqlclient-dev: Depends: libmysqlclient16 (= 5.1.41-3ubuntu12.10) but 5.1.57-1~dotdeb.1 is to be installed
E: Broken packages

I'm going from Ubuntu 9.10 to 10.4 LTS, MySQL Ver 8.42 Distrib 5.1.51

---

### Post by isthisyournacho on 2011-08-14
I resolved this by using aptitude:

aptitude install libmysqlclient-dev

This downgraded the dependencies so that all dependencies were met.  Unfortunately I moved on further with my upgrade and didn't copy the output.

---

