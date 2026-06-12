---
title: "where to place the boot partition"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-11-18
so last night, when i tried to do a clean re-install of intrepid, i managed to corrupt grub by loading tgrub onto the wrong partition (this required a complete re-install of vista). b4 i attempt the ubuntu re-install again, i hav a few questions.
1) i have 4 partitions right now (a 10gb vista recovery, a 210gb vista main, swap, and a 10gb ext3 linux), what should i specify as the mount point for each partition when i am installing from the intrepid livecd?
2) which partition should i install GRUB onto?
thanks

---

### Post by kellemes on 2008-11-18
> **minibeardeath said:**
> so last night, when i tried to do a clean re-install of intrepid, i managed to corrupt grub by loading tgrub onto the wrong partition (this required a complete re-install of vista). b4 i attempt the ubuntu re-install again, i hav a few questions.
1) i have 4 partitions right now (a 10gb vista recovery, a 210gb vista main, swap, and a 10gb ext3 linux), what should i specify as the mount point for each partition when i am installing from the intrepid livecd?
2) which partition should i install GRUB onto?
thanks

Grub will install itself in MBR, the configuration files will be installed in /boot You may create a /boot-partition but there is no need to.
I understand you only have disk? In this case Grub should have no problem installing itself without further instructions.
You don't need to specify any mountpoints at all if you don't want to. If you want /home on it's own partition, you need to create a partition for it and create /home mountpoint for it.
But basically there are only 2 partitions you need.. swap and /(root).. these will be automagically created.

---

### Post by caljohnsmith on 2008-11-18
I agree with kellemes, you don't have to do anything special to have Grub installed to the MBR (Master Boot Record), which is where you want it unless you plan on using Vista's boot loader to boot Ubuntu. So bottom line, when you go through the installer, just don't click on the "advanced" button at the end of the installation process to change anything, and you should be fine. 

As far as mount points are concerned, just set your main Ubuntu partition with a mount point of "/" or root, and then the swap partition with a mount point of "swap", and you should be fine. Let us know how it goes. :)

---

