---
title: "Attempting to install Ubuntu to dual boot Win 7"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Mythblstr on 2012-12-25
I chose the option to install Ubuntu 12.10 next to Win 7 and at the end of the installation I received the error message: "Executing grub install /dev/sda failed. This is a fatal error."
I have attached a .jpg of my hard drive configuration that has 4 hard drives with multiple partitions. The Win 7 system files are on the C drive. The D drive identified as XPPro has  Win XP and the Win 7 boot files on it. The partion next to XPPro that has 29.63GB is where  Ubuntu created a partition and installed it's files. 
Can anyone see why grub wasn't able to install?.
Help!:popcorn:

---

### Post by Mark Phelps on 2012-12-25
First of all, "C" and "D" aren't actually drives; instead, they are partitions resident on the same drive.  Why MS chose to misname them is unknown.

Second, GRUB tends to install to the "first" drive it sees, which in this case, is likely NOT the drive with the OSs on it.  Since that is your default boot drive, GRUB is most likely not where it needs to be.

---

### Post by DeezyFaReal on 2012-12-25
use debian-boot-repair-cd?
----> to fix boot

---

### Post by oldfred on 2012-12-26
With multiple drives & systems best to document system with BootInfo. Best not to let Boot-Repair install grub to all drives which it will offer but just to one drive and keep Windows boot loader in a Windows drive that you can also boot directly from BIOS with.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

