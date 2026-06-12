---
title: "Installation does not work"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Discospawn on 2008-07-31
Hi!
I've installed Ubuntu 8 64 bit, first time as main O/S.
Somehow everything went well til I needed my second hdd. It didn't show up so I followed this guide [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) . And when I restarted my computer I couldn't get into ubuntu. It all freezes when it verifies my data pool.
The only thing I can think of doing wrong was when I formatted the partition, and I typed the logical name. And I wrote something in fstab.
The weird about this is that I can run iso from my usb and I can find both my hdds and enter them.
So what to do? clean both disks and start all over?  I can reach all the installed files on the first disk, but dunno how much I can do with my live guest pass.

---

### Post by rockerphil on 2008-07-31
i'd personally try first pulling the secondary drive you installed and try booting the machine, if at all possible try to get in to recovery mode, this can usually be achieved by pressing Esc upon boot, usually you have about 3 seconds to do so, taking you to the GRUB boot loader. let that do it's thing and let it repair the X server. if this works then all is well. and typically i try mounting a secondary hard drive manually through the terminal first time around to see if there's any issues that need to be sorted, hope the infromation helps,

Phil

edit: also, if that doesn't work you may need to reinstall. i personally (no expert here) can't think of anything else that might be done, but i'm sure someone else here on the forums might be able to help

---

### Post by Discospawn on 2008-07-31
I can only start ubuntu from my usb. And that's live version. Any tip how I can clean the hdd from liveubuntu? or do I have to put it into another computer?

---

### Post by rockerphil on 2008-07-31
well if all you can do is run in live mode then the only thing i can suggest is a clean reinstall, and possibly use the Gparted utility on the Live CD to completely reformat your second hard drive, bit of a tip here, i'd personally format your 2nd HDD to an ext3 format. Linux is able to deal with NTFS partitions, but it plays a lot nicer with ext2/ext3, hope it helps,

Phil

---

