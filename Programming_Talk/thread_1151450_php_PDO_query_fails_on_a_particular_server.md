---
title: "php PDO query fails on a particular server"
date: 2009-05-06
forum: Programming Talk
---

### Post by orlox on 2009-05-06
Hi, Im using php PDO to access a mysql database. However, a server I use simply fails to proccess a query. My test script is this:

[PHP]
<?php
echo "hi!";
$connection = new PDO("mysql:host=localhost;dbname=test", "user", "pass");
$res=$connection->query("Show databases;");
echo "bye!";
[/PHP]

On my apache server on my computer, this works correctly, and show both messages. However, on the server Im trying to use to put my webpage, the script fails, it outputs nothing, and firefox asks me to download the php file which has 0 kb...Commenting on the query line gives me both messages though...

Is it just the server thats messed up?? Or perhaps some strange php variable needs to be changed???

---

### Post by orlox on 2009-05-06
Damm! just made a phpinfo() and the configure used to compile php says:

```
'./configure' '--build=x86_64-redhat-linux-gnu' '--host=x86_64-redhat-linux-gnu' '--target=x86_64-redhat-linux-gnu' '--program-prefix=' '--prefix=/usr' '--exec-prefix=/usr' '--bindir=/usr/bin' '--sbindir=/usr/sbin' '--sysconfdir=/etc' '--datadir=/usr/share' '--includedir=/usr/include' '--libdir=/usr/lib64' '--libexecdir=/usr/libexec' '--localstatedir=/var' '--sharedstatedir=/usr/com' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--cache-file=../config.cache' '--with-libdir=lib64' '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' '--disable-debug' '--with-pic' '--disable-rpath' '--without-pear' '--with-bz2' '--with-curl' '--with-exec-dir=/usr/bin' '--with-freetype-dir=/usr' '--with-png-dir=/usr' '--enable-gd-native-ttf' '--without-gdbm' '--with-gettext' '--with-gmp' '--with-iconv' '--with-jpeg-dir=/usr' '--with-openssl' '--with-png' '--with-pspell' '--with-expat-dir=/usr' '--with-pcre-regex=/usr' '--with-zlib' '--with-layout=GNU' '--enable-exif' '--enable-ftp' '--enable-magic-quotes' '--enable-sockets' '--enable-sysvsem' '--enable-sysvshm' '--enable-sysvmsg' '--enable-track-vars' '--enable-trans-sid' '--enable-yp' '--enable-wddx' '--with-kerberos' '--enable-ucd-snmp-hack' '--with-unixODBC=shared,/usr' '--enable-memory-limit' '--enable-shmop' '--enable-calendar' '--enable-dbx' '--enable-dio' '--with-mime-magic=/etc/httpd/conf/magic' '--without-sqlite' '--with-libxml-dir=/usr' '--with-xml' '--with-apxs2=/usr/sbin/apxs' '--without-mysql' '--without-gd' '--without-odbc' '--disable-dom' '--disable-dba' '--without-unixODBC' '--disable-pdo' '--disable-xmlreader' '--disable-xmlwriter'
```

It has the option '--disable-pdo'!!

However, afterwards it says pdo.ini is parsed, and it shows that it has mysql and sqlite drivers enabled...

However, the PDO object is recognized (i can create a new connection) and it fails at a query only...

---

