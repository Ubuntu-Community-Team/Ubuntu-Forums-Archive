---
title: "[new]disk boot failure, insert system disk and press enter"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by Czar_Panganiban on 2015-12-27
Im new to using ubuntu and im using ubuntu 11.04 desktop edition. My PC was working well and then experienced a power cut. Right after the power goes back, whenever I try to open my PC it says "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". I have read and tried different solutions I found in the internet but none of them worked. I tried unplugging and plugging mu PSU, checked if the hard disk is receiving power. Cleaned my RAMs. Checked boot priority, even tried to reinstall the OS but none of them worked. So Im hoping to find solutions here. I wish someone can help me with this problem because I got too many important files in my system. Thanks in advance :D happy holidays

---

### Post by UltimateCat on 2015-12-28
Looking at this schedule Ubuntu 11.04 reached it's end of life for support.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I recommend downloading one of the current versions, burn it to CD/DVD and install that.

If the boot disk isn't being read it could be because the boot order isn't set to boot to CDROM first.
Try going into the BIOS and set the boot order priority to CDROM first save your changes in the BIOS and exit.
It should boot to the Live CD of Ubuntu.
Also while in your BIOS check and see if the BIOS's see's the CD/DVD?

If not the power outage may have shorted out your computer. (not sure)
You might need Boot Repair. Try going into Recovery Mode and access GRUB.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If your machine is a UEFI pc you will have to disable the secure boot in order to install your distro.

Maybe these threads will help:
[http://ubuntuforums.org/showthread.php?t=2072696](http://ubuntuforums.org/showthread.php?t=2072696)
[http://ubuntuforums.org/showthread.php?t=1740670](http://ubuntuforums.org/showthread.php?t=1740670)

> 
If your drive is in the process of self destructing, best to mount it read-only.

[http://www.tomshardware.com/forum/303459-31-ubuntu-disk-boot-failure-insert-system-disk](http://www.tomshardware.com/forum/303459-31-ubuntu-disk-boot-failure-insert-system-disk)

I hope the power outage didn't damage your HDD or your power supply.
HTH

---

### Post by leunam12 on 2015-12-28
You shouldn't be using 11.04. Download a recent version and burn on DVD or USB. Boot the live USB stick or DVD and let us know what happens, if you cannot boot from USB or DVD, please describe the problem that you are getting. It would also help if you give more information about your PC. Thanks.

---

### Post by gordintoronto on 2015-12-28
"I got too many important files in my system."

What approach do you use for backup?

---

### Post by grahammechanical on 2015-12-28
> "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

That could mean that the hard disk is no longer working. If you get that message it proves that the power supply is working; the CPU is working; the RAM is working and the motherboard is working because it has just completed its Power On System Tests (POST).

Your best hope is to run a Ubuntu live session and try to access that hard disk with the file manager and start saving your important data. You might want to think about creating another partition formatted as Ext4 and then start copying data over to it.

A Ubuntu live session (not an 11.04 disk) will have a utility on it called Disks. That can read a hard disk's SMART data and tell you something about the hard disk. Provided of course, that the hard disk is not too old to have SMART data.

We would need to see a screen shot of what Gparted sees on that hard disk. We can also do that from a Ubuntu live session. And a live session is what you have to work with now.

Regards.

---

