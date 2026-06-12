---
title: "Xdebug is loaded but not showing up in phpinfo()"
date: 2012-02-05
forum: Programming Talk
---

### Post by goldingroup on 2012-02-05
Hello,

This is my first post. I have googled this matter several times before writing here. 

I have a server with Ubuntu 4.5, Lighttpd and PHP Version 5.3.2. I have installed Xdebug and I can verify that it has been installed correctly by doing this in terminal

php-cgi -i 
php-cgi -m
php -i
php-cgi m

Xdebug is listed both as PHP modules and Zend modules

Yet, it does not work in debugging and I can't see Xdebug in the phpinfo() script I have made. This is very strange as the php-cgi -i and php -i shows another phpinfo() WITH xdebug showing. 

Any solutions out there? It would be much appreciated!

Regards
Mikael

---

