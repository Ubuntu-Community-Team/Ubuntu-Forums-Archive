---
title: "Problem with Dual boot windows xp/ubuntu 8.10"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by icem237 on 2008-11-23
Ok I installed windows xp pro first , then installed ubuntu 8.10 . ubuntu works perfectly. 

Grub wont boot windows xp, it shows the option of windows xp but when executed it just says Starting up and never does anything.

**Here is my fdisk -l below:**

Disk /dev/sda: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x41487fae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7872     2015216    e  W95 FAT16 (LBA)

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a9e3161

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12372    99378058+   7  HPFS/NTFS
/dev/sdb2           12373       24792    99763650    5  Extended
/dev/sdb5           12373       24281    95659011   83  Linux
/dev/sdb6           24282       24792     4104576   82  Linux swap / Solaris

**And my menu.lst file below:**

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		78dac45a-8f7f-4e01-8406-76a4e5bf9b2f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78dac45a-8f7f-4e01-8406-76a4e5bf9b2f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		78dac45a-8f7f-4e01-8406-76a4e5bf9b2f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78dac45a-8f7f-4e01-8406-76a4e5bf9b2f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		78dac45a-8f7f-4e01-8406-76a4e5bf9b2f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Not sure what changes should be made. I know just enough to be dangerous with linux.

---

### Post by Bucky Ball on 2008-11-23
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
***root        (hd1,0)***
savedefault
makeactive
chainloader    +1
```Try the change I have highlighted in menu.lst. hd0,0 would be sda1. Your Windoze install appears to be on *sdb1 *(hd1,0)*. *What has me a bit puzzled is what exactly is on sda1, a 2Gb hard drive?

---

### Post by logos34 on 2008-11-23
I think the fact that you're seeing 'Starting up' message means there's something wrong with the boot sector code or it needs error checking. 

Try booting into the recovery console on the XP CD (press 'R') and at the prompt run

> fixboot

and

> chkdsk /r

---

### Post by icem237 on 2008-11-23
The 2GB partition is a USB thumb drive. Ill try your change.

---

### Post by icem237 on 2008-11-23
**I rebooted with the change of HD (1,0) and no change except an error 21. I rebooted again and this time without the thumb drive plugged in and ran fisk -l. Below are the results:**

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a9e3161

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12372    99378058+   7  HPFS/NTFS
/dev/sda2           12373       24792    99763650    5  Extended
/dev/sda5           12373       24281    95659011   83  Linux
/dev/sda6           24282       24792     4104576   82  Linux swap / Solaris

---

### Post by Bucky Ball on 2008-11-24
> **icem237 said:**
> The 2GB partition is a USB thumb drive. Ill try your change.
  Ahh! Take that out!

Okay, change the menu.lst back to what it was (hd0,0) and everything should be fine. *Then* insert the USB dongle. Phew. 

In your BIOS, it is checking the USB device as your boot disk and that is why you are getting the error (I would think). You can probably change that.

---

### Post by icem237 on 2008-11-24
I ran the chkdsk /r from the windows xp cd and it completed. Still no change just says Starting up and nothing.


I change the menu.lst back to HD(0,0). No change.

Im thinking the MBR is screwed or something for windows xp. I thought about using the Fixboot from the windows cd but im afraid that grub  will be taken out of the MBR. 

Kinda lost on this one. I Dont mind to reinstall windows but Id just like to know what the best course of action is .

---

### Post by Bucky Ball on 2008-11-24
Doesn't seem to be the mbr, if this is your problem.

[http://users.bigpond.net.au/hermanzone/p15.htm#WINDOWS_XP](http://users.bigpond.net.au/hermanzone/p15.htm#WINDOWS_XP)

Maybe you could try Testdisk inside Linux instead of FIXBOOT, instructions here:

[http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance](http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance)

---

### Post by caljohnsmith on 2008-11-24
Sometimes after resizing a Windows partition, the file system parameters in the Windows boot sector become slightly corrupted; if that happens to be your problem, fortunately "testdisk" can usually fix it. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows from Grub. :)

---

