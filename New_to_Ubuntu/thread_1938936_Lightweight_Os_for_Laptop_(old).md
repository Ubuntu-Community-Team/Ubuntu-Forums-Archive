---
title: "Lightweight Os for Laptop (old)??"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-03-10
I have a Acer Travelmate 230 with a
Intel® Mobile Celeron® processor with 256 KB L2 cache that I ran Puppy linux on years ago. But even the new versions of it are loaded with the new Xorg which will not load. This computer does not have a hard drive in it.

I have spent days trying to find a linux distro that will boot from USB and can run on it with 256MB of memory. Does anyone have a recomendation?? I did get Wary Puppy to load, but it could not connect to a WPA2 wireless network...

---

### Post by arochester on 2012-03-10
"antiX works on computers with as little as 64 MB RAM, though 128MB RAM is the recommended minimum and the 486 kernel version should work on AMD K5/k6. antiX is fast and has low RAM usage running live or installed." - [http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by bkratz on 2012-03-10
> **theducksfan2010 said:**
> I have a Acer Travelmate 230 with a
Intel® Mobile Celeron® processor with 256 KB L2 cache that I ran Puppy linux on years ago. But even the new versions of it are loaded with the new Xorg which will not load. This computer does not have a hard drive in it.

I have spent days trying to find a linux distro that will boot from USB and can run on it with 256MB of memory. Does anyone have a recomendation?? I did get Wary Puppy to load, but it could not connect to a WPA2 wireless network...



Bodhi may be a very good choice for you. See the system requirements here

[http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)

---

### Post by I2k4 on 2012-03-10
Maybe this article will give you some more leads, some of the suggestions are on my fun to-try list:

[http://maketecheasier.com/best-lightweight-linux-distribution-for-older-computers/2012/02/17](http://maketecheasier.com/best-lightweight-linux-distribution-for-older-computers/2012/02/17)

---

### Post by theducksfan2010 on 2012-03-10
AntiX vs Bodhi? Anything to recommend one over the other?

---

### Post by bkratz on 2012-03-10
> **theducksfan2010 said:**
> AntiX vs Bodhi? Anything to recommend one over the other?



The E17 desktop!

---

### Post by theducksfan2010 on 2012-03-10
> **bkratz said:**
> The E17 desktop!

E17 is in Bodhi?

---

### Post by theducksfan2010 on 2012-03-10
Bodhi 1.3.0 is the current release from Bodhi, but the Universal USB installer 1.8.8.7 only allows for bodhi_1.0.0.iso to use for bootable USB. How do I get the 1.3.0 .iso I downloaded to load as a bootable USB?

---

### Post by bkratz on 2012-03-10
> **theducksfan2010 said:**
> E17 is in Bodhi?

Yes, see here

[http://www.bodhilinux.com/e17guide/e17guideEN/intro.html](http://www.bodhilinux.com/e17guide/e17guideEN/intro.html)

---

### Post by bkratz on 2012-03-10
> **theducksfan2010 said:**
> Bodhi 1.3.0 is the current release from Bodhi, but the Universal USB installer 1.8.8.7 only allows for bodhi_1.0.0.iso to use for bootable USB. How do I get the 1.3.0 .iso I downloaded to load as a bootable USB?

Please see my response to your other posting in the other thread

[http://ubuntuforums.org/showthread.php?t=1937848&page=2](http://ubuntuforums.org/showthread.php?t=1937848&page=2)

---

### Post by sidzen on 2012-03-10
antiX support forum is tops; if new do a Full install, if intermediate use a Base install.  Post-install, run the [*smxi*]("http://smxi.org/") script to tweak it -- easy!

---

### Post by theducksfan2010 on 2012-03-10
Doing a UNetbootin install to USB drive of Bodhi. If there is anything missing or incompatible, slow with this I will give AntiX a try.

---

### Post by theducksfan2010 on 2012-03-10
bkratz, I installed Bodhi from the USB drive onto a external hard drive, it boots up on this laptop, but the one I am trying to bring back to life says no operating system found. Any ideas on how to get anything to install on a external hd or USB on the old laptop and actually boot up, not just inststall the .iso on a usb drive that will not be actually installed as a OS.

---

### Post by bkratz on 2012-03-10
> **theducksfan2010 said:**
> bkratz, I installed Bodhi from the USB drive onto a external hard drive, it boots up on this laptop, but the one I am trying to bring back to life says no operating system found. Any ideas on how to get anything to install on a external hd or USB on the old laptop and actually boot up, not just inststall the .iso on a usb drive that will not be actually installed as a OS.


Does you laptop allow you to boot from another device (usb) in the bios?

---

### Post by theducksfan2010 on 2012-03-10
CD-ROM, Hard Drive, +Removable Devices (Legacy Floppy Drives).

BUT, YES it will boot off of USB. I booted the Bodhi loaded with UNetbootin, but that just loads the .iso on the USB, it does not load a bootable functioning OS.

I'm trying to do ZenWalk using Universal USB installer as we speak, I'm trying tons of distro .ISO's and ways of loading but no success in booting up. The only thing that worked so far was the new Wary Puppy linux, but it would not connect wirelessly. The other new distros of Puppy use the new Xorg which this old laptop can't handle.

---

### Post by theducksfan2010 on 2012-03-10
The ZenWalk USB load results in:

SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:

---

