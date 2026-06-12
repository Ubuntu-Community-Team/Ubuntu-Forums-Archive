---
title: "Trouble with Win7 Ubuntu Dual Boot"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by klundquist on 2013-12-17
Hi. I am trying to set up a dual boot system with Ubuntu 13.10 and Windows 7. I previously had Win7 installed on an NTFS partition, and I was planning to use the remainder of the drive to install ubuntu. I allowed the installer to unmount my windows partition, and then chose the option to install Ubuntu alongside Windows 7. After completing the installation and rebooting, Windows didn't appear in the GRUB options, it seems my NTFS partition has been converted to an Ext4 file system, and I am unable to locate my old files. Has anyone had a similar issue, or guess as to what the linux distribution may have done to my windows partition/files?

Thanks

---

### Post by jones quest on 2013-12-17
You can use gparted to scan your hard drive to see if your windows partition is still there.
If the installer has formatted and overwritten it then you might still be able to recover it.
I recommend system rescue cd for that. If the windows partition is there, the you can add it to the grub menu.
It's best to have a full backup, before you install any os...

---

### Post by klundquist on 2013-12-17
I have used gparted to view my partitions, but I don't think I can use it to recover the partitions. In fact, I had previously intstalled ubuntu on a separate Ext4 partition, and when ubuntu failed to recognize my Windows NTFS partition, I used a utility called testdisk to find and recover the lost windows partition. After the attempted recovery, ubuntu failed to load on reboot, and I was stuck with a grub rescue command prompt when I started my computer. This led me to reattempt the installation, this time allowing the installation to unmount my windows partition, and install alongside win7, which led me to the current situation.

---

### Post by jimmyh1972 on 2013-12-17
I advise you to boot with ubuntu live cd (or usb) to choose the option "try ubuntu" after it boot open the terminal and type
sudo fdisk -l  --- this will give you a summery of your HDD and its partitions.
if you will see something like /dev/sda yda yda yda ntfs --- this is part of your windows
now you can go into those partiotions (usualy mounted no /media) and try to copy them to external HDD
since your system is already a mess i advise you to install fresh copies of Windows & Ubuntu
To install dualboot first you have to install Windows than Ubuntu.
Instead of "alongside" its better to create EXT4 partiotion for Ubuntu install it there and install grub menu on the main HDD 
if you'r having troubles you can write to me in the private messges

---

