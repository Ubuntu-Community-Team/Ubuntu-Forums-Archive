---
title: "updates"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by pdtpatrick on 2008-05-26
Im coming from fedora so some things are a bit different in this debian type environment. How do you make your system update from the command line.. im guessing its not sudo apt-get update or sudo aptitude update .. 

I tried those and yet the update just sat there.. i know apt-get uses sources from the internet to update or download applications so the computer update would be local? what do i use to update that..?

---

### Post by sharks on 2008-05-26
it's sudo apt-get upgrade

---

### Post by iaculallad on 2008-05-26
> **pdtpatrick said:**
> Im coming from fedora so some things are a bit different in this debian type environment. How do you make your system update from the command line.. im guessing its not sudo apt-get update or sudo aptitude update .. 

I tried those and yet the update just sat there.. i know apt-get uses sources from the internet to update or download applications so the computer update would be local? what do i use to update that..?

Just make sure that you have added the repositories:

System->Administration->Software Sources and make sure that Main, Universe, Restricted, Multiverse (under the Ubuntu software tab) is enabled and "Installable from CD-ROM/DVD is uncheck. Click on "Close" button and do your sudo apt-get update/ sudo apt-get upgrade on the terminal.

---

### Post by cdtech on 2008-05-26
Yes, sudo apt-get update should give an output something like:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Fetched 5B in 1s (4B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pdtpatrick on 2008-05-26
sweet - thanks fella!

---

