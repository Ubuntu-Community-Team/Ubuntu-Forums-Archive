---
title: "cant installl amd overdrive ctrl"
date: 2017-10-15
forum: New to Ubuntu
---

### Post by jhip626 on 2017-10-15
i have been trying to install the program and it keeps getting errors.. this is what i get.
any help is greatly appreciated .
im brand new to linux. so it might be something totally obvious to you that im missing.


Downloads$ sudo dpkg -i amdoverdrivectrl_1.2.7_amd64.deb
(Reading database ... 173816 files and directories currently installed.)
Preparing to unpack amdoverdrivectrl_1.2.7_amd64.deb ...
Unpacking amdoverdrivectrl (1.2.7) over (1.2.7) ...
dpkg: dependency problems prevent configuration of amdoverdrivectrl:
 amdoverdrivectrl depends on libwxbase2.8-0 (>= 2.8.10.1); however:
  Package libwxbase2.8-0 is not installed.
 amdoverdrivectrl depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package amdoverdrivectrl (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for man-db (2.7.6.1-2) ...
Errors were encountered while processing:
 amdoverdrivectrl
josh@josh-Aspire-V5-122P:~/Downloads

---

### Post by oldos2er on 2017-10-15
Dpkg doesn't install dependencies; that is something you need to do manually. Try ```
sudo apt install libwxbase2.8-0
``` Which version of Ubuntu are you running?

---

### Post by ajgreeny on 2017-10-15
You could also install gdebi first and install that package using gdebi which does manage dependencies, unlike dpkg.

Depending on your version of Ubuntu you may also be able to run ```
sudo apt install /path/to/amdoverdrivectrl_1.2.7_amd64.deb
``` but that's only on version 17.04 and later, I think, not sure about 16.04.

---

### Post by jhip626 on 2017-10-15
> **ajgreeny said:**
> You could also install gdebi first and install that package using gdebi which does manage dependencies, unlike dpkg.

Depending on your version of Ubuntu you may also be able to run ```
sudo apt install /path/to/amdoverdrivectrl_1.2.7_amd64.deb
``` but that's only on version 17.04 and later, I think, not sure about 16.04.

i believe its the newest Lubuntu

---

### Post by jhip626 on 2017-10-15
> **oldos2er said:**
> Dpkg doesn't install dependencies; that is something you need to do manually. Try ```
sudo apt install libwxbase2.8-0
``` Which version of Ubuntu are you running?

thats what i get when i try that

josh@josh-Aspire-V5-122P:~$ sudo apt install libwxbase2.8-0
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libwxbase2.8-0
E: Couldn't find any package by glob 'libwxbase2.8-0'
E: Couldn't find any package by regex 'libwxbase2.8-0'
josh@josh-Aspire-V5-122P:~$ 
josh@josh-Aspire-V5-122P:~$

---

### Post by mc4man on 2017-10-15
wxwidgets2.8 was dropped in Ubuntu sometime between 14.04 & 16.04, currently only wxwidgets3.0 is used.

It's available for 16.04 thru this ppa, after 16.04 probably nowhere..
[https://launchpad.net/~codeblocks-devs/+archive/ubuntu/release](https://launchpad.net/~codeblocks-devs/+archive/ubuntu/release)

---

### Post by deadflowr on 2017-10-15
Uninstallable or unusable on anything beyond 14.04.1 as amdoverdrivectrl require the closed-source fglrx driver and catalyst control center which cannot run on anything beyond what comes with 14.04.1.
You can run it on Ubuntu 14.04.1 downloadable from here:
[http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")

---

### Post by jhip626 on 2017-10-15
> **deadflowr said:**
> Uninstallable or unusable on anything beyond 14.04.1 as amdoverdrivectrl require the closed-source fglrx driver and catalyst control center which cannot run on anything beyond what comes with 14.04.1.
You can run it on Ubuntu 14.04.1 downloadable from here:
[http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)

ok so basically it wont work.... well thats a bummer, i wanted to see if i could push this slow processor a bit more. but i guess i cant

---

