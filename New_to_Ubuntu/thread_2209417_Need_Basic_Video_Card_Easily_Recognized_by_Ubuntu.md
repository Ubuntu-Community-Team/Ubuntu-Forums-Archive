---
title: "Need Basic Video Card Easily Recognized by Ubuntu"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-03-05
I have not been able to run recent versions of Ubuntu because of the SIS 661 FX graphics used on my Motherboard.  I believe that SIS 630 compatibility is required.

Would plugging in a basic video card solve this problem?  Would I need to disable the SIS 661 FX first?  Video Card suggestions and any other comments would be a great help.

Thank you.

---

### Post by Frogs Hair on 2014-03-05
Determining what kind motherboard and PCI slot for a graphics card would be first on the list. [COLOR=#000000]SIS 630 compatibility is available on different boards . A graphics card would likely help, but mother board model is required to shop for a card. The link will provide ways to do that if  you have version of Ubuntu installed
[http://askubuntu.com/questions/179958/how-do-i-find-out-my-motherboard-model](http://askubuntu.com/questions/179958/how-do-i-find-out-my-motherboard-model)[/COLOR]

---

### Post by Vladlenin5000 on 2014-03-05
I would guess the graphics card has to be AGP. The boards based on that SiS chipset are all very old now. 
And indeed I remember having a not so good video experience with such onboard graphics, SiS being so "Windows only". Even some SD video files were hard to play satisfactorily back with Ubuntu 11.10, if I remember correctly. The last computer we had running such hardware (AsRock board) was decommissioned soon after.

---

### Post by KAWill70 on 2014-03-05
Thanks for both replies.  My Motherboard is a Gigabyte GA-8S661FXM-775 and it has an AGP card slot and three PCI slots.

The BIOS lets me select AGP or PCI for the entry labeled INIT DISPLAY FIRST.  Maybe either would work.  I wonder if an inexpensive PCI based AMD Radeon Video Card would work with Ubuntu.

---

### Post by Vladlenin5000 on 2014-03-05
An inexpensive nvidia AGP card, some with one of the latest chipsets released for AGP cards, will be easier and perform better than an AMD one, I suppose. 
The following cheap unbranded one should improve your experience noticeably but don't expect miracles (it won't be enough for HD video, probably): [http://dx.com/p/174341?Utm_rid=96781194&Utm_source=affiliate](http://dx.com/p/174341?Utm_rid=96781194&Utm_source=affiliate)

---

### Post by KAWill70 on 2014-03-06
Thanks for the help and link.

I checked my Motherboard manual and the AGP slot supports 4X and 8X with 1.5V device support.  The card keying apparently prevents an incompatible card from being inserted.  It does seem that AGP has an advantage over PCI in terms of bus contention.  I'll check the AGP card compatibility.  A PCI based Video Card may work as well and can be enabled in my BIOS.

I assume that Ubuntu locates the proper video card driver during boot although I have no idea how that is done.

---

### Post by jim Kane on 2014-03-06
I use a geforce 8500GS a basic card but works fine with *buntu

---

### Post by Vladlenin5000 on 2014-03-06
For better results I would prefer AGP over PCI (and, of course, PCI-e x16 over any other) and nVIDIA rather than ATI/AMD (the few ATI/AMD you can fit in that board are no longer supported by the newer proprietary drivers).

---

