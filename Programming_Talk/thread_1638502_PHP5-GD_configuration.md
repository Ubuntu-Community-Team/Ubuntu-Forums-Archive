---
title: "PHP5-GD configuration"
date: 2010-12-05
forum: Programming Talk
---

### Post by BillGrates on 2010-12-05
Please help with PHP5 configuration problems on Ubuntu10.10, I am totally confused.
What I am trying to do is to get php5-gd working and mysql

Running 'phpinfo' for PHP Version 5.1.6 lists:-

a) Configuration File (php.ini) Path 	/etc/php.ini

This file is actually located in /etc/php5/apache2/

Should I copy php.ini into /etc/ ?

b) Scan this dir for additional .ini files 	/etc/php.d 

These additional ini files are actually located in /etc/php5/apache2/conf.d/.

Directory /conf.d contains gd.ini, mysql.ini, imagick.ini, mycrypt.ini, mysqli.ini, pdo.ini and pdo_mysql.ini.

Should I copy /etc/php5/apache2/conf.d and it's contents  into /etc/ ?

c) From 'phpinfo' at the end of 'Configure Command' provides:-

' '--without-mysql' '--without-gd' '--without-odbc' '--disable-dom' '--disable-dba' '--without-unixODBC' '--disable-pdo' '--disable-xmlreader' '--disable-xmlwriter' 

I can not get GD scripts to run, searching for a solution provides :-
 
Look to see if GD is installed
GD Support enabled
GD version 2 or above (Synaptic packet manager installed is 5.3.3.1ubuntu9(maverick)
If you think GD is installed but php does not see it find and edit php.ini
if you see ;extension=php_gd.dll
remove ; to make it
extension=php_gd.dll

The /etc/php5/apache2/php.ini file does not contain either ;extension=php_gd.dll or extension=php_gd.dll

ANY suggestions would be most gratefully received.

Bill

---

### Post by roccivic on 2010-12-06
In my Maverick box I just executed:

```
sudo apt-get install php5 apache2 php5-gd
sudo /etc/init.d/apache2 restart
```

and GD is working fine.

---

### Post by BillGrates on 2010-12-06
Roccivic ..thank you..thank you..thank you.
I am deeply indebted to you.

Would it be possible for you to run <?phpinfo()?> and tell me what version the title line gives please?. 

I downloaded from Synaptic the pre-compiled PHP5 with GD making the file
PHP5-GD
The version of PHP5-GD in Synaptic is 5.3.3.1.
Yet when I run 'phpinfo' the Title line says PHP Version 5.1.6

I certainly owe you Guinness or two or...

Thanking you

Bill

---

### Post by roccivic on 2010-12-06
Here's what I get from phpinfo():

```
PHP Version 5.3.3-1ubuntu9.1

System 	Linux roccivic-pc 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64
Build Date 	Oct 15 2010 13:59:55
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
Additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/pdo.ini
PHP API 	20090626
PHP Extension 	20090626
Zend Extension 	220090626
Zend Extension Build 	API220090626,NTS
PHP Extension Build 	API20090626,NTS
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
Zend Multibyte Support 	disabled
IPv6 Support 	enabled
Registered PHP Streams 	https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk 
```

---

### Post by BillGrates on 2010-12-09
Please be aware my ISP had disabled GD in the PHP code and say they have no intention of enabling.
I am changing hosting services as a result.
Roccivic thank you for pointing me in the right direction, I am depply indebted to you Sir.
Thank you warmly,

Bill

---

