---
title: "phpbrew issue"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by numan2 on 2015-03-04
I'm installing apache2, mysql and php on ubuntu 14.04 and I need to run a certain version of PHP.  I currently have apache 2.4, mysql5.5 and need PHP 5.3, or 5.4.

I went to the php website and downloaded php-5.4.38.tar.gz and unzipped it and inside there I see a install-sh file but it's not installing.  

Anyone have any ideas?

Thanks!

---------------------

**New Issue**

I installed phpbrew from the home user and when I do php -v I see the correct php version but when I do over to root and do php -v it says 5.5.9.  Phpbrew appears to be install in both places...

---

### Post by snowpensi on 2015-03-04
hi numan2 I can help you!
To PHP is explain page 194 "Ubuntu Server Guide"

[https://help.ubuntu.com/14.04/serverguide/serverguide.pdf](https://help.ubuntu.com/14.04/serverguide/serverguide.pdf)

apt-get is helping yes? install-sh  only good for, how you say, man no groom: "hair grow on neck"! ;)

---

### Post by sandyd on 2015-03-04
> **numan2 said:**
> I'm installing apache2, mysql and php on ubuntu 14.04 and I need to run a certain version of PHP.  I currently have apache 2.4, mysql5.5 and need PHP 5.3, or 5.4.

I went to the php website and downloaded php-5.4.38.tar.gz and unzipped it and inside there I see a install-sh file but it's not installing.  

Anyone have any ideas?

Thanks!

See [phpbrew]("https://github.com/phpbrew/phpbrew")

---

### Post by numan2 on 2015-03-12
Thanks for the information...

I went ahead and installed phpbrew.  Through phpbrew I installed php 5.4.38 a couple days ago.  I just checked the version and it's indeed running 5.5.  This is weird because before it was php 5.4.  Previously I rebooted the box and it went back to the default php (5.5).  I'm not sure if this is normal behavior.  Then I just used the phpbrew command 'switch' and when I did php -v info for 5.4 was shown.  Now, it looks like 5.4.38 isn't even install under phpbrew list...  

max@xx:/$ phpbrew list
Please install at least one PHP with your prefered version.
max@xx:/$

max@xxx:/$ phpbrew info
Version
PHP-5.5.9-1ubuntu4.6


Constants
PHP Prefix: /usr
PHP Binary: /usr/bin/php5
PHP Default Include path: .:/usr/share/php:/usr/share/pear
PHP Include path: .:/usr/share/php:/usr/share/pear


General Info
phpinfo()
PHP Version => 5.5.9-1ubuntu4.6

---

### Post by numan2 on 2015-03-12
I reinstalled php 5.4... message below:
```

Congratulations! Now you have PHP with 5.4.38 as php-5.4.38
To use the newly built PHP, try the line(s) below:
    $ phpbrew use php-5.4.38

Or you can use switch command to switch your default php to php-5.4.38:
    $ phpbrew switch php-5.4.38

Enjoy!
ee@xx:~$ php -v
PHP 5.5.9-1ubuntu4.6 (cli) (built: Feb 13 2015 19:17:11)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend OPcache v7.0.3, Copyright (c) 1999-2014, by Zend Technologies


ee@xx:~$ php -vPHP 5.4.38 (cli) (built: Mar 12 2015 10:43:47)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2014 Zend Technologies

```
I'm installing sugarCRM and in there system check it's saying that I'm still using 5.5.9 for php.  

I'm going to change the installsystemcheck.php file.   I changed the file and I don't get the error anymore.

The problem that I have is that from root, when I do php -v is shows 5.5.9 and when I'm not in root it's 5.4.38.  Phpbrew appears to be installed in both places.

Do you know if there is anything thing else that I would need to change?

Thanks!

---

### Post by sandyd on 2015-03-12
Few things

To install php with apache2 -> [https://github.com/phpbrew/phpbrew/wiki/Cookbook#apache2-support](https://github.com/phpbrew/phpbrew/wiki/Cookbook#apache2-support)

To get the versions to match up, use
[https://github.com/phpbrew/phpbrew/wiki/Cookbook#install-phpbrew-into-system-wide-environment](https://github.com/phpbrew/phpbrew/wiki/Cookbook#install-phpbrew-into-system-wide-environment) for systemwide installation.

---

### Post by numan2 on 2015-03-13
I appreciate the help sandyd!

So, I checked my phpinfo from x.x.x.x/phpinfo.php and it showed the php version as 5.5.9.

I did phpbrew install 5.4.38 +apxs2 and restart apache2 and the version is now 5.4.38.  I had a call with a support engineer from sugarcrm and he wasn't that helpful and I'm getting sugarcrm specific errors now will have to create a support ticket.  I wasn't getting these errors before.  

I'm going to spin up a new ubuntu LAMP vm and will do it over again and have support work on the issues.... sucks

Since I'm going to do the phpbrew install again... I'm going to be in root and where should install phpbrew?  Currently it's installed in the root directory.  Is that fine?

Thanks!

---

### Post by sandyd on 2015-03-15
> **numan2 said:**
> I appreciate the help sandyd!

So, I checked my phpinfo from x.x.x.x/phpinfo.php and it showed the php version as 5.5.9.

I did phpbrew install 5.4.38 +apxs2 and restart apache2 and the version is now 5.4.38.  I had a call with a support engineer from sugarcrm and he wasn't that helpful and I'm getting sugarcrm specific errors now will have to create a support ticket.  I wasn't getting these errors before.  

I'm going to spin up a new ubuntu LAMP vm and will do it over again and have support work on the issues.... sucks

Since I'm going to do the phpbrew install again... I'm going to be in root and where should install phpbrew?  Currently it's installed in the root directory.  Is that fine?

Thanks!

Probably should be installing it into /opt/phpbrew, which the link above about installing systemwide talks about

---

