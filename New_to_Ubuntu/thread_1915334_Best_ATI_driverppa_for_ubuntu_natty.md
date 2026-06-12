---
title: "Best ATI driver/ppa for ubuntu natty"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by editheraven on 2012-01-26
What are the best ati drivers for ubuntu? I currently have "xserver-xorg-video-ati" from official xorg repository. I can upgrade them by enabling

```
#xorg ppa
# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu natty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu natty main
```

I hadn't installed flgrx driver (from additional drivers or "sudo apt-get install flgrx") because they cause me lag in compiz effects. But this drivers from xorg cause me "checking battery state" sometimes and gives me lag in games. Is there any better 3d acceleration sollution?

---

### Post by mastablasta on 2012-01-26
if you can install fglrx you oculd try to get the latest ones from ATI site. and install them manually.
 
opensource also has an unstable version, but if fglrx support your card it would be better to use those.

---

### Post by editheraven on 2012-01-26
From my experience i have very low performance in compiz with fglrx. (metacity works fine)

---

### Post by mastablasta on 2012-01-26
but the fglrx found at their website is newer than the one in natty repositories that came out at beginning/middle of the year.
 
you could also do better if you upgraded to 11.10.
 
but hard to say for sure, since you didn't give any info on GPU and system.

---

### Post by editheraven on 2012-01-26
I have an ati radeon hd 6770 made by shappire. 2gbddr2/dual core@3ghz

---

### Post by editheraven on 2012-01-27
The website desciption of ati drivers fox x86 says "Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5, or 7.6". And i have "X Protocol Version 11, Revision 0 (X.Org X Server 1.10.4)".  How come. Also, the documentation says that the lastest stable version is 1.11.3. should i enable the xorg ppa and do the upgrade?

---

