---
title: "not able to install any software on my machine"
date: 2019-06-29
forum: New to Ubuntu
---

### Post by pratap73 on 2019-06-29
code
sudo apt-get install gparted
[sudo] password for user: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: The package php7.2-readline needs to be reinstalled, but I can't find an archive for it.

---

### Post by Impavidus on 2019-06-29
Can you show us your software sources?```
cat /etc/apt/sources.list
```php7.2-readline is available in the official repositories for Ubuntu 18.04 and up. It should be reinstalled before you can do anything else with your package manager.

---

### Post by pratap73 on 2019-07-06
cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main multiverse restricted universe
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) bionic-updates main
cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main multiverse restricted universe
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) bionic-updates main

---

### Post by Impavidus on 2019-07-06
That seems OK. Maybe someone else sees a problem.

What do you get from these commands?```
dpkg --list | grep -v '^rc \|^ii '
apt policy php7.2-readline

```Just trying to find out what's wrong.

---

### Post by TheFu on 2019-07-06
Run 
```
sudo apt update
sudo apt upgrade

```first. The package lists are probably out of date.

gparted doesn't need php.

---

### Post by pratap73 on 2019-07-06
code
```
dpkg --list | grep -v '^rc \|^ii '
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                      Architecture Description
+++-======================================-============================================-============-===============================================================================
ic  php7.2-cli                             7.2.19-0ubuntu0.18.04.1                      amd64        command-line interpreter for the PHP scripting language
ic  php7.2-json                            7.2.19-0ubuntu0.18.04.1                      amd64        JSON module for PHP
ic  php7.2-mbstring                        7.2.19-0ubuntu0.18.04.1                      amd64        MBSTRING module for PHP
ic  php7.2-opcache                         7.2.19-0ubuntu0.18.04.1                      amd64        Zend OpCache module for PHP
iUR php7.2-readline                        7.2.19-0ubuntu0.18.04.1                      amd64        readline module for PHP
ic  php7.2-xml                             7.2.19-0ubuntu0.18.04.1                      amd64        DOM, SimpleXML, WDDX, XML, and XSL module for PHP
```

```
apt policy php7.2-readline
php7.2-readline:
  Installed: 7.2.19-0ubuntu0.18.04.1
  Candidate: 7.2.19-0ubuntu0.18.04.1
  Version table:
 *** 7.2.19-0ubuntu0.18.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        500 [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     7.2.3-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
```

---

### Post by Bashing-om on 2019-07-06
pratap73; Hello :)

I poke my nose into this -

The package is there in the repo:
> 
sysop@x1804mini:~$ apt list php7.2-readline
Listing... Done
php7.2-readline/bionic-security,bionic-updates 7.2.19-0ubuntu0.18.04.1 amd64
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1804mini:~$ 


what shows from your system:
```

apt list php7.2-readline
dpkg -L php7.2-readline

```

whereas I can expect that once we get  php7.2-readline installed we can get the others to fall inline.

[INDENT][INDENT]there must be a reason why not
[/INDENT][/INDENT]

---

### Post by pratap73 on 2019-07-09
apt list php7.2-readline
Listing... Done
php7.2-readline/bionic-security,bionic-updates,bionic-updates,now 7.2.19-0ubuntu0.18.04.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

---

### Post by pratap73 on 2019-07-09
dpkg -L php7.2-readline
/.
/etc
/etc/php
/etc/php/7.2
/etc/php/7.2/mods-available
/usr
/usr/lib
/usr/lib/php
/usr/lib/php/20170718
/usr/lib/php/20170718/readline.so
/usr/share
/usr/share/bug
/usr/share/bug/php7.2-readline
/usr/share/bug/php7.2-readline/control
/usr/share/bug/php7.2-readline/script
/usr/share/doc
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/php7.2-readline
/usr/share/php7.2-readline
/usr/share/php7.2-readline/readline
/usr/share/php7.2-readline/readline/readline.ini
/usr/share/doc/php7.2-readline

---

### Post by Bashing-om on 2019-07-09
pratap73; Hummmm ...
Odd as that last shows installed, but we have:
> 
iUR php7.2-readline


Can not hurt to try:
```

sudo apt install --reinstall php7.2-readline

```

And see what then the package manager has to advise.

Then what shows:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

