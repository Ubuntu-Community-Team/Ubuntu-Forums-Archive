---
title: "Create/Delete Partitions using GNU GRUB 2.02"
date: 2016-12-23
forum: New to Ubuntu
---

### Post by Ismael_Fernandes on 2016-12-23
Hey folks,

Is any way to manage HDD partitions inside GRUB ?

I've messed up pretty bad, cannot boot manually to my usb in GRUB, windows bootloader got broken, Ubuntu also... And the only way to force to boot into my usb is remove any partition on my HDD, and that means remove grub also....

**THESE ARE 2 OF MANY POSSIBLE FIXES THAT I TRIED**

[I]grub> set root=(hd1)
grub> kernel /vmlinuz root=/dev/sda7 ro
grub> initrd /initrd.img
grub> boot
[/I]
**I've tried this code above, but "kernel" isn't known by GRUB, and I can't build it...**


[I]set root=(hd1,1)
chainloader +1
boot[/I]

**Also tried this tip, but "chainloader" sends "Invalid EFI file path" and when I specify the .efi file location it says "Filesystem is unknown"**



I forgot to say, my laptop is an ACER W510 (TABLET/PC), can't remove HDD, wich complicate things....

I know this seems confuse but, I'm gettimg mad and upset for "brick" my laptop and GRUB is the only tool I have for fix...

And sorry for my bad english, isn't my mother language!

Regards

---

### Post by oldfred on 2016-12-23
You need to boot live installer which has gparted or a gparted live flash drive in UEFI mode.

But if you left fast boot on in UEFI, that boots so fast you do not have time to press a key to get into UEFI to change boot order.
You usually can cold boot to get it to reset. Not warm reboot.
If laptop, you may have to remove battery.  And then hold power key down for 10 sec to drain all power. Then system should cold boot and give you just a few seconds to press correct key to get into UEFI/BIOS. Often f2 but varies by brand.

Fast Boot in UEFI assumes no system change, so all the system info/boot order/data from previous boot has not changed. UEFI/BIOS writes system hardware configuration to hard drive for operating system to know what you have. And assumption is you get to UEFI from Windows or grub menu, if not using a key.
Cod boot then has system go thru a full start up check of hardware & configuration which gives you a few seconds to press keys.

Some tablet type systems have a pin hole /reset/reboot on bottom of system, or your manual may have other instructions. 
Some desktops can only be totally reset by jumpering pins on motherboard.

---

### Post by Ismael_Fernandes on 2016-12-24
> **oldfred said:**
> You need to boot live installer which has gparted or a gparted live flash drive in UEFI mode.

But if you left fast boot on in UEFI, that boots so fast you do not have time to press a key to get into UEFI to change boot order.
You usually can cold boot to get it to reset. Not warm reboot.
If laptop, you may have to remove battery.  And then hold power key down for 10 sec to drain all power. Then system should cold boot and give you just a few seconds to press correct key to get into UEFI/BIOS. Often f2 but varies by brand.

Fast Boot in UEFI assumes no system change, so all the system info/boot order/data from previous boot has not changed. UEFI/BIOS writes system hardware configuration to hard drive for operating system to know what you have. And assumption is you get to UEFI from Windows or grub menu, if not using a key.
Cod boot then has system go thru a full start up check of hardware & configuration which gives you a few seconds to press keys.

Some tablet type systems have a pin hole /reset/reboot on bottom of system, or your manual may have other instructions. 
Some desktops can only be totally reset by jumpering pins on motherboard.


Thank you oldfred for the fast reply!! Gonna try GParted with my USB stick! Gonna leave the feedback soon :) Thanks once again!

---

### Post by Ismael_Fernandes on 2016-12-24
Unfortunately, it freezes when I try to boot up GParted Live.... So, no fix right... ?

---

### Post by oldfred on 2016-12-24
So does it start to boot from flash drive? 
Or do you have so much corruption or broken hard drive, so gparted cannot parse drive.

I do not know what boot parameters gparted ISO might need. It has always just worked for  me.

But what video card/chip do you have.
What brand/model system.

---

### Post by Ismael_Fernandes on 2016-12-24
> **oldfred said:**
> So does it start to boot from flash drive? 
Or do you have so much corruption or broken hard drive, so gparted cannot parse drive.

I do not know what boot parameters gparted ISO might need. It has always just worked for  me.

But what video card/chip do you have.
What brand/model system.

The PC boots to USB, I'm at the grub menu of gparted and whatever I choose to boot, it freezes... displays the background image of grub and it stays there without the grub menu...

The HDD is flash EMMC, as I said earlier its a Tablet PC, BIOS UEFI (it's CSM atm)

---

### Post by oldfred on 2016-12-24
This older thread mentions it has the 32 bit UEFI. Some vendors did that to make it Windows only as back then Linux did not have a 32 bit UEFI for 64 bit systems. Or it was intentionally crippled.
[https://ubuntuforums.org/showthread.php?t=2116227](https://ubuntuforums.org/showthread.php?t=2116227)

But Linux now has a 32 bit UEFI, but it is not standard in any distribution. You have to download the 32 bit boot files and add them in place of the standard 64 bit versions.

Some of these may mention have to compile your own, not now required as you can download files directly.
 [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 16.04 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

