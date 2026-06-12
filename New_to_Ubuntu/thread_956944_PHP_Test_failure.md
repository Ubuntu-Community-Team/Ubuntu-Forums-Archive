---
title: "PHP Test failure"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-23
I installed the server edition 8.04 as a LAMP.  I have managed to get my web development pages from my windows XP system and can view them through LocalHost in my browser.  I have some PHP pages that will not execute that work under Windows XP/Apache Server .  I go to the synaptic package manager and PHP5-common, PHP5-Mycrypt, PHP5-MySQL, is installed I have tried creating the PHPinfo() test page saved as phpinfo.php in the same directory as my other web pages.  When I try to view this in my browser I get nothing, a blank page. Anybody have any suggestions on something I'm missing or maybe a guide for further testing and getting this to work?  All help will be appreciated.

---

### Post by Dr Small on 2008-10-23
The file phpinfo.php should look exactly like this:
[php]<?php
phpinfo();
?>[/php]

---

### Post by nnamdi on 2008-10-23
u could call it up from another  system on a network

---

### Post by JKHinton CPBD on 2008-10-23
Thank you Dr Small I had missed the first question mark.  I now have the PHP info box up. PHP version 5.2.4-2ubuntu5.3 Do you have any suggestions on why my PHP scripts are not running under Ubuntu but are running under XP/Apache?  They were all copied over and they all work but the .PHP extension pages.

---

