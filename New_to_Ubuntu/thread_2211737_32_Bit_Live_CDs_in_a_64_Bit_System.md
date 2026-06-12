---
title: "32 Bit Live CDs in a 64 Bit System"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-03-17
I just tried several 32 bit Ubuntu and Linux Live CDs made several years ago in a new Windows 7 64 bit computer and none worked.  Would that be expected?

Video was displayed on my screen during boot.  The system has a new Gigabyte motherboard with 8 GB memory.  I intend to download the latest version of Ubuntu and assume I should select the 64 bit version.


Each boot attempt with the different 32 bit Live CDs seemed to start out normally.  Some progressed farther than others.  OpenSUSE 11.0 made it to the desktop but the keyboard was not active.  Ubuntu, Knoppix, Fedora and Puppy Linux all failed earlier.

Thanks for any comments.

---

### Post by Impavidus on 2014-03-17
The 32 bit versus 64 bit is no problem. Worst case is that Ubuntu may not be able to use all memory. I think the problem is that the old live disk doesn't have the drivers for the hardware in the new computer.

Try a more recent version (12.04 LTS or 13.10). Use the 64 bit version.

---

### Post by KAWill70 on 2014-03-17
Thanks for the help.  The driver issue definitely makes sense. Those CDs were all created 2008-2010.

Now downloading 64 bit version of Ubuntu 13.10.

---

### Post by KAWill70 on 2014-03-18
Downloaded Lubuntu 13.10 instead so it would fit on a 700 MB CD.  Works great which I think confirms your thoughts on the driver problems with the Live CDs from 2008-2010.

Actually wanted to boot from USB Flash but this Win 7 computer has a new BIOS also usable with Win 8 and it currently only allows boot from CD or Hard Drive for security purposes.

I even tried to boot from USB with a simple boot manager on CD but it failed to hand the boot off to USB with no boot device found.  My Linux activities will probably move over to my WinXP computer a little later.

---

### Post by Vladlenin5000 on 2014-03-18
> **KAWill70 said:**
> Actually wanted to boot from USB Flash but this Win 7 computer has a new BIOS also usable with Win 8 and it currently only allows boot from CD or Hard Drive for security purposes.

No quite. It requires the USB to be booted the same way the already installed OS,ie, uEFI.

---

