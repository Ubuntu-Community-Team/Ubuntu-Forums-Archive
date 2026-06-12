---
title: "PHP/MySQL trouble"
date: 2007-02-17
forum: Programming Talk
---

### Post by raevin on 2007-02-17
I compiled PHP5 on my own (aka: not using what's found in the repository, because I needed FastCGI), but used all the MySQL packages in the repository (libmysql15off & libmysql15-dev to be specific).

Here's the problem...whenever I try to connect to MySQL, I get this error: "Warning: mysql_connect() [function.mysql-connect]: Too many open links (0) [...]".  The line in failure is simply mysql_connect() (the arguments are correct).  mysql_connect does exist, because I checked with function_exists().  phpinfo() shows only this:

```

mysql
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.24a
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient

Directive	Local Value	Master Value

```

Also, on topic in a way, does anyone know about getting a fatal error in phpMyAdmin (always getting: "Fatal error: Call to undefined function PMA_getenv() in /var/www/pma/index.php on line 49" when I try to go to it).

---

### Post by Mirrorball on 2007-02-17
I'd check the values of all MySQL options in /usr/local/lib/php.ini

---

### Post by raevin on 2007-02-17
> **Mirrorball said:**
> I'd check the values of all MySQL options in /usr/local/lib/php.ini

I've done that...and, it's below incase you or anyone else wants to see it...

```

[MySQL]
; Allow or prevent persistent links.
mysql.allow_persistent = On

; Maximum number of persistent links.  -1 means no limit.
mysql.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
mysql.max_links = -1

; Default port number for mysql_connect().  If unset, mysql_connect() will use
; the $MYSQL_TCP_PORT or the mysql-tcp entry in /etc/services or the
; compile-time value defined MYSQL_PORT (in that order).  Win32 will only look
; at MYSQL_PORT.
mysql.default_port =

; Default socket name for local MySQL connects.  If empty, uses the built-in
; MySQL defaults.
mysql.default_socket =

; Default host for mysql_connect() (doesn't apply in safe mode).
mysql.default_host = localhost

; Default user for mysql_connect() (doesn't apply in safe mode).
mysql.default_user = 

; Default password for mysql_connect() (doesn't apply in safe mode).
; Note that this is generally a *bad* idea to store passwords in this file.
; *Any* user with PHP access can run 'echo get_cfg_var("mysql.default_password")
; and reveal this password!  And of course, any users with read access to this
; file will be able to reveal the password as well.
mysql.default_password = 

; Maximum time (in secondes) for connect timeout. -1 means no limit
mysql.connect_timeout = 60

; Trace mode. When trace_mode is active (=On), warnings for table/index scans and
; SQL-Errors will be displayed.
mysql.trace_mode = Off

```

I even enabled the extension (mysql.so), and it's not made a difference.

---

### Post by Mirrorball on 2007-02-17
I've done exactly what you did, compiled PHP on my own and installed Ubuntu's MySQL packages. Here is how I compiled PHP:
```
CFLAGS="-O2" ./configure --with-apxs2=/usr/bin/apxs2 --with-mysqli --enable-mbstring --with-gd --with-zlib --with-freetype-dir=/usr/include/freetype2 --with-png-dir=/usr/include/libpng12 --with-jpeg-dir=/usr/include --with-mysql
```
And my php.ini is exactly the php.ini-recommended file that came with the source code. I hope it helps.

---

### Post by raevin on 2007-02-17
> **Mirrorball said:**
> I've done exactly what you did, compiled PHP on my own and installed Ubuntu's MySQL packages. Here is how I compiled PHP:
```
CFLAGS="-O2" ./configure --with-apxs2=/usr/bin/apxs2 --with-mysqli --enable-mbstring --with-gd --with-zlib --with-freetype-dir=/usr/include/freetype2 --with-png-dir=/usr/include/libpng12 --with-jpeg-dir=/usr/include --with-mysql
```
And my php.ini is exactly the php.ini-recommended file that came with the source code. I hope it helps.

O.o

I dunno why this works but mine won't, but thank-flippin-God you've helped me...!

(Sorry...just been racking my mind for the past day now trying to get this to work, and things...)

One question...what does the "CFLAGS='-O2'" do?  I'm assuming it's a switch/flag for gcc for a 2nd level of something...but I'm not to sure.

---

### Post by Mirrorball on 2007-02-17
-O2 is an optimization flag for g++ to make php run faster.

---

