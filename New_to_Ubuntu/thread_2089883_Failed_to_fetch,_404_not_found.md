---
title: "Failed to fetch, 404 not found"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by nesoor on 2012-11-30
Hey,

I have the somehow the same problem I think.
I can't update either my Ubuntu i get the following error message.
I tried also several servers.

nesoor@Kenyen:~$ sudo apt-get updrade
[sudo] password for nesoor: 
E: Invalid operation updrade
nesoor@Kenyen:~$ ~$ sudo apt-get upgrade
~$: command not found
nesoor@Kenyen:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  firefox-locale-en flashplugin-installer linux-libc-dev
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,357 kB of archives.
After this operation, 24.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-en i386 16.0.1+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/multiverse flashplugin-installer i386 11.2.202.243ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main linux-libc-dev i386 3.2.0-32.51
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_16.0.1+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_16.0.1+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.243ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.243ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-32.51_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-32.51_i386.deb)  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by oldos2er on 2012-11-30
Post moved to its own thread.

---

