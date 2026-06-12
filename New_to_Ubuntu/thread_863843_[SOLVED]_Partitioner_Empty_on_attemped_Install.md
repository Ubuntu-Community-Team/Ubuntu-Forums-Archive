---
title: "[SOLVED] Partitioner Empty on attemped Install?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by The MAX on 2008-07-18
So I have two HDD's
a 500 gb seagate with a windows install and an extra ntfs partition
and a 250 gb seagate with currently no partition
both are sata2

Tried to install Ubuntu but when it got to the partitioner there were no drives or partitions listed in the window. Obviously can't install if I can't create a partition.

the Mobo is a Asus P5Q-Pro brand new, and it does have linux drivers available so I know its supported, but I guess the HDD's just aren't being detected by the live cd for whatever reason.

Any ideas?

---

### Post by HDave on 2008-07-18
I have found the paritioning tool inside the installer isn't always as good as the generic gparted tool.

Boot under the live CD, and run System->Preferences->Parittion Editor and see if that works better.

If that tool doesn't recognize your drives, then you need to go to the device manager and see if the kernel sees them.

---

### Post by The MAX on 2008-07-19
Changing the sata mode to ACPI instead of IDE seemed to work. But when I went to boot from grub it gave me an Error 17 for Linux and an Error 13 for windows.

The setup I have is 

/sda1 windowsxp
/sda2 ntfs

/sdb1 ext3
/sdb2 swap

those were the only partitions I have/made. I installed the boot loader on the second harddisk. (selected /sdb from the advanced menu)

Any ideas?

---

### Post by bumanie on 2008-07-19
From live cd post the output > sudo fdisk -l

---

### Post by The MAX on 2008-07-19
If I still have my sata in IDE configuration even after Linux has been installed fdisk -l gives me nothing.
In ACHI mode on the live CD the fdisk out puts this

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb7fdb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       60800   283579380    f  W95 Ext'd (LBA)
/dev/sda5           25497       60800   283579348+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfc9dfc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056   83  Linux
/dev/sdb2            7296        8268     7815622+  82  Linux swap / Solaris

```

Would the linux drive need to be the first drive as in sda or hd0?
At this print out it was set as the first drive in the bios but still being listed as the second.

---

### Post by bumanie on 2008-07-19
It is best to have windows as the first hard disk ie, sda viz (hd0) as you say. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) Go to this site and about 2/3 of the way down the page there is all the grub error codes listed with explanations of the code and likely fixes. Good luck, post back if nothing helps.
PS: It looks as though windows and ubuntu are both installed, it's a matter of sorting out grub.

---

### Post by The MAX on 2008-07-19
went to the Grub menu and after typing find /vmlinuz or whatever it said it was on hd0,0 which is wrong. 
SO grub has it screwed up where everything is but fdisk is right apparently.

Will keep reading to see if I can fix this.

---

### Post by The MAX on 2008-07-19
Okay so I went into the devices.map from the live cd and changed it to

hd1 /sda
hd0 /sdb

then went into menu.lst and changed all the linux boots to hd0,0 and windows to hd1,0

Linux then works, but windows will not boot from the grub. Just goes to a window that says "Starting Up" or something like that and hangs there. But booting from the other drive shows that the widows boot loader and sector are still fine.
Also if I switch back to sata config as IDE instead of AHCI then linux won't boot the Ubuntu boot screen just seems to go on for ever. 
Also windows won't boot with the sata in AHCI mode.

I'm going to DL a fresh version of ubuntu, this time the regular 32bit, even though I have an Intel E8400 core 2 duo which is 64 bit, I'll only be using it to ssh into high performance computer clusters mainly.
Maybe a fresh install and then changing the devices.map and menu.lst again will help.

Anyone have this problem of sata as IDE mode not working with linux before?

---

### Post by bumanie on 2008-07-19
Error 13 is indiscating a corrupt windows boot sector - reinstall the boot sector via recover console for xp (fixboot;fixmbr) or recovery disc for vista. Then to get get grub reinstalled correctly > sudo grub > root (hd1,0) > setup (hd0)>  quit and then reboot. Also change the drive map back to how it was. That should get the dual boot to work. I have done this many times with a similar setup and it has worked.

---

### Post by The MAX on 2008-07-19
Because this issue has changed a bit, I've started a new thread with a more appropriate title.

[http://ubuntuforums.org/showthread.php?p=5420539#post5420539]("http://ubuntuforums.org/showthread.php?p=5420539#post5420539")

---

### Post by The MAX on 2008-07-22
Anyway, anyone having similar issues Try setting the sata configuration in your bios from IDE to AHCI, that fixed my problem.

---

