---
title: "Creating Dual-boot system"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by jnedenrod on 2013-03-17
I'm trying to create a dual boot system. I'm going to make a 20 GB NTFS partition for Win8 and a 6 GB ext4 partiion for Ubuntu. The remaining partition is to be shared between the two OS's. Can I make the third NTFS or is Ubuntu only able to reat files from FAT file systems?

Also, if I'm messing anything else up, let me know! :)

---

### Post by jnedenrod on 2013-03-17
I'm also confused with gparted... Can all three be primary partitions? What's the purpose of primary partitions and extended partitions?

---

### Post by ibjsb4 on 2013-03-17
[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+dual+boot&sa=Search&cof=FORID:9"]
Dual boot
[/URL][http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+dual+boot&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+dual+boot&sa=Search&cof=FORID:9)

Partitioning
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+partition&sa=Search&cof=FORID:9)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Setting up a data partition
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi&sa=Search&cof=FORID:9)

UEFI (if you got it)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-03-17
For shared data with Windows & Linux use NTFS.

 FAT does not save files over 4GB, and does not have journaling, so chkdsk may not recover from damage or will take very long. FAT is ok for small devices like smaller USB flash drives.

Windows has to boot from one of the four primary partitions sda1 thru sda4. But one primary partition can become an extended partition which then can have many logical partitions. Linux boots from logicals just fine. Windows also reads logicals also and a second install of Windows can be in a logical, but all its boot files are really in the primary of the first install. 

 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
ht[URL="https://help.ubuntu.com/community/WindowsDualBoot"]tps://help.ubuntu.com/community/WindowsDualBoot
[/URL]
 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

 [URL="http://www.psychocats.net/ubuntu/installseparatehome"]http://www.psychocats.net/ubuntu/installseparatehome
[/URL][URL="https://help.ubuntu.com/community/SwapFaq"]https://help.ubuntu.com/community/SwapFaq
[/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

