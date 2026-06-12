---
title: "Can't remove MySQL clean."
date: 2012-03-08
forum: New to Ubuntu
---

### Post by tarundas on 2012-03-08
Ubuntu 11.10. I had MySQL installed which I was not aware of and tried to install LAMP. "sudo apt-get install lamp-server^" ... In the middle of installation  it gave an error ...

useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g mysql -s /bin/false -u 116 mysql' returned error code 1. Exiting.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to remove MySQL and then reinstall MySQL but without any success 
I tried following commands 
apt-get -f install ( same error)
then I found following commands somewhere in the Internet and tried ...
apt-get purge mysql-server
apt-get purge mysql-common
rm -rf /var/log/mysql
rm -rf /var/log/mysql.*
rm -rf /var/lib/mysql
rm -rf /etc/mysql
then I tried reinstalling MySQL
sudo apt-get install mysql-server --fix-missing --fix-broken
the command end up with an error.

How can I remove mysql completely and reinstall it again. I don't really want to format my harddisk and reinstall ubuntu from scratch.

---

### Post by LowSky on 2012-03-08
What error is it giving you when you tried:

```
sudo apt-get install mysql-server --fix-missing --fix-broken
```?

---

### Post by wyliecoyoteuk on 2012-03-08
have you tried 

```

sudo dpkg --configure -a
sudo apt-get update

```

---

