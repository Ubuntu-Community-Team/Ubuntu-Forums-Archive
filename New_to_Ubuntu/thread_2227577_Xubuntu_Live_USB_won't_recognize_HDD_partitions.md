---
title: "Xubuntu Live USB won't recognize HDD partitions"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by hunter7 on 2014-06-02
I am very new to Ubuntu, but not so much to computers. I have a Windows 8 Toshiba laptop. My intention was to install Ubuntu in a partition I created on my hard drive. I created a bootable flash drive with the Xubuntu 14.04 ISO on it. When I booted to this, I chose not to install right away. Later, when I tried installing, it wouldn't recognize the partitions on my hard drive. Now, I am completely unable to boot to Windows 8, and as of yet, I cannot find any system restore options, as it won't boot to the Windows System Recovery menu. Any advice on what to do would be greatly appreciated.

---

### Post by Bucky Ball on 2014-06-02
Welcome. For starters, you can not create an EXT* partition with Windows so whatever you created with Windows (an NTFS or FAT partition) Ubuntu would not go on anyway. You need to leave free space/unallocated space and create the Ubuntu OS partition by either manually partitioning during install or letting Ubuntu install to the free space and create its own partition. 

As for Windows not booting, it would help if you could tell us how far you got with trying to install Ubuntu. With the information given, it is hard to see how Ubuntu has changed anything. 

I suggest you remove the Xubuntu USB dongle, reboot the machine and get into the BIOS to make sure you are booting from the hard drive (not USB) and try again. Main point: make sure that USB dongle is out when you reboot.

---

