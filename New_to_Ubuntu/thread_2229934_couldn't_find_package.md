---
title: "couldn't find package"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by engineer2 on 2014-06-16
Hello ...i'm new the the whole linux things ...i  need some packages for a software i'm installing but it says couldn't find package:

see these are the packages i need to install :
openmotif
openmotif-devel
openmotif22
openssl-devel
openssl-static
pam-devel
libXpm
libXpm-devel
ncurses
ncurses-devel

by using apt-get install i've got 
E: couldn't Finf Package ****

Note:i'm using Ubuntu 10.04LTS x64

I appreciate help:confused:
Regards

---

### Post by mörgæs on 2014-06-16
Hi, welcome to the fora.

Please read this regarding 10.04: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by LastDino on 2014-06-16
You would benefit greatly if you shifted to 14.04 or at least 12.04 for year or two,

---

### Post by engineer2 on 2014-06-16
Thanks ..i couldn't upgrade since the software i want to install support 10.04lts but the above versions does not list in the supported OS 
and for the end of life for 10.04lts desktop i have 12.04lts installed in other laptop and i tried to install these packages and got the same result couldn't find the package :confused:

---

### Post by LastDino on 2014-06-16
Well, what kind of software is it? Maybe, look for an alternative, or run the older Ubuntu in VM which is isolated?

---

### Post by mörgæs on 2014-06-16
On the 12.04 system please run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and post the results in CODE tags.

---

### Post by steeldriver on 2014-06-16
Those package names don't seem consistent with current (even 10.04) Debian/Ubuntu naming practices, so you'll need to guess a bit. I'd start with

libmotif-dev libssl-dev libpam0g-dev libxpm-dev libncurses5-dev

which should all be available in 10.04 once you've added the old-releases repo

References:
[http://packages.ubuntu.com/lucid/libmotif-dev](http://packages.ubuntu.com/lucid/libmotif-dev)
[http://packages.ubuntu.com/lucid/libssl-dev](http://packages.ubuntu.com/lucid/libssl-dev)
[http://packages.ubuntu.com/lucid/libpam0g-dev](http://packages.ubuntu.com/lucid/libpam0g-dev)
[http://packages.ubuntu.com/lucid/libxpm-dev](http://packages.ubuntu.com/lucid/libxpm-dev)
[http://packages.ubuntu.com/lucid/libncurses5-dev](http://packages.ubuntu.com/lucid/libncurses5-dev)

---

### Post by engineer2 on 2014-06-16
hello  [COLOR=#000000][B]LastDino  
[/B][/COLOR]iam M.Sc student and i'm trying to build a grid system using open grid scheduler/grid engine which is an official open source version of sun grid engine.

---

### Post by mörgæs on 2014-06-16
No need for old releases. The same packages are available with precise in stead of lucid.

---

### Post by engineer2 on 2014-06-16
hello  [COLOR=#C61919][B]mörgæs
[/B][/COLOR]what do you mean?

---

### Post by mörgæs on 2014-06-16
In post #7 there are five links pointing to packages from Lucid. 

Don't take this as a recommendation to use Lucid / 10.04. If you open the same links with 'precise' you will see the new versions of the packages, as in 
[http://packages.ubuntu.com/precise/libmotif-dev](http://packages.ubuntu.com/precise/libmotif-dev)

Please post the output requested in #6.

---

### Post by steeldriver on 2014-06-16
To clarify, my inclusion of the links to Lucid packages was meant to indicate that **if you absolutely can't upgrade to a supported version for some reason, the packages you likely require appear to be available in Lucid**

---

