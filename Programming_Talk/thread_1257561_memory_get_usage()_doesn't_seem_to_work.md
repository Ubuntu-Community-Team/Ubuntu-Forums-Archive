---
title: "memory_get_usage() doesn't seem to work"
date: 2009-09-03
forum: Programming Talk
---

### Post by torio on 2009-09-03
Hi!
I have real problem getting memory_get_usage() to work (correctly). I am running the  the Jaunty Jackalope, and have apache + php 5.2.6 server with GD module available. When I am using memory_get_usage() - I get very small number (like 65KB), while expected number is much higher (I am loading 6Mb image using gdcreatefromgif - and on my other box - slackware - output is around 19Mb - I've used exactly the same script). 
If I use memory_get_usage(true) I have a constant 256Kb as output. So, although memory_get_usage() seems to work (--enable-memory-limit is not required during compiling as of PHP 5.2+, so I think it is all set), results are not correct - they just stay the same even if I am creating gd images in a loop, and have memory_get_usage() | memory_get_usage(true) calls in each iteration. Numbers stay the same!

I have spent about 2 hours reviewing and googling the problem, to no avail. So, here is my question: did any of you guys experienced sth like that, are there any additional packages to be installed to get it to work? May php-cli conflict with php apache module? I am just lost..

I have following LAMP packages installed (in case you know of some probable conflict):
apache2
apache2.2-common
apache2-prefork-dev
apache2-mpm-prefork
apache2-utils
libapache2-mod-php5
libapache2-svn
libapache2-mod-auth-mysql
php5
php5-common
php5-cli
php5-dev
php5-gd
php5-xdebug
phpunit


Btw, I tried to get memory traces with xdebug - it shows exactly same values. It seems like memory management is taking place somewhere else..

Thanks in advace!

---

### Post by torio on 2009-09-12
Well, I actually found the solution - [here]("http://www.phpmag.ru/2009/09/12/ubuntu-9-04-php-5-gd-2/") is an explanation.
Thanks to all who replied :)

---

