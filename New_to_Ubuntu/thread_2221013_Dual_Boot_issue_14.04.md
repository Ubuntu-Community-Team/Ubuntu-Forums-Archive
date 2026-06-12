---
title: "Dual Boot issue 14.04"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by Anthony_Ratcliffe on 2014-04-30
Hello,

I have Windows 8 with I think is UEFI and i'm trying to dual boot, the other times I have done this, i had windows on the drive I put in the Ubunut USB and was given the option to install along side, however this is now there anymore. So i made some room on the drive with Gparted and made a a partition and installed it too, however it is not showing grub as the boot loader. I tried BCDeasy however it cannot boot to the ubuntu partition. Can anyone tell me the right way to do it with 14.04 and windows 8.1

---

### Post by LastDino on 2014-04-30
Have you tried turning off UEFI to legacy?

---

### Post by oldrocker99 on 2014-04-30
UEFI is the latest method that Micro$oft uses to enforce their inferior OS being on every PC in existence.

---

### Post by oldfred on 2014-04-30
Does Windows still boot?
Always best to use Windows to shrink the NTFS partition and immediately reboot so it can run chkdsk. Grub really only boots working Windows and with Windows now you need to have a separate Windows repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

You must turn off fast boot or always on hibernation.
and usually better to turn off secure boot, but Ubuntu will install with secure boot on.

What computer & model is this and what video card/chip?

Post link to BootInfo report from this:
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

More info in link in my signature.

---

