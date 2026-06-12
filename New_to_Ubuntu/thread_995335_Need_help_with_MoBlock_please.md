---
title: "Need help with MoBlock please"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by AnonUK on 2008-11-27
Hey, i was following the guide on this website - [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

When i try to start MoBlock, it says this:

root@anonymous-laptop:~# sudo moblock-control start
sudo: moblock-control: command not found


Prior to this, i did these two commands. -

root@anonymous-laptop:~# sudo aptitude update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

and then i did:

root@anonymous-laptop:~# sudo aptitude install moblock moblock-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "moblock-control"
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "moblock-control"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      

From the second command it says it can't find anything called moblock :S 

Any help is greatly appreciated:)

---

### Post by nynoah on 2008-11-27
Use this site.  I run Mobloquer.  It is the graphical front end for moblock.  There are some repos for the latest stuff.  Plus instructions.


[http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

Hope that helps.

Noah

---

### Post by AnonUK on 2008-11-27
> **nynoah said:**
> Use this site.  I run Mobloquer.  It is the graphical front end for moblock.  There are some repos for the latest stuff.  Plus instructions.


[http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

Hope that helps.

Noah

Hi, i looked on the site, when i tried to install the graphic interface it said it couldn't find MoBlock

root@anonymous-laptop:~#  sudo apt-get install moblock mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package moblock

---

### Post by nynoah on 2008-11-27
look for mobloquer

---

### Post by nynoah on 2008-11-27
Also reboot too

---

