---
title: "four problems"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by santhust on 2008-08-31
hi. yesterday i installed ubuntu 8.o4.lts!
 i am faced with the following problems:

1: i have to use some softwares like--nimultisim,PsPice (both of these are simulation softwares of analyzing electronics circuits). these i found unable to install and use in ubuntu.earlier when i had windows vista as an alternate operating system on my hard disk, i could install them there (in vista) and use. now i want to use them in ubuntu. how to get around this problem??

2: in my laptop (dell inspiron 1525),there is an integrated webcam. now how to get it working in ubuntu? i have a dell webcam installation CD, which also was installed in vista.(now vista has been formated, when i yesterday installed ubuntu, knowingly.)

3: vcd/dvd not playing. also a dvd, which i suppose contains gparted, is isn't even being recognized.

4: how to get around with dealing .exe files in ubuntu? finding difficulty in installing some other applications also( which are easily installable in windows). would i be able to find what ever i need in synaptic package manager? if not how to get such applications working in ubuntu?

please help...):P

---

### Post by Irony on 2008-08-31
You need to look in synaptic (System > Admin > Synaptic) for the linux equivalents of these programs.

Also look at Wine which may enable you to install certain windows programs.

---

### Post by RSingh on 2008-08-31
well the webcam problem can be fixed by installing cheese.

Terminal:

sudo aptitude install cheese

---

### Post by Nepherte on 2008-08-31
1. Unfortunately you are mixing up Windows and Linux. These two operate totally different. Linux (and therefore Ubuntu) doesn't work with .exe files. Almost every piece of Windows software will not work in Ubuntu. Some programs have a version for Linux as well (Firefox, Thunderbird, OpenOffice, Filezilla, ...) and a very small part of the Windows programs can be simulated in Ubuntu with 'wine'. You can try to simulate nimultisim and PsPice with wine or find an alternative that works Linux.

3. The necessary codecs are problably not installed. This multimedia guide will give you all the codecs you need: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

4. See point 1. The way to find and install programs is to look for it in Synaptic.

---

### Post by kellemes on 2008-08-31
Something to read..
[https://help.ubuntu.com/8.04/switching/index.html]("https://help.ubuntu.com/8.04/switching/index.html")

By the way, welcome to the Ubuntu community.

---

### Post by billgoldberg on 2008-08-31
[You don't seem to understand that linux != windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by GrandpaLeaman on 2008-08-31
While searching the EE homepage, I found reference to an open source design tool called Ngspice. Here is a link to the web site:

[http://ngspice.sourceforge.net/](http://ngspice.sourceforge.net/)

It says on the web site:

> Ngspice is part of             [gEDA project]("http://www.geda.seul.org/"), a full GPL'd suite of Electronic Design             Automation tools.This may be what you are looking for. I hope this helps.

---

