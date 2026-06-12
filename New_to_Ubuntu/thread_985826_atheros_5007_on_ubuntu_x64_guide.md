---
title: "atheros 5007 on ubuntu x64 guide ?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-11-18
is there a definative up to date guide on how to install madwifi drivers for a atheros 5007 wifi adapter under ubuntu 8.04 x64bit ? ive seen several different ones and i need to know which one works best ?

---

### Post by bumanie on 2008-11-18
Apparently that card can be enabled by loading [backports]("http://backports.ubuntuforums.com/showthread.php?t=969225") - I actually did it by using ndiswrapper on 32bit.

---

### Post by ibizatunes on 2008-11-18
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

I got it working fine last night in x64 bit - same wirless card as you

PS i ran through the instruction twice as it didnt work first time (i think i missed a step out though)

---

### Post by smooth3006 on 2008-11-18
i need a guide for 8.04 x64 not 8.10 but thanks.

---

### Post by aeiah on 2008-11-18
> **smooth3006 said:**
> i need a guide for 8.04 x64 not 8.10 but thanks.

there is a link on the madberry page right at the top of the article that directs you to the 8.04 howto.

---

### Post by smooth3006 on 2008-11-19
> **aeiah said:**
> there is a link on the madberry page right at the top of the article that directs you to the 8.04 howto.

your sure this guide is for 64bit ubuntu ? the reason im asking is i just bought 4gigs of ram and i will be installing x64 bit ubuntu 8.04 pretty soon.

---

### Post by aeiah on 2008-11-19
[SIZE="7"]["...has been tested by me and works for (K)Ubuntu 8.0.4.1(both x86-64 and i686)"]("http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/")[/SIZE]

---

### Post by smooth3006 on 2008-11-20
> **aeiah said:**
> [SIZE="7"]["...has been tested by me and works for (K)Ubuntu 8.0.4.1(both x86-64 and i686)"]("http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/")[/SIZE]

just wanted to make sure because ive been reading about the ndiswrapper method. i just don't want to run into issues.

---

### Post by smooth3006 on 2008-11-22
does anybody know if the ndiswrapper method is a better way to go with x64 & madwifi ?

---

### Post by smooth3006 on 2008-11-23
> **smooth3006 said:**
> does anybody know if the ndiswrapper method is a better way to go with x64 & madwifi ?

anybody ?, i need to know by this week.

---

### Post by smooth3006 on 2008-11-23
> **bumanie said:**
> Apparently that card can be enabled by loading [backports]("http://backports.ubuntuforums.com/showthread.php?t=969225") - I actually did it by using ndiswrapper on 32bit.

will that method work with hardy (8.04) as well ? i keep hearing about using atk5k instead of madwifi.

---

### Post by acreech on 2008-12-08
> **smooth3006 said:**
> will that method work with hardy (8.04) as well ? i keep hearing about using atk5k instead of madwifi.

This is what works for me......

[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

---

