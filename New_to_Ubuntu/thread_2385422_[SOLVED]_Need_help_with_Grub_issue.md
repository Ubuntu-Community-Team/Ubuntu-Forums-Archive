---
title: "[SOLVED] Need help with Grub issue"
date: 2018-02-20
forum: New to Ubuntu
---

### Post by carrola7 on 2018-02-20
Hi all!


I installed Ubuntu 16.04 on a USB that I had been happily using for a number of months. I then started to run out of memory due to the way I had partitioned 
the USB. After trying and failing to re-partition the USB I just reformatted it and reinstalled Ubuntu. I was then unable to boot from the USB (some issue with 
Grub not installing properly) so I manually installed Grub.

Hardware: Lenovo Thinkpad X1 running Windows 7

When I boot up my laptop I see the following screen

[https://ubuntuforums.org/attachment.php?attachmentid=278596&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=278596&stc=1)



From there I can happily boot to either Ubuntu or Windows.


The problem is when I start up the laptop without the USB connected. Then I see the following screen:

[https://ubuntuforums.org/attachment.php?attachmentid=278597&d=1519121679](https://ubuntuforums.org/attachment.php?attachmentid=278597&d=1519121679)

I wonder does anybody know an easy fix for this and I'd love if you can briefly explain what is going on. I suspect that I have installed Grub on my laptop's 

hard drive rather than the USB.

Thanks.

---

### Post by oldfred on 2018-02-20
Grub defaults to installing to drive seen as sda, usually your internal drive.
During partitioning screen with Something Else is a combo box, and you need to change that to the same drive as you install Ubuntu.

You need to first reinstall grub boot loader to sdb. Make sure that works. Set BIOS to boot flash drive first & internal hard drive second. Then when external drive missing, it will boot internal drive.
Then install a Windows boot loader to sda.

You can use Boot-Repair or just install grub from inside your Ubuntu.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb 

Boot-Repair can install a generic Windows type boot loader or you can use your Windows repair flash drive to install the Windows boot loader.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by carrola7 on 2018-02-20
Thanks for taking the time oldfred.

I'm just wondering, seeing as Windows boots no problem when it is selected, does that mean the Windows boot loader is still/already installed or is grub booting Windows?

---

### Post by oldfred on 2018-02-20
Are you booting from UEFI, almost all Windows 7 systems are BIOS.
If BIOS you have one MBR per device.drive. So then you are booting Windows via grub. 
Normal Windows boot has its boot loader in MBR, and then more boot code in the Windows partition boot sector & in Windows.

Grub bypasses MBR and in-effect just jumps to Windows partition to boot Windows. Its just that if Windows is hibernated that will not work.
You always should have your Ubuntu live installer as a repair disk and your Windows installer or its own repair/recovery flash drive.
And keep them with current versions of installed systems, if you upgrade.

---

### Post by carrola7 on 2018-02-21
Yes I was booting from UEFI. I changed that to Legacy but it didn't make any difference.

I sudo grub installed on /dev/sdb without issue. Thanks for that. I don't suppose there's a similar command to uninstall grub from /dev/sda or did I actually erase the windows boot loader when I inadvertently installed grub?

---

### Post by oldfred on 2018-02-22
When you installed grub to sda, you erased the Windows boot loader.
You then just need to reinstall a Windows boot loader to sda.

You can use your Windows repair flash drive, boot repair or manually install Windows like boot loaders. 
In Ubuntu Universe are lilo & syslinux which work like the Windows boot loader in that they start boot process and look for partition with boot flag. 
Grub does not use boot flag.

---

### Post by carrola7 on 2018-03-19
So I finally plucked up the courage to try and repair the boot loader. It worked no problem .

I downloaded a copy of windows to a USB, then booted to that USB and from the command prompt did

```

bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd

```

Thanks you for your help oldfred. Much appreciated.

---

