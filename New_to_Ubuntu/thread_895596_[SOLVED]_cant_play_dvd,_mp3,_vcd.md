---
title: "[SOLVED] cant play dvd, mp3, vcd"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-20
i cant play my dvd dics, mp3 files, vcd on my newly installed xubuntu.  the player said that i need to download some plugins.  please help.... thanks

---

### Post by LowSky on 2008-08-20
copy and paste this command into a terminal

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb 
```
and then this one
```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

---

### Post by OffAxis on 2008-08-20
you need to install the codecs from medibuntu.

[http://medibuntu.org](http://medibuntu.org)

instructions can be found here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Potatoj316 on 2008-08-20
i would suggest downloading the plugins that it says it needs.  im not too familiar with xubuntu but ubuntu has synaptic package manages, xubuntu probably has something similar, if not the same thing.  Search in there for those plugins. 

alternativly you could do it in the terminal with this command
```
sudo aptitude install PLUGIN
```
where PLUGIN is a list of the plugins that it says you need.  if listing multiple packages to install do not put a comma between them, just list one after another like this
```
sudo aptitude install package1 package2 pacakge3
```

---

### Post by Bucky Ball on 2008-08-20
I thought gstreamer would do the job. I can play all those files and have never downloaded any mediubuntu things.

---

### Post by LowSky on 2008-08-20
> **Bucky Ball said:**
> I thought gstreamer would do the job. I can play all those files and have never downloaded any mediubuntu things.

gstreamer cannot play DVDs or MP3 without installing the codecs

medibuntu solves those issues

---

### Post by silkstone on 2008-08-20
If you don't already have the Medibuntu repos enabled, you may need to do this first...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Paqman on 2008-08-20
The [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683) will tell you everything you need to know.

Short version: get the medibuntu repo, VLC, libdvdcss and xubuntu-restricted-extras.

---

