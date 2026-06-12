---
title: "[SOLVED] Windows XP / Linux Dual boot problems"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Red Rebel on 2008-06-17
I need to keep a laptop that has Windows XP and Linux running on it at the same time. I tried to achieve this twice now, and the end result has been the same, failure. The first time I tried this, was under the following scenario: With The original Windows Xp installation in place, I loaded the Ubuntu 8.04 Cd to start the installation. Ubuntu does its thing, until it gets to the partitioning. It recognizes that Windows XP is installed and gives me the option to select the partition sizes. I chose 2/3s for Windows XP  and 1/3rd for Ubuntu. Then it asked me if I wanted to import some settings from windows to ubuntu, (which I appreciated), I selected my settings, and let the installation finish. When I restarted I saw what I expected to see, GRUB boot loader giving me the option to load the operating system of my choice, I chose Windows XP. It starts loading to the point where I see the Windows XP logo, and then, all of a sudden, this blue screen flashes, and it restarts the machine. The Ubuntu install works fine and loads every time. I tried this again under a different Windows XP installation, and the end result was the same. Why is it that Windows Starts to boot, and then the computer all of a sudden Restarts?  I was told that I should install Windows first, and then Linux after. Is this true? If anyone has ever accomplished this, can you share exactly how you did it or possibly refer me to a wiki or something. Any help would be greatly appreciated....

---

### Post by steve101101 on 2008-06-17
install ubuntu within windows

---

### Post by steve101101 on 2008-06-17
this will give you the enhancements of having a dual boot system, but it sets up everything automatically. Just pop the cd while in windos and click install within windows. That what i have done twice. It works great.

---

### Post by Happy_Man on 2008-06-17
This sounds like a Windows problem, try holding F8 down as you boot Windows to get into Safe Mode, and see if that works.

---

### Post by Red Rebel on 2008-06-19
I appreciate the information, however, I would prefer to keep windows Xp and Ubuntu on two seperate partitions. Here is a link to another user that is having the same problem:

[http://ubuntuforums.org/archive/index.php/t-504625.html](http://ubuntuforums.org/archive/index.php/t-504625.html)


and I have heard of other people having the same issues, so far with no solution. Windows just restarts. Any help would be greatly appreciated....

---

### Post by stchman on 2008-06-19
> **Red Rebel said:**
> I need to keep a laptop that has Windows XP and Linux running on it at the same time. I tried to achieve this twice now, and the end result has been the same, failure. The first time I tried this, was under the following scenario: With The original Windows Xp installation in place, I loaded the Ubuntu 8.04 Cd to start the installation. Ubuntu does its thing, until it gets to the partitioning. It recognizes that Windows XP is installed and gives me the option to select the partition sizes. I chose 2/3s for Windows XP  and 1/3rd for Ubuntu. Then it asked me if I wanted to import some settings from windows to ubuntu, (which I appreciated), I selected my settings, and let the installation finish. When I restarted I saw what I expected to see, GRUB boot loader giving me the option to load the operating system of my choice, I chose Windows XP. It starts loading to the point where I see the Windows XP logo, and then, all of a sudden, this blue screen flashes, and it restarts the machine. The Ubuntu install works fine and loads every time. I tried this again under a different Windows XP installation, and the end result was the same. Why is it that Windows Starts to boot, and then the computer all of a sudden Restarts?  I was told that I should install Windows first, and then Linux after. Is this true? If anyone has ever accomplished this, can you share exactly how you did it or possibly refer me to a wiki or something. Any help would be greatly appreciated....

Problem is that most new laptops have Vista and they do not provide drivers for XP.

Forst thing you need to do when you want to dual boot a laptop with XP is to perform a defrag and a chkdsk /f on all NTFS partitions.

Once that is done you will want to create some free space using the partition resizer of your choice.  The Ubuntu LiveCD contains  gparted and it can do this for you.

When you install Ubuntu tell it to use the largest continuous free space.  This method has always worked for me.

---

### Post by jbaerbock on 2008-06-19
With me after installing Kubuntu and starting XP is wants to scan my disks (apparently it finds Kubuntu to be a disk corruption lol). So I let it scan em once and it is then happy. Maybe something is messed up with that process on ur xp install? At that point it wouldn't be a grub error but a winxp starting error.

---

### Post by Duck2006 on 2008-06-19
Do you have a recovery partition for windoze on your hard drive.

---

### Post by bumanie on 2008-06-19
Sounds as though your windows mbr may be corrupted. You may have to boot with the windows cd and go into recovery console and do a fixboot and a fixmbr. Then you will have to boot with the ubuntu live cd and reinstall grub. I agree, that a separate partition is uperior to a wubi install, if you plan to use ubuntu much of the time.

---

### Post by Zenze on 2008-06-19
I have set up duel boot XP and ubuntu many times and have had no problems so far. Each time I had windows installed first taking up the entire hard drive. Then I just run the LiveCD and when it gets to partition editor I just select manual. Then I just resize the windows partition to the size I want it. Then just make a ext3 partition and a swap partition. I always kept the default setting that it had when I made the partitions and just selected "/" as the mount point for the ext3. Then when I boot back into XP for the first time after the resize it runs a disk check and everything is ok.

It may be the your windows partitions have been very fragmented when you resized it, I have heard of this causing problems.

---

### Post by Duck2006 on 2008-06-19
> I agree, that a separate partition is uperior to a wubi install, if you plan to use ubuntu much of the time

Also it will run faster.

---

### Post by Red Rebel on 2008-06-19
Thanks for the input guys, I will try out some of your ideas and let you know. I am going to try installing windows xp from scratch, then degfrag the drive, then I will load the live cd, ubuntu 8.04, and do a manual install, resize the windows partition, and then create an ext3 and a swap partition, after that, I will set up / as mount point. I will let you guys know how this worked. thanks again...

---

### Post by bumanie on 2008-06-19
Assuming you have space it is a good idea to have an 8-10 gb / a 1-2 gb swap and the rest of the available space can be the separate /home partition. Good luck.

---

### Post by ferperezd on 2008-06-19
Hello guys, I have installed the tree of them.. XP and VISTA as well as Unbuntu. Had no problems. When booting it goes first to the GRUB boot loader and there you can choose if you wanna use Ubuntu o Windows loader, then if you choose windows, it will take you to another boot loader where it shows only Vista or XP. I had to install on Vista an app to manage the boot load. That works just perfect. The only problem is that my little bro always forgets to choose windows and has to reboot.... :lolflag:

---

### Post by Red Rebel on 2008-06-20
Well, I finally had success. I did exactly what ZenZe said to do and it worked for me. 

First, I installed Windows XP. Then I inserted the live cd. When it got to the partition section, I selected manual, downsized the Windows partition, and created an ext3 partition as well as a swap file partition. I have a dual boot system.... thanks very much for the info guys....

---

