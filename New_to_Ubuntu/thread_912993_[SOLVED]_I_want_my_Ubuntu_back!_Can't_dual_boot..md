---
title: "[SOLVED] I want my Ubuntu back! Can't dual boot."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jbruced on 2008-09-07
The quick story,

Installed new HD(150GB) on Dell 5150 laptop.
Installed Windows XP, left 50GB partition
Installed Ubuntu 8.04 from Live CD, chose to use all available free space.
Worked beautifully! 
Tweaked and prodded Ubuntu, until I screwed up some functionality.
Deleted Ubuntu partitions using gparted.
Reinstalled Ubuntu from LiveCD to get a clean install.

All I can get is grub error 18 while trying to boot.


I've since repaired XP boot with XP install/rescue cd, and using the fixmbr command, but it only boots straight to XP.


Tried reinstalling Ubuntu at least 20 times, 
in various ways, all resulting in grub error 18.

I've searched for weeks for something I can understand that will help, but to no avail.

Most posts say it has something to do with the disk size, or PC setup, but it was working before I deleted the partition, so I know my setup can work.

Any spare time for a noob who'll be eternally greatful for a solution to this problem?

---

### Post by bumanie on 2008-09-07
Boot live ubuntu cd and post the output of > sudo fdisk -lu

---

### Post by Sef on 2008-09-07
This is GRUB error 18:

>  Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Here's one [suggestion]("http://ubuntuforums.org/archive/index.php/t-346958.html").

---

### Post by egalvan on 2008-09-07
Some more reading....

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

And depending on the age of your computer, the following may be relevant...

quoted from the above page...

> Now, technology has also passed the 33.8 and 137 GB hard drive limits too, so bear these two in mind as well, when diagnosing error 18 faults.
The GRUB error 18 message could nowadays be referring to the 137 GB BIOS hard disk size limit. This occurs when a machine was made for an 80 or 120 GB hard disk, and someone fits a 137 GB+ hard disk in thier machine without checking if the BIOS supports it.
Windows XP will work okay because it is usually installed in the first part of the hard disk, so the average user is blissfully unaware of the situation until they maybe install Linux on the second half of their hard disk, past the BIOS limit and get GRUB error 18.



Further....

> ...apparently, an operating system that is partly inside the hard drive limit may boot for some time as long as the kernel happens to be located within the part of the disk that the BIOS can 'see'.
After an update, if a newer kernel  happens to be placed somewhere outside the limit, the operating system might suddenly become unable to boot (at least by the new kernel), and most users would find it difficult to understand the reason why not.
Here is a great explanation of how that might happen, also already linked to in the above link, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)

---

### Post by jbruced on 2008-09-07
Thank you to all!

I went the route that egalvan provided.

short version-

egalvan points out that 137gb is another potential boot barrier.
(if kernal beyond that point)

using rescue cd with gparted, I resized xp partition to 70gb
added a 30gb partition as ntfs, and made sure it was at the end of the disk.

This left unallocated space of 50gb within the 137gb space potential barrier.

Rebooted into xp to check if ok, it ran chkdsk automatically, then rebooted and rechecked xp, all ok with xp. 70gb c drive and a 30gb e drive.

Booted Ubuntu live CD, clicked on desktop install, chose to allow Ubuntu to use all contiguous unallocated space.

Rebooted when complete, and voila!, grub menu asking which operating system to boot!

Thanks to all.

Can someone let me know how to return the favor?
I can help research issues you're working on or whatever.

Regards,

---

### Post by egalvan on 2008-09-09
> **jbruced said:**
> Thank you to all!

Rebooted when complete, and voila!, grub menu asking which operating system to boot!


Glad to see your machine working.
Since I use a lot of older computer components, I tend to run into "obsolescence" issues.
Too big a drive, or too much RAM, can confuse older mobos & BIOS, 
and do a wonderful job of confusing MS products.
And we users are then also confused...

> 
Can someone let me know how to return the favor?
Regards,

Sure, keep using, studying and enjoying Linux and it's many flavors.
And even better, FORWARD THE FAVOR.
Help a newbie one day, and as far as I'm concerned,
that's PAID IN FULL.

:popcorn:

---

### Post by jbruced on 2008-09-10
Thanks again, and I want to let you know I'm serious about returning the favor.

Going right now to search for some issues I can help others with.

Feel free to keep in touch, and don't hesitate to ask for help researching any other issues you're working on. I could use a good mentor.
Regards

---

