---
title: "Empty /boot folder when booting with grub2"
date: 2018-11-01
forum: New to Ubuntu
---

### Post by mr-mister on 2018-11-01
Hi there! I was trying to make some room for my / partition (where i also have my /home), so i booted from a live usb and used Gparted and moved that partition to use the new space. When i try to boot computer i find myself having to use grub2 to boot manually following [this guide]("https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux%20%20") . But when i want to load the kernel i find boot folder is empty! I have a partition for /boot but i do not know how to reach it
Here's the current state of my disk. /sda5 would be the partition i expanded (files were not accidentally erased)
```
Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   597GB   597GB   ntfs            Basic data partition          msftdata
 4      597GB   598GB   1049MB  ntfs                                          hidden, diag
 5      598GB   968GB   370GB   ext4
 6      968GB   968GB   210MB   ext4            /dev/sda0                     boot, esp
 7      968GB   977GB   8501MB  linux-swap(v1)
 8      978GB   1000GB  22.3GB  ntfs            Basic data partition          hidden, msftdata
```

---

### Post by yancek on 2018-11-01
Your post shows that you have 2 partitions labelled "boot, esp", in other words 2 EFI partitions on the same drive.  That is never a good idea.  You can sda1 and sda6, the 2 EFI partitions and take a look at them to see if you have the correct files.  You could also mount sda5 and see if you have a boot directory on the root partiton.  Unless you are using LVM, there aren't many situations in which having a separate boot partition is necessary, particularly with an EFI install.  Another option would be to go to the site below and download and run the boot repair script.  Use the 2nd option using the ppa and when you run boot repair using the instructions on their page, be sure to select ONLY the option to Create BootInfoSummary and do NOT try to make any repairs.  When boot repair finishes, it will give a paste bin link you can post here for members to view and make suggestions.  Read the instructions carefully before beginning.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

