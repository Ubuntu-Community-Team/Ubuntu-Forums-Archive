---
title: "Duel Boot installation w/out XP CDs: Possible?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by ibgeorgeb on 2008-08-07
I received a Dell Inspiron 5100 laptop withOUT any of the original CDs. Presently, it's running WindowsXP (Home Edition). I would like to install Xubuntu 8.04 as  a duel boot.

I've read that I would have to re-partition the HDD using the WindowsXP CDs that supposedly come with a new laptop. I ain't got no Windows-CDs (sic).

Questions: #1) Can I  install Xubuntu on this laptop without the WindowsXP CDs?  In other words, I just hit the Install icon on the live Xubuntu I'm now running?

GParted shows:

Partition---filesystem---size-----used------unused------flags
/dev/sda1---fat16-------39.19MiB--5.78MiB---33.41MiB 
/dev/sda2---ntfs--------37.21GiB--9.89GiB---27.33GiB----boot
unallocated-unallocated-7.84MiB   ----       ----

#2) Is  a 10GiB partition minimum for Xubuntu? I plan to use it for internet access only. 
#3) If so, where in the installation process do I tell it to partition Xubuntu to 10Gib.

Thank you in advance for your assistance.  gB

---

### Post by logos34 on 2008-08-07
choose the option 'Guided--resize' and it will shrink sda2 down to make room for xubuntu /.  

> To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.

---

### Post by scooterpd on 2008-08-07
I just walked my cousin through this no more than 2 hours ago using Kubuntu 8.04.  
First, start up XP, make sure your C: drive (or whatever drive XP is installed on) has at least 6gb of space available for your linux partition, and defrag once or twice (I recommend Auslogics Disk Defrag, fast and free).  Then make sure to put the Xubuntu cd in your cd/dvd drive and reboot.  

When the screen boots up asking if you want to try or install, choose Install Xubuntu, and do as logos34 said above.  It is pretty self-explainatory.  Then go throught the rest of the installer and enjoy.  No need for XP cd's.

I recommend around 4-6GB for Xubuntu, depending upon how much stuff you might decide on adding at a later time.  If doesnt hurt as long as you have the room.

---

### Post by LowSky on 2008-08-07
Windows has a built in defraging tool

Start> programs> Accessories>System tools> Defragemnt

I reccomend doing a disk cleaning before defraging.. under the same menu

---

### Post by ibgeorgeb on 2008-08-07
Thank you everyone for your suggestions. It's getting late here and I have some "honey-do's" to finish. I'll jump on this at first light tomorrow. Any other suggestions are appreciated. Merci beaucoup, gB

---

### Post by ace007 on 2008-08-07
Check out this guide:[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

