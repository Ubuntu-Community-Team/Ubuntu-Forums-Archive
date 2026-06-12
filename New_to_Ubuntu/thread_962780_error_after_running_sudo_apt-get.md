---
title: "error after running sudo apt-get"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by wawadave on 2008-10-29
i ran sudo apt-get as instructed in this thread:
[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

i see in terminal i got this error
Reading package lists... Done
W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_qgis_ubuntu_dists_gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
bud@bud-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
bud@bud-desktop:~$ sudo apt-get update

how would i go about it to fix this error?

---

### Post by bodhi.zazen on 2008-10-29
Your first error can be ignored, it is a warning. To fix it you need to download and install the apt-key for the repository (first error) and remove teh duplicate repo (second error). See the repository main page for how to do this / where to get the link.

Your second error was because you did not use sudo.

---

### Post by fooman on 2008-10-29
what happened after "bud@bud-desktop:~$ sudo apt-get update"?

---

### Post by markharding557 on 2008-10-29
if you want to follow the guide precisely then you can open a tempory root console with> sudo -ithen you won't have to type sudo more than once

---

### Post by wawadave on 2008-10-29
ok i got rid of the duplicate. 
but i cannot find where to get that public key i googled on this(found little this post and a few other) and  ubuntu site searched. i know where to add the key if i can get it.

---

### Post by bodhi.zazen on 2008-10-29
Well , you do not really "need" the key.

You can try downloding it and installing it if you wish :

[http://deb.mulx.net/dists/hardy/Release.gpg](http://deb.mulx.net/dists/hardy/Release.gpg)

See also : [http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/](http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/)

---

### Post by wawadave on 2008-10-29
i had actually gone to there site and found:
With hardy repository

Type the following commands :
sudo wget [http://deb.mulx.net/playonlinux_hardy.list](http://deb.mulx.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://deb.mulx.net/pol.gpg](http://deb.mulx.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux
With gutsy repository

Type the following commands :
sudo wget [http://deb.mulx.net/playonlinux_gutsy.list](http://deb.mulx.net/playonlinux_gutsy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://deb.mulx.net/pol.gpg](http://deb.mulx.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux

that fixed the problem two solved!!

but now i get a wine problem showing up.

Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
  Unable to connect to wine.budgetdedicated.com http:
Fetched 15.8kB in 2min5s (127B/s)                            
Reading package lists... Done
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2)  Unable to connect to wine.budgetdedicated.com http:


so going to try and see why this is now coming up any ideas would be welcomed!!

---

### Post by bodhi.zazen on 2008-10-29
Looks like the server is down. Not much you can do but wait ;)

---

### Post by wawadave on 2008-10-29
good its not my end!!!
thanks for your help!!!

---

