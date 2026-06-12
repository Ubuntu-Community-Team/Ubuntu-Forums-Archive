---
title: "Best way to image hard drive (acronis, ghost, etc)?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-11-09
Hi,

I bought a Dell Mini with Ubuntu on it.  I would like to make an image before I mess with anything on the system so I can try 8.10, dual boots, etc.  

I am familiar with Ghost & Acronis software which I use on Windows.

I am pretty sure I imaged a dual boot PC with Vista & Ubuntu in the past (I never restored it though).

I wanted to find out if either of those is a good solution.  

Thanks,
Rich

---

### Post by drs305 on 2008-11-09
One program you can use is partimage. You would run it from the LiveCd, gparted CD or a systemrescuecd if you wanted to make a copy of an installed system. It will make a complete copy of a partition but won't include unused space.

---

### Post by _sAm_ on 2008-11-09
Guide for partimage:; [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Or you could use Clonezilla, can be used from a USB stick [http://www.tectonic.co.za/?p=2291](http://www.tectonic.co.za/?p=2291) Clonezilla

---

### Post by Orographic on 2008-11-09
Sadly, using Acronis doesn't seem to be a good option anyore since the release of 8.10 as the installer formats differently and makes it problematic for Acronis to be used. 

Its a real shame as it was a fast and easy way to image drives, especially for those of us used to using Acronis on Microsoft systems. I'm a bit surprised Ubuntu has made it harder for newbies to try and backup their OS now. 

I can still easily restore Hardy via Acronis but not Intrepid...

---

### Post by Efros on 2008-11-09
I recently imaged a Panasonic toughbook W2K with gparted live CD and used that image to setup 3 further toughbooks. The toughbooks were ancient and each image write took about 5 hours via USB, which I suspect was 1.1. But all worked after the imaging.

---

### Post by gpsmikey on 2008-11-09
While not free, I have been very happy with the partitioning and imaging utilities from terabyteinc (Bing, Image 4 Linux etc).  Very reasonably priced, not bloated and they give very good support.  I gave up on Acronis several years ago after purchasing it and then an upgrade -- they never did fix the bugs that people were reporting, they just released a new version and wanted us to upgrade again to get the fixes (which then had new bugs).  Terabytes stuff is a bit on the "geeky" side which should fit right in with the linux bunch :) 

[http://www.terabyteinc.com](http://www.terabyteinc.com)  (no connection to them except through my visa card ! )

mikey

---

### Post by RichTJ99 on 2008-11-09
I tried Clonezilla & setup the USB boot disc, but the mini doesnt seem to load properly.  I dont know if its due to the processor or what.  I have the 8.04 on the mini now. I would like something that will work with 8.10 & windows as well.

---

