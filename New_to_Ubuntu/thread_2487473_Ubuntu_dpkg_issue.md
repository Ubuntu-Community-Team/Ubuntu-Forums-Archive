---
title: "Ubuntu dpkg issue"
date: 2023-06-06
forum: New to Ubuntu
---

### Post by joshi-1234 on 2023-06-06
hii,
i i have ubuntu 20.04 and when i try to run **sudo dpkg --configure -a **this command i get this error


dpkg: error processing package php7.4-common (--configure):
 installed php7.4-common package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of php7.4-readline:
 php7.4-readline depends on php7.4-common (= 7.4.3-4ubuntu2.18); however:
  Package php7.4-common is not configured yet.

dpkg: error processing package php7.4-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.4-cli:
 php7.4-cli depends on php7.4-common (= 7.4.3-4ubuntu2.18); however:
  Package php7.4-common is not configured yet.
 php7.4-cli depends on php7.4-readline; however:
  Package php7.4-readline is not configured yet.

dpkg: error processing package php7.4-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-cli:
 php-cli depends on php7.4-cli; however:
  Package php7.4-cli is not configured yet.

dpkg: error processing package php-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.4-opcache:
 php7.4-opcache depends on php7.4-common (= 7.4.3-4ubuntu2.18); however:
  Package php7.4-common is not configured yet.

dpkg: error processing package php7.4-opcache (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.4-json:
 php7.4-json depends on php7.4-common (= 7.4.3-4ubuntu2.18); however:
  Package php7.4-common is not configured yet.

dpkg: error processing package php7.4-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jsonlint:
 jsonlint depends on php-cli; however:
  Package php-cli is not configured yet.
  Package php7.4-cli which provides php-cli is not configured yet.

dpkg: error processing package jsonlint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php7.4-common
 php7.4-readline
 php7.4-cli
 php-cli
 php7.4-opcache
 php7.4-json
 jsonlint

what to do?

---

### Post by Rubi1200 on 2023-06-06
Hi and welcome to the forums :-)

dpkg does not install dependencies.

To fix this, try the following in a terminal:

```
sudo apt-get install -f
```

Hope this helps.

---

### Post by MAFoElffen on 2023-06-08
Well, Ubuntu 20.04 LTS was PHP version 7.4...

A lot of times this is a chicken before the egg affair, where if you do
```

sudo apt install --fix-broken

```
It will error out and then tells you to do
```

sudo dpkg --configure -a

```
...and vice versa, around in circles. I think this might be one of those times.

I would just reinstall it to ensure all the dependencies are there and the versions of the pieces match each other.
```

sudo apt install --reinstall php7.4 

```
Although, if you are commercial, and/or have mission critical things written in PHP, you can still get security updates from Ubuntu Pro ( [https://ubuntu.com/security/notices/USN-5818-1](https://ubuntu.com/security/notices/USN-5818-1) ), but I would upgrade to Ubuntu 22.04, so that you could be using PHP 8.1... PHP 7.4 officially reached end-of-life Q4 2022.

---

