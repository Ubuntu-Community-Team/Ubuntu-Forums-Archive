---
title: "&quot;Upgrade&quot; my Ubuntu 20.04 to Ubuntu Studio"
date: 2022-01-25
forum: New to Ubuntu
---

### Post by aexistenax on 2022-01-25
Hello, I am trying to *upgrade" my Ubuntu 20.04 to Ubuntu Studio, but since that didn't work out, I'm simply installing all the Debian packages that should come with Ubuntu Studio from Synaptic. Now, every package I installed from [https://wiki.debian.org/Multimedia](https://wiki.debian.org/Multimedia) so far gave me the same error message:  E: cpl-plugin-muse-calib: installed cpl-plugin-muse-calib package post-installation script subprocess returned error exit status 1 I also tried to install and to config the very same plugin from the terminal, without any results: it enters an endless loop in which it tells me "that the package is being used by synaptic", eventhough synaptic is closed and I rebooted. Or it informs me that the "frontend is locked and removing the lock will cause system failure". Anyone has any idea of how to manage to finally install these plugins please? Thanks in advance for your help!

---

### Post by QIII on 2022-01-25
Moved to** New to Ubuntu**

---

### Post by Impavidus on 2022-01-25
Ubuntu Studio is just Ubuntu with a different set of default packages and installing the package ubuntustudio-desktop should be all you had to do. It should pull in all the other packages. I don't know if that's what you tried.

Ubuntu is not Debian. Packages for Debian don't always work on Ubuntu, so trying to install a lot of them is likely to break your system. Which is what happened. Yes, Ubuntu uses Debian-style packages and for packages with few dependencies it usually works, until it doesn't. All Ubuntu studio stuff can already be installed from the official Ubuntu repository, so stick to that. Remove the packages from other sources, those it complains about first. If you're really stuck, it may be best to do a clean install of Ubuntu Studio.

---

### Post by aexistenax on 2022-01-25
Thanks for your answer. I tried installing the package ubuntu studio, but it didn't work out. I got the icons on my programs' list, and I mean only those of "ubuntu studio installer" and "ubuntu studio", but not one single program more was added. I know Ubuntu is based on Debian but it's not Debian, that's why I said I am using synaptic to do all the manual installations, within my Ubuntu 20.04, of all the software that figures as having to be in any "normal ubuntu studio installation". But I'm downloading all the files needed, and only when they are indeed needed, from the canonical website official mirror, following synaptic, only using the list of soft it should have installed to seek them one by one in synaptic, and then apply their installation. I haven't even tried to install packages from other sources than canonical official website repositories. And it's not "complaining" about anything that I did install, but about a small plugin it claims it can NOT install, however it is still demanded by each and every piece of soft I'm installing with synaptic. I tried to install this particular plugin using the terminal, and I also got an error message, the same I mentioned above. My system is NOT broken, it's fully functional. It only asks me, each damned time!, for the "cpl-plugin-muse-calib", and it claims it can't configure it, although it says it's installed. Yes, I tried to do a manual cfg with the terminal, that didn't work either. I simply need some way to workaround this plugin problem so all the soft can work properly, not to do yet another fresh installation, seen as I've just finished one last one.......Thanks!

---

### Post by aexistenax on 2022-01-25
By the way, I may have missexplained myself: what I'm chosing from the Debian Multimedia website is NOT the packages, simply the names of all the soft that's media dedicated, and then doing a manual search, item by item, on synaptic, which is configured to seek ONLY on the canonical official repositories. Because Ubuntu Studio doesn't have an "easy to find" list of all the soft that should come with it, or at least not one that I know of, although it wouldn't be the first time I make a mistake. :-)

---

### Post by Impavidus on 2022-01-25
OK, that makes things clearer.

It appears your package management is broken anyway. It will complain about an unconfigured package until it's either configured and fully installed, or removed, and will be very reluctant to do anything else until fixed. So let's have a look at that.
```
sudo apt update
sudo apt upgrade
```Could you show us the complete and unabridged output? I'm hoping to find something interesting in the error message.

---

### Post by aexistenax on 2022-01-25
Thanks for your answer. Here's the message for the first command. aexis@EricasLastWish:~$ sudo apt update [sudo] password for aexis:  Hit:1 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal InRelease Get:2 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]      Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                       Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]       Get:5 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB] Get:6 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [592 kB] Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [40.7 kB] Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [66.3 kB] Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2’464 B] Get:10 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1’510 kB] Get:11 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [281 kB] Get:12 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/main DEP-11 48x48 Icons [60.8 kB] Get:13 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/main DEP-11 64x64 Icons [98.3 kB] Get:14 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [664 kB] Get:15 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [894 kB] Get:16 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [364 kB] Get:17 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [940 B] Get:18 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-backports/main amd64 DEP-11 Metadata [7’964 B] Get:19 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [12.2 kB] Fetched 4’931 kB in 4s (1’266 kB/s)                                            Reading package lists... Done Building dependency tree        Reading state information... Done All packages are up to date. aexis@EricasLastWish:~$   now the second command aexis@EricasLastWish:~$ sudo apt upgrade Reading package lists... Done Building dependency tree        Reading state information... Done Calculating upgrade... Done E: Could not get lock /var/cache/apt/archives/lock. It is held by process 19333 (synaptic) N: Be aware that removing the lock file is not a solution and may break your system. E: Unable to lock directory /var/cache/apt/archives/ aexis@EricasLastWish:~$   I hope this helps you help me out. Thanks for your time!

---

