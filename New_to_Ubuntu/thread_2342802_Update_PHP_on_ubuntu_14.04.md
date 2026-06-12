---
title: "Update PHP on ubuntu 14.04"
date: 2016-11-10
forum: New to Ubuntu
---

### Post by jecdk on 2016-11-10
Hi

Im brand new til ubuntu, but want to upgrade php 5.5.9 to 5.6.27.

I've installed 5.6.27:
root@gna:~# php -v
PHP 5.6.27-1+deb.sury.org~trusty+1 (cli)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2016, by Zend Technologies

But PHP info in Moodle still shows:
PHP Version 5.5.9-1ubuntu4.20

Looking for the php.ini I get:
root@gna:~# locate php.ini
/etc/php/5.6/apache2/php.ini
/etc/php/5.6/cli/php.ini
/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini
/usr/lib/php/5.6/php.ini-development
/usr/lib/php/5.6/php.ini-production
/usr/lib/php/5.6/php.ini-production.cli
/usr/share/php5/php.ini-development
/usr/share/php5/php.ini-production
/usr/share/php5/php.ini-production.cli

---

### Post by SeijiSensei on 2016-11-10
Lets start with the basics.  Did you restart apache?

Also what version of Ubuntu are you using, and how did you install 5.6.27?  The [current version of PHP5 for 14.04]("https://launchpad.net/ubuntu/+source/php5") is 5.5.9.  On 16.04 the default is PHP7.

---

