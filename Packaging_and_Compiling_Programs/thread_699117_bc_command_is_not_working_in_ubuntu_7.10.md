---
title: "bc command is not working in ubuntu 7.10"
date: 2008-02-17
forum: Packaging and Compiling Programs
---

### Post by jaspreet2142 on 2008-02-17
i tried to run bc command in ubuntu 7.10 but it show me message that 
bc command is not installed try installing it by entering ubuntu disk in your
drive and type sudo apt-install bc
when i tried it it shows that enter ubuntu 7.10 gusty gibbon cd

---

### Post by ashmew2 on 2008-02-17
if its asking you for the cd , 

do in the terminal :

```
sudo gedit /etc/apt/sources.list
```

and comment out the all the lines with the deb cdrom( Put a # before their name) , For example :

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

Then do a ```
sudo apt-get update
```
Then```
 sudo apt-get install bc
```

---

### Post by jaspreet2142 on 2008-02-17
thanx for your reply

i had done all the steps but after 'sudo apt-get install bc'

it say couldn't find bc package

---

### Post by ashmew2 on 2008-02-17
You can get the bc installer package by going to [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbc%2Fbc_1.06-20ubuntu2_i386.deb&md5sum=d807d4feb8a2783d8b57dfc8c27f83d3&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fb%2Fbc%2Fbc_1.06-20ubuntu2_i386.deb&md5sum=d807d4feb8a2783d8b57dfc8c27f83d3&arch=i386&type=main)

Btw , Have you enabled the Universe and Multiverse Repositories ?

---

### Post by jaspreet2142 on 2008-02-21
actually i am running xp and i installed ubuntu 7.10 in vmware 6 but i installed only CLI
version cause i am an eng. student and i installed it only to practice at home what i am studing in college but i found out that bc command is not working
i tried to install bc package but i was unable to mount it on ubuntu
plz help

---

