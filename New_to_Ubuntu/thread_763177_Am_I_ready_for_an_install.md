---
title: "Am I ready for an install?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by chogoria on 2008-04-22
Right, so I've read through all of the help files...

I'm waiting until Thursday so I can get Ubuntu 8.04. I'll have the iso file installed onto a CD which I then verify.

I've already got an 18Gb partition on my hard drive that I store my rarely used files on (am currently using Windows XP), but these have been moved onto my main Windows partition. All of the files that I would not want to lose have been backed up onto CDs.

I now insert the Ubuntu CD and run the installation process through Live Play and select the 18Gb partition.

Will it reformat this partition automatically for me once I've selected it and have I forgotten anything else? Also, as my disk is already partitioned, can anything go majorly wrong during the installation process?

---

### Post by st33med on 2008-04-22
You need to delete that partition. Ubuntu prefers ext3, a journaled FS, instead of FAT32 or NTFS. Also, the only thing is if you want to keep Windows, make sure there is no other empty space on the drive, else the Ubuntu Installer might get confused.

Best of Luck, and welcome to the wild wonderful world of Ubuntu.

---

### Post by GepettoBR on 2008-04-22
Actually, the installer will delete the partition for you. You just have to select it during installation - choose the "manual" partitioning option if you're installing via the LiveCD environment or the Alternative CD. If you plan to install from within Windows, using the new Wubi installer, it's even easier: just select the partition from a drop-down list.

Welcome to the wonderful world of GNU/Linux and Open-Source!

---

### Post by chogoria on 2008-04-22
> **GepettoBR said:**
> Actually, the installer will delete the partition for you. You just have to select it during installation - choose the "manual" partitioning option if you're installing via the LiveCD environment or the Alternative CD. If you plan to install from within Windows, using the new Wubi installer, it's even easier: just select the partition from a drop-down list.

Welcome to the wonderful world of GNU/Linux and Open-Source!

When you say the installer will delete the partition, do you mean simply overwrite it without it affecting my other partition (containing windows which i'd still like to hang on to for the time being)?

Would the Wubi installer be easier for me to do this with? I think I understand the LiveCD install process, but it's just the partitions I'm not sure on. I've got a 60Gb / 20Gb split. The 60Gb I don't want touched and the 20Gb is where I plan to install Ubuntu. Both partitions are currently using NTFS.

---

### Post by GepettoBR on 2008-04-22
Unless something goes wrong, your 60GB partition won't be touched. 

In the Live/Alternative install, just select the smaller one for your "/" directory. 

The Wubi will install Ubuntu from inside Windows. You can select which partition to install from by choosing the Windows drive letter (d:,e:, etc).

(either way, remember to make another partition for your swap - it should be as big as your RAM, but doesn't have to be bigger than 1GB)

The partition you select will be reformatted in ext3, and everything on it will be erased. The swap partition will also be erased. The other partitions shouldn't be affected.

Back in January, I installed Gutsy on my laptop using the Alternative CD, and my partition scheme was almost the same as yours. I backed up my data just in case, but nothing was lost or corrupted during the process.

---

### Post by legolas on 2008-04-22
You asked "Am I ready", and I noticed you didn't say you backed up your system...always a good thing to do before a new install.

---

### Post by chogoria on 2008-04-23
> **GepettoBR said:**
> Unless something goes wrong, your 60GB partition won't be touched. 

In the Live/Alternative install, just select the smaller one for your "/" directory. 

The Wubi will install Ubuntu from inside Windows. You can select which partition to install from by choosing the Windows drive letter (d:,e:, etc).

(either way, remember to make another partition for your swap - it should be as big as your RAM, but doesn't have to be bigger than 1GB)

The partition you select will be reformatted in ext3, and everything on it will be erased. The swap partition will also be erased. The other partitions shouldn't be affected.

Back in January, I installed Gutsy on my laptop using the Alternative CD, and my partition scheme was almost the same as yours. I backed up my data just in case, but nothing was lost or corrupted during the process.

So when I come to installing onto the 20Gb partition (D: ), I will need to select which option during the installation process?
First select the d: and then partition that into a 19Gb/1Gb split?

---

### Post by chogoria on 2008-04-23
> **legolas said:**
> You asked "Am I ready", and I noticed you didn't say you backed up your system...always a good thing to do before a new install.

I have backed up all of my important files from windows onto DVDs just in case.

---

### Post by ad_267 on 2008-04-23
During the install you should be able to select the partition you want and the installer will automatically create an ext3 partition and a swap partition.

This gives a walk through of exactly what the installer will be like. It may be a bit different with hardy but should be pretty much the same: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
This is also a good guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by chogoria on 2008-04-23
Okay, I've read through that help file a couple of times and think I've got it. I need to first select the 20Gb d: partition at the 'select a disk' page and then at the 'prepare disk space' screen, would I just select the top option to resize the disk into a 19Gb/1Gb split? OR would i need to select 'erase entire disk' or 'manually edit partition table'?

---

### Post by ad_267 on 2008-04-23
After looking at those pages myself I'm not sure you can select an individual partition for the installation using the "select a disk" option as this looks like it only shows the entire hard drive. The resize is used to resize an existing partition (eg one with windows) and put the ubuntu installation at the end.

You may want to create the swap partition yourself (this should be about as much as your ram, maybe 1 or 2GB) and choose the manual partitioning option. Then you just need to select the partition you want Ubuntu on to be mounted at / and formatted as ext3 and the swap partition to be formatted as a swap partition. The live CD contains gparted which can be used to resize and create partitions.

---

### Post by chogoria on 2008-04-23
As the new (tomorrow's 8.04) release comes with Wubi on the LiveCD, should I just install with that instead, as I have over 20gb of free space on my C: partition.

---

### Post by ad_267 on 2008-04-23
I would say do a proper install onto the separate partition rather than use wubi. With gparted it is very straightforward to create a swap partition and then when selecting the partitions manually during the installation you know exactly what's going to go where.

---

### Post by chogoria on 2008-04-23
So to clarify (sorry, just want to be absolutely sure) use gparted to create a 1Gb partition (as I have 1Gb of memory) which will be used as my swap partition, effectively E:.

Also if I use the graphical installer would I need to manually create the partition to be used for swap or would I create it during the installation process itself?

---

### Post by GepettoBR on 2008-04-23
> **chogoria said:**
> So to clarify (sorry, just want to be absolutely sure) use gparted to create a 1Gb partition (as I have 1Gb of memory) which will be used as my swap partition, effectively E:.

Also if I use the graphical installer would I need to manually create the partition to be used for swap or would I create it during the installation process itself?

You can create the swap during install, but the best option is to create it yourself using Gparted ("Partition Editor" on the LiveCD system menu). To do it in the install, just select "manually edit the partition table". Whichever way you do it, the process is quick, easy and straightforward.

Also, about the Wubi install, you'd stll be using the separate partition. The only advantage of using Wubi is that, should you decide to go back to only Windows, you can remove Ubuntu from Windows as if it were just another application. I reccomend the "traditional" ways.

---

### Post by chogoria on 2008-04-23
> **GepettoBR said:**
> You can create the swap during install, but the best option is to create it yourself using Gparted ("Partition Editor" on the LiveCD system menu). To do it in the install, just select "manually edit the partition table". Whichever way you do it, the process is quick, easy and straightforward.

Also, about the Wubi install, you'd stll be using the separate partition. The only advantage of using Wubi is that, should you decide to go back to only Windows, you can remove Ubuntu from Windows as if it were just another application. I reccomend the "traditional" ways.

I think I'm going to use wubi because it sounds like a lot less can go wrong for me. Do I need to make any adjustments at all to the 20Gb partition such as format or delete the partition? Please be specific as I am very new.

---

### Post by Martje_001 on 2008-04-23
If you download the image tomorrow, please download it with bittorrent. It saves the Ubuntu servers bandwidth.

---

### Post by ad_267 on 2008-04-23
As far as I know, no you don't need to format the partition. The installer creates a file on your windows partition and formats that file using ext3.

---

### Post by GepettoBR on 2008-04-23
> **ad_267 said:**
> As far as I know, no you don't need to format the partition. The installer creates a file on your windows partition and formats that file using ext3.
The Wubi installer can also use his 20GB partition, I think. I haven't used it myself, but from the screenshots I've seen online (just google "hardy wubi") you select a partition from a pulldown list.

---

### Post by chogoria on 2008-04-24
I've sorted out my installation problems now and am now running a dual boot with Hardy and XP. Both OS's work fine. Am now having major network connection problems in Ubuntu, but thats for a different thread!

Ps. I found this website [http://www.easy-ubuntu-linux.com/ubuntu-installation-606-1.html]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-1.html") very helpful as well. It is based on installing 6.06 but I found it a great help when working out how to correctly partition my hard drive and hopefully it will help others out too.

---

### Post by ad_267 on 2008-04-24
Good to hear it! Hope you get the networking problem sorted out.

---

