---
title: "Need help compiling PHP5 widh --enable-debug"
date: 2011-02-18
forum: Packaging and Compiling Programs
---

### Post by r.osmanov on 2011-02-18
Hi there! 

I'm compiling PHP5 from source in order to enable debugging of Zend extensions.
Cannot find what I'm doing wrong.

That's what I do:
```
$ mkdir ~/src/php-build && cd ~/src/php-build 
$ apt-fast source php5
$ sudo apt-get build-dep php5
$ ls -lh
drwxr-xr-x 26 ruslan ruslan 4.0K 2011-02-18 21:14 php5-5.3.3
-rw-r--r--  1 ruslan ruslan 193K 2011-02-18 20:56 php5_5.3.3-1ubuntu9.3.diff.gz
-rw-r--r--  1 ruslan ruslan 2.4K 2011-02-18 20:56 php5_5.3.3-1ubuntu9.3.dsc
-rw-r--r--  1 ruslan ruslan  14M 2010-08-05 22:05 php5_5.3.3.orig.tar.gz
$ cd php5-5.3.3/

$ vim debian/rules
```
1) replace --disable-debug with --enable-debug
2) add the following the the end of COMMON_CONFIG:
```
--enable-maintainer-zts \
--disable-inline-optimization
```
(the last option terminated by "\")
```

$ dpkg-buildpackage -rfakeroot
...
make[2]: Leaving directory `/home/ruslan/src/php-build/php5-5.3.3/cgi-build'
make[1]: Leaving directory `/home/ruslan/src/php-build/php5-5.3.3/cgi-build'
sed -i -e 's/-d output_buffering=1 -d open_basedir="" -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /home/ruslan/src/php-build/php5-5.3.3/pear-build/usr/bin/pear && \
    sed -i -e 's/-d output_buffering=1 -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /home/ruslan/src/php-build/php5-5.3.3/pear-build/usr/bin/pecl && \
    sed -i -e 's/-d memory_limit="-1"//' \
           -e 's/-d output_buffering=1 -d open_basedir="" -d safe_mode=0/-d output_buffering=1 -d open_basedir="" -d safe_mode=0 -d memory_limit="-1"/' \
           /home/ruslan/src/php-build/php5-5.3.3/pear-build/usr/bin/peardev
sed -i -re "s#('PEAR_CONFIG_SYSCONFDIR', PHP_SYSCONFDIR)#\1 . '/pear'#" /home/ruslan/src/php-build/php5-5.3.3/pear-build/usr/share/php/PEAR/Config.php
touch build-pear-stamp
mkdir -p temp_session_store
# start our own mysql server for the tests
/bin/sh debian/setup-mysql.sh 1025 /home/ruslan/src/php-build/php5-5.3.3/mysql_db
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
make: *** [test-results.txt] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

It should have tried to start MySQL daemon on spare port, but lacks priveleges... I doubt if it somehow interfers another running mysqld process:
```
$ ps aux | grep mysqld 
ruslan    2223  0.0  0.2 151092 20872 pts/5    Sl   21:14   0:00 /home/ruslan/src/php-build/php5-5.3.3/mysql_base/bin/mysqld --no-defaults --bind-address=localhost --port=1025 --socket=/home/ruslan/src/php-build/php5-5.3.3/mysql_db/mysql.sock --datadir=/home/ruslan/src/php-build/php5-5.3.3/mysql_db
root      3304  0.0  0.0   4148   632 ?        S    17:32   0:00 /bin/sh /usr/local/mysql/bin/mysqld_safe --datadir=/var/lib/mysql --pid-file=/var/lib/mysql/megahost.pid
mysql     3415  0.1  0.1 121480 11504 ?        Sl   17:32   0:27 /usr/local/mysql/libexec/mysqld --basedir=/usr/local/mysql --datadir=/var/lib/mysql --user=mysql --log-error=/var/lib/mysql/megahost.err --pid-file=/var/lib/mysql/megahost.pid --socket=/tmp/mysqld.sock --port=3306
ruslan    5048  0.0  0.0  10108   852 pts/5    S+   21:46   0:00 grep --color=auto mysqld
```

Regards.

---

### Post by r.osmanov on 2011-02-18
Then I run 
```
$ dpkg-buildpackage -rfakeroot
... 
Restoring acinclude.m4

Removing patch 001-libtool_fixes.patch
Restoring TSRM/configure.in
Restoring configure.in

Patch ubuntu/ubuntu-php-version.patch does not remove cleanly (refresh it or enforce with -f)
make: *** [unpatch] Error 1
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
```

---

### Post by r.osmanov on 2011-02-18
Or it's better to just install *php5-dbg* package?

---

