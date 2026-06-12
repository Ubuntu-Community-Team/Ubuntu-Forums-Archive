---
title: "Attempted Windows/Ubuntu dual-boot. System will not boot."
date: 2014-10-17
forum: New to Ubuntu
---

### Post by Matthew_A_Shreve on 2014-10-17
I had an installation of Windows 7 all set to roll and attempted  to install a dual boot of Ubuntu 14.04 with Windows 7.  When running the install program from within Windows 7 I had first went into Disk management to shrink the main partition down to 50 Gb and then allowed the install to allow the machine to boot from the DVD.    Now all I have is a flashing cursor in the left hand corner and unable to boot to either  unless the Ubuntu disk is in the CD drive...  Attempted the boot repair using the "Recommended"  option and got the following URL when it failed:  [http://paste.ubuntu.com/8577329/](http://paste.ubuntu.com/8577329/)
Please assist.

Thank you

Matt S.

---

### Post by coffeecat on 2014-10-17
Welcome to the forum.

I've repaired the URL in your post - you'd accidentally removed some characters. It's now a hyperlink for the convenience of other members.

I have to tell you that you've managed to delete your Windows installation entirely. There are no Windows partitions at all. Somehow you opted for a full-disk LVM (logical volume management) installation, possibly with encryption. There is no boot loader installed in the MBR of your hard drive which is why it will not boot and you simply see a flashing cursor. I would guess that you are booting into the live session when you boot with a disc in the optical drive.

I would imagine that a full-disc LVM system with or without encryption is not what you want, so I'd guess it's not worth trying to install the grub bootloader. If you give more details of what you did during the installation process, what you wish to achieve, and whether or not you have backups of your Windows system, and/or a Windows installation medium, and members will be able to help you.

As soon as I've posted I'll edit your thread title to something more likely to attract help.

---

