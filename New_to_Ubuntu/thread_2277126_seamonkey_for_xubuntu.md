---
title: "seamonkey for xubuntu"
date: 2015-05-06
forum: New to Ubuntu
---

### Post by Southron on 2015-05-06
This is for seamonkey for ubuntu does will it work on xubuntu?

Will everything that works on ubuntu work on xubuntu?
[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

I couldnt find it on Software Center. 

I am very new to linux and programming. Would anyone advise against trying to install it? I don't want to mess my computer up

---

### Post by kerry_s on 2015-05-06
it'll work just fine.

---

### Post by vasa1 on 2015-05-06
There's also a Seamonkey ppa. The guy who keeps that ppa updated posts quite often and will surely post the way to install it :) I've forgotten the link :(

---

### Post by vasa1 on 2015-05-06
The "guy" is **nanotube** and see this for example: [http://ubuntuforums.org/showthread.php?t=2249826](http://ubuntuforums.org/showthread.php?t=2249826)

---

### Post by Southron on 2015-05-06
I followed the directions on this page
[http://www.maketecheasier.com/install-latest-version-firefox-ubuntuzilla/](http://www.maketecheasier.com/install-latest-version-firefox-ubuntuzilla/)
but except for the first command none of them did anything

---

### Post by Southron on 2015-05-07
> **vasa1 said:**
> There's also a Seamonkey ppa. The guy who keeps that ppa updated posts quite often and will surely post the way to install it :) I've forgotten the link :(

What is a ppa? 

It looks like following the directions on that site worked. I have Mozilla Build for seamonkey and mozilla build for firefox now. 

Heres what my terminal says. Do you agree the whole seamonkey is installed?

edwin@edwin-ThinkCentre-A63:~$ sudo apt-get install seamonkey-mozilla-build
[sudo] password for edwin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  seamonkey-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 41.9 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main seamonkey-mozilla-build amd64 2.33.1-0ubuntu1 [41.9 MB]
Fetched 41.9 MB in 3min 33s (196 kB/s)                                         
Selecting previously unselected package seamonkey-mozilla-build.
(Reading database ... 235980 files and directories currently installed.)
Preparing to unpack .../seamonkey-mozilla-build_2.33.1-0ubuntu1_amd64.deb ...
Adding 'diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey-mozilla-build'
Unpacking seamonkey-mozilla-build (2.33.1-0ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up seamonkey-mozilla-build (2.33.1-0ubuntu1) ...
edwin@edwin-ThinkCentre-A63:~$

I found composwer and everything works. I guess Im a programmer after all

---

