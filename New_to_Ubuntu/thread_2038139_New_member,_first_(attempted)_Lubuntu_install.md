---
title: "New member, first (attempted) Lubuntu install"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by zuren on 2012-08-06
I'm truly a beginner to Linux and my first post!  I'm here with the hope of  breathing some new life into an old computer.  The system:

Dell Dimension L866R tower (circa 1999)
Pentium III 866MHz
256MB RAM (soon to be 512MB max-ed) 
4+1 USB PCI card
Soundblaster Live PCI sound card
Dynex NIC PCI card
Intel 82810E Graphics Controller (monitor currently connected to this)
ATI Radeon 7500 video card (installed but not working; also have a Voodoo2 in a box that is not recognized by XP)
currently running XP SP3 (slowly)

I did some research and elected to try Lubuntu 12.04 first due to the  age and specs of the system.  From what I read, Lubuntu should run fine  on this and Ubuntu may be possible with the increased RAM.  This is an  "experimental" box that I don't really care about so I tried to do a  full install immediately.

Even though I selected "install" it looks like it is running from the CD  and even at that it boots to a black screen where I have a cursor and  can right-click to get a menu but that is it.  I also tried selecting  "nomodeset" based on some searches.  It appears that the ISO burned to  the disc correctly.  XP is still there but my hope is to make it a full  Linux box for playing and learning.  

I'm continuing to search and learn but I'm looking for advise for what  to try next or if there is a fatal flaw in the hardware that is  preventing it from installing.

Thank you for any help!

---

### Post by marinara on 2012-08-06
if you have a menu and mouse cursor, you don't need to mess with modeset.  
I donno what is wrong, but you probably need the alternate cd.
[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)

---

### Post by mastablasta on 2012-08-06
with 256MB ram you need to use alternate CD.
 
a problem might be the kernel. if support for your CPU is still there then it will be ok if not then you need to find a distro for older maschines.

---

### Post by audiomick on 2012-08-06
> **mastablasta said:**
> with 256MB ram you need to use alternate CD.

Yep, try that first.

---

### Post by zuren on 2012-08-06
> **mastablasta said:**
> with 256MB ram you need to use alternate CD.

That worked!  Lubuntu is up and seems happy.  When I install the 512MB, it looks like it will still be considered a low RAM system and should stay with Lubuntu for the duration?

It is still using the onboard graphics controller rather than the video card so I will have to troubleshoot that but otherwise I'm happy!

Thank you!

---

### Post by audiomick on 2012-08-06
> **zuren said:**
>   When I install the 512MB, it looks like it will still be considered a low RAM system and should stay with Lubuntu for the duration?

Yes, 512MB is considered low ram these days. This 10.04 Ubuntu install on a Lenovo netbook is using around 300MB RAM with just the system monitor and Firefox with 4 tabs open.

---

