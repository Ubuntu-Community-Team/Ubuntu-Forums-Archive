---
title: "[SOLVED] adept problems"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by stonerrob420 on 2008-09-22
Hello! I am getting this warning :The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem. Does anybody know how to fix this? With adept not working I am at a complete loss.

---

### Post by stonerrob420 on 2008-09-22
when I try to use $sudo apt-get update I get this :
 
sudo: apt-setup: command not found
rob@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Hit [http://viewizard.com](http://viewizard.com) debian/ Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://viewizard.com](http://viewizard.com) debian/ Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign mirror://www.getdeb.net hardy/ Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://viewizard.com](http://viewizard.com) debian/ Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://viewizard.com](http://viewizard.com) debian/ Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Ign mirror://www.getdeb.net hardy/ Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://viewizard.com](http://viewizard.com) debian/ Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Ign mirror://www.getdeb.net hardy/ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit mirror://www.getdeb.net hardy/ Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 1B in 44s (0B/s)
Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
rob@ubuntu:~$

---

### Post by stonerrob420 on 2008-09-22
It seems that my /var directory is full so I ran $sudo apt-get clean. it freed up 550MB. now adeptt works again. Is there anyway to increase size of /var directory?

---

### Post by willca on 2008-09-23
A couple ways I can suggest but since I dont know your setup in that computer here is what I would do.

1- if i got some partition that is not used, then use that if its bigger or perhaps move /var/cache to it.

2- i will use gparted while booted from a livecd.

---

