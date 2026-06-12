---
title: "I want to install 64 bit on drive with 32 already loaded"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by phread59 on 2008-07-21
I have 32 bit Ubuntu on a 320 gig Sata drive.  I want to install 64 bit on the same drive.  I want to use both.  Any suggestions on how to add the 64 bit without screwing up the 32 bit install.  I have a working 64 bit live CD.  I'm using it now.  I do not want the 64 bit to write Grub onto the MBR.  I have a configured Grub set up already in place.

I'm sure I'll need the manual install option.  Just not sure how to go about it.  I cannot use Gparted from the 32 bit to repartition the drive for some reason.  Any help would be appreciated.  And if there is any suggestions on the syntax for adding the 64 bit into the 32 bit grub's list would be appreciated.  Thanks a bunch, I'll check back in tomorrow to answer any specific questions.  I gotta hit the hay and work tomorrow.

Mark Shuman

---

### Post by bodhi.zazen on 2008-07-21
If you want to keep the 32 bit install, resize the partition from the live CD.

You can not resize a mounted partition. You also very likely need to unmount the swap partition.

From there you have several options. Easiest is to install grub to the MBR. you can fix it post install very easily. If you do not want to do this, at the last step on the installer, where you confirm the install process, hit the advanced button and install grub to your new target (root) partition. You then will need to add an entry into the old /boot/grub/menu.lst to boot your new install.

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

