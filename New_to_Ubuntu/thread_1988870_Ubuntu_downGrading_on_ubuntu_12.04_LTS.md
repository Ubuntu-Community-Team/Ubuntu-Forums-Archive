---
title: "Ubuntu downGrading on ubuntu 12.04 LTS"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by chksnrao on 2012-05-28
Hi,
I am new to Ubuntu...
I have doubt about Ubuntu. 
Now I am using Ubuntu 12.04 LTS. i was install apache2 & php5 and i want to downgrading php5.3 version to php5.2 version in Ubuntu 12.04 LTS O/S.

It is possible to install the downgrade version of php in the new version of Ubuntu12.04 LTS.

please help......

---

### Post by jtarin on 2012-05-28
[Software downgrade guide]("http://ubuntuforums.org/showthread.php?t=321156")

[Downgrade PHP]("http://www.nickveenhof.be/blog/reverting-or-downgrade-php-53-52-ubuntu-lucid-lynx-1004").....change PHP version and Ubuntu version appropriately.

---

### Post by chksnrao on 2012-05-29
Hi jtarin,

thank you for your replay.... 

but it is applicable to (downgrade PHP 5.3 to 5.2) in Ubuntu Lucid Lynx 10.04. but O/S is Ubuntu 12.04 LTS...So, it is possible to downgrade in Ubuntu 12.04 LTS.... ?

If it is possible i was follow the Link [Downgrade]("http://www.nickveenhof.be/blog/reverting-or-downgrade-php-53-52-ubuntu-lucid-lynx-1004").

Thank you...!

Krish

---

### Post by zombifier25 on 2012-05-29
Yes it's for Lucid Lynx but it should work with 12.04. Just replace all occurances of "lucid" with "precise".

---

### Post by jtarin on 2012-05-29
> **chksnrao said:**
> Hi jtarin,

thank you for your replay.... 

but it is applicable to (downgrade PHP 5.3 to 5.2) in Ubuntu Lucid Lynx 10.04. but O/S is Ubuntu 12.04 LTS...So, it is possible to downgrade in Ubuntu 12.04 LTS.... ?

If it is possible i was follow the Link [Downgrade]("http://www.nickveenhof.be/blog/reverting-or-downgrade-php-53-52-ubuntu-lucid-lynx-1004").

Thank you...!

KrishI cannot guarantee if it will work. I'm only assuming it will work. If all dependencies (if any) are met I dont see why it wouldn't work. Backup your /etc/apt/sources.list  before doing anything.

here are two more links with information on methods and security of downgrading PHP.

[http://ubuntuforums.org/showthread.php?p=11920993](http://ubuntuforums.org/showthread.php?p=11920993)
[http://randyfay.com/node/63](http://randyfay.com/node/63)

---

### Post by chksnrao on 2012-05-29
Hi zombifier,

Thank you for your reply...
I will try this one....


Thank you..!

Krish

---

