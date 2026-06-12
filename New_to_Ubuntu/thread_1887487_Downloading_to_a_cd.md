---
title: "Downloading to a cd"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by 1200max on 2011-11-27
Noobie here.
I want to try Ubuntu from a cd on Windows 7.
When I click on the start download button on the try it from a cd or usb stick it comes up with a box asking what Firefox should do with this file - open with Nero Express or save file.
Should I open the file or save it?

---

### Post by coffeecat on 2011-11-27
Download the file and save it. Then burn it to CD as an image using your favourite burning software. More here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You then set the BIOS of your machine to boot from CD first (if it is not already thus set) and boot up from the CD. You don't run the CD from Windows.

**EDIT**: since you have Windows7, you don't need Nero to burn the ISO file to CD. That can be done from Windows itself. See the link I posted.

---

### Post by 1200max on 2011-11-27
Thanks for the advice.

---

### Post by Megaptera on 2011-11-27
... and don't forget to use the 'try' option not 'install' unless that's really what you want to do!

---

### Post by 1200max on 2011-11-27
Just finished downloading onto the disc.  Have got a few bits to do on Windows and then I'll give Ubuntu a try!!

---

### Post by Mark Phelps on 2011-11-27
If you decide afterward that you want to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

