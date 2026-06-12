---
title: "PHP/Call to undefined function mcrypt_module_open()"
date: 2008-02-15
forum: Programming Talk
---

### Post by BongoLand on 2008-02-15
Hello All,

I just installed a fresh copy of Ubuntu Server 7.10 as a LAMP. But whenever I try to run my PHP code I get the following error: -

Fatal error: Call to undefined function mcrypt_module_open() in /home/ndd/pass1.php on line 5

When I run <? phpinfo(); ?> it shows that "mcrypt" is enabled but its failing to run any of mcrypt functions. 

I have following PHP packages installed: -

ndd@hyperion:/home/ndd# dpkg --get-selections | grep php
libapache2-mod-php5				install
php-pear					install
php5						install
php5-cli					install
php5-common					install
php5-curl					install
php5-dev					install
php5-mcrypt					install
php5-mhash					install
php5-mysql					install
phpmyadmin					install
ndd@hyperion:/home/ndd# 

Can anyone please help me how to solve this problem... 

Cheers,
/N

---

### Post by stryder73 on 2008-02-16
Since I'm new to the site in order to learn myself, personally, I won't be much help.  I did do a search on your issue and from what I can see, it's a server-side issue.

[url=https://support.cubecart.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=51&nav=0,2]> This error message will show if your server doesn't support "mhash". It is a PHP function which is used to securely encrypt sensitive data such as credit card used by the manual credit card capture module. 

The only solution to this is to contact your hosting company or server administrator to ask them if they can enable mhash with the PHP compilation.
[/url]

The only other source I found that may be somewhat insightful is [here.](http://lists.debian.org/debian-isp/2004/10/msg00199.html)

---

### Post by BongoLand on 2008-02-16
Genius Dude... 

You solved ma problem within minute... You should be proud man... 

Found out that "mcrypt.so" was loaded only in apache (/etc/php5/apache2/php.ini) and not in CLI (/etc/php5/cli/php.ini). So just had to add extension=mcrypt.so with the module directory extension_dir="/usr/lib/php5/20060613+lfs/mcrypt.so". 

Once again thanks for the reply...

Cheers,
/N

---

