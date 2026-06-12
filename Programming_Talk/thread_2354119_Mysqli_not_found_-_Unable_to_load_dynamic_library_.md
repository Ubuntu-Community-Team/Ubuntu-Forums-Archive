---
title: "Mysqli not found - Unable to load dynamic library mysqli.so"
date: 2017-02-28
forum: Programming Talk
---

### Post by slushbrain on 2017-02-28
Hello,

I tried all ways but always the same result Mysqli not found.
I just installed Xubuntu 16.04, but also with the distro 15.10 not working.

Mysqli is working:
```
php -m | grep -i mysqli
mysqli
```

php 7 is working:
```
a2query -m | grep php
php7.0 (enabled by maintainer script)
```

phpinfo():
```
API Extensions     mysqli,pdo_mysql 
```

I added these lines in php.ini:
```
extension=msqli.so
extension=pdo_mysql.so
```

I tried ```
sudo apt-get install php-mysql
``` 
but ```
php-mysql is already the newest version (1:7.0+35ubuntu6).
```

I always rebooted the server ```
sudo service apache2 restart
```


The problem could be on the directory of PHP extensions, because the log files says ```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/.../mysqli.so' - /usr/lib/php/.../mysqli.so
``` 

The extensions directory is 
```
php -i | grep extension_dir
extension_dir => /usr/lib/php/20151012 => /usr/lib/php/20151012
``` 
so I tried to add in php.ini ```
extension_dir = "/usr/lib/php/20151012"
``` or ```
extension=/usr/lib/php/20151012/msqli.so
extension=/usr/lib/php/20151012/pdo_mysql.so
``` 
but nothing changed.

The php.ini file I edited is ```
/etc/php/7.0/apache2/php.ini
```

Still not working, I do not know what else to do..

---

### Post by slushbrain on 2017-02-28
Resolved, it was not a problem of Ubuntu but the code that I was doing, where there was a mysqli function written incorrectly. The error MySQLi not found made me think that the problem was in the files system, however the error was in the code I was writing.

---

