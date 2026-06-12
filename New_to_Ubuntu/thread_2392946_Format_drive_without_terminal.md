---
title: "Format drive without terminal"
date: 2018-05-27
forum: New to Ubuntu
---

### Post by eldarraz on 2018-05-27
I want to format my HDD to NTFS to install windows, but dev/sda1 is failing to unmount because "device is busy". However, when I try to open terminal and force an unmount it flashes open and immediately closes, same thing with UXterm and Xterm. The tty screens do the same thing, after login something flashes and it returns to the enter username screen. Is there anyway to format the HDD with recovery mode in Grub, which seems to be the only place I can actually run commands?

---

### Post by yancek on 2018-05-27
> [COLOR=#111111][FONT=Ubuntu]I want to format my HDD to NTFS to install windows,[/FONT][/COLOR]

Windows  will do that during the installation and you can use the Custom installation option to select unallocated space to do it.  So the question is, what is on sda1?  If you have Ubuntu installed (you are posting at an Ubuntu forum) then is that it's root partition or do you have an EFI system.  Use a Live DVD or flash drive to shrink a partition to make room on which to install windows.  Can't really give you any more advice as your question is too general.  Do you have another OS currently installed?  What is it?  How many hard drives do you have?  How many partitions?  What filesystem on each?  What is your end goal?  If you want to simply install windows and overwrite whatever you might currently have , just boot the DVD and install.  If you want to do something else, explain what you want.  You would be better off formatting a partition with a windows filesystem from windows, either the installation media or an installed system if you have one.  Better advice on installing windows will be had a t a windows forum or a microsoft site.

---

### Post by SL0ltMJGyh on 2018-05-27
Is Linux installed to /dev/sda1? because if you try to format the disk your OS is running on the formatting operation is going to fail. You have to boot into the Ubuntu installer or other live media to format your disk.

---

### Post by eldarraz on 2018-05-28
My machine has only Ubuntu, running from a single TB HDD with three partitions. One of them is the main one with ubuntu on it (Ext4 983Gb, dev/sda1), another is a 17Gb Extended partition (dev/sda2) and another is NTFS (also 17Gb, not enough space for windows). My end goal is installing Windows, but the first partition can't have windows as the Winstaller requires NTFS. Would Windows forums have more knowledge of dealing with Ext4 partitions and installing windows onto them? I assumed since the PC only has windows, they'd advise to post on these forums. Is there any way to split up my first partition and create enough space for Win (34Gb) and format that to NTFS?

---

### Post by yancek on 2018-05-28
A default install of windows will not understand an ext4 formatted partition and will not read/write to it unless you install third party software.  You will not be able to install windows to an ext4 filesystem. Since you are planning to use only windows, the installer should overwrite everything.  Have you attempted to install windows and come up with an error due to the ext4 partition?  If you want to keep Ubuntu or the ext4 partition, windows has a Custom install option and you can select partitions or unallocated space on which to install it.    You can use Ubuntu or and LIve Linux system to delete the Ubuntu partition if you do not want it and do not have any data on it.  The Ubuntu (as well as a number of other Linux systems) will have GParted on it which is a graphical partition manager and you can use it to delete and/or format the current Ubuntu partition.

---

### Post by bijayalaxmi1808 on 2018-05-30
> **eldarraz said:**
> My machine has only Ubuntu, running from a single TB HDD with three partitions.
...
Is there any way to split up my first partition and create enough space for Win (34Gb) and format that to NTFS?

You can use an Ubuntu Live Disk and shrink the /dev/sda1 partition using gpart application. (probably, you need to find a guide on this how to do this)
Make sure to shrink enough space so that you can install Windows on it.

You just need to shrink the volume using the Live Disk and don't create any file system on that free space.

Now boot to Windows installer disk and you will see this free space (unallocated space) that you created by shrinking the /dev/sda1.
There you create a new NTFS file system and install Windows.

---

