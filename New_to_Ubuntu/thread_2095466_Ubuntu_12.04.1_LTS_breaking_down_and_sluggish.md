---
title: "Ubuntu 12.04.1 LTS breaking down and sluggish"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by ahamza on 2012-12-16
0     down vote          [favorite]("http://askubuntu.com/questions/229799/ubuntu-12-04-1-lts-breaking-down-and-sluggish#")            
                                     I am in the process of switching from Windows to a Linux  based system and am currently deciding between distributions...I am  currently trying Ubuntu as WUBI. I find that my experience is not very  smooth and streamlined for example, crash-reports, bugs, applications  taking time to run etc etc (this in spite of the fact that I am very  patient and am constantly researching solution to different driver and  application issues). Was wondering if this is because I am running  through NTFS right now or is it just like this? Looking to switch to  Linux because of its opensource nature, interest in software development  in college as well as maximizing the potential of my machine. I am  running an AMD quadcore-x64 2.2GHz, 6GB RAM and 750 GB HDD  on an HP G6  notebook. I would appreciate any honest opinions.

---

### Post by mastablasta on 2012-12-17
> **ahamza said:**
>  I am running an AMD quadcore-x64 2.2GHz, 6GB RAM and 750 GB HDD on an HP G6 notebook. 
 
these specs info are nearly useless. OS needs about 8 GB disk to run normally and have some free space left, 1GB RAM while it runs on any AMD/Intel architecture as well as some ARM. 
 
the important specs are left out though. GPU, Wi-fi etc.
 
as for your issues it's ahrd to say. 
did you install the correct graphics drivers?
did you check the ISO md5sum to make sure that downloaded image is exactlythe same as the one one the server?
were there any issues on windows prior to linux install? because wubi installs it "inside windows" in a virtual file.
did you try any other desktop environment (for example Kubutnu, Xubuntu...)? are crashes present there as well? Ubuntu 12.10 with Unity interface (and Gnome desktop) doesn't play nice on some maschines. an option is to try 12.04 LT S(long term support) version instead.

---

### Post by resander on 2012-12-17
Some months ago I installed Ubuntu 12.04 LTS on a 64-bit Dell Vostro-260 Dual-core 2x2.7GHz, 2gb ram, 500GB disk. The PC came preinstalled with Windows 7 and I added Ubuntu 12.04 LTS as a dual-boot. Ubuntu ran extremely well and my spec is about the same as hardware of the original poster. I have also installed Ubuntu 12.04 on a 32-bit desktop and 10.04 LTS Ubuntus on laptops all with lesser specs and never noticed any sluggishness.

As Mastablasta pointed out the sluggishness may be caused by running Ubuntu in Windows mode or by a bad install, so

-  download the latest version of Ubuntu 12.04.01 LTS and check the MD5 checksum before burning CD/DVD.
Also check the MD5 on the CD/DVD

-  boot up from the Live CD in 'try Ubuntu' mode and check it out

Running Ubuntu from the Live CD will sometimes be slower than a normal install, so you may be misled. Best to do a full Ubuntu install. If you don't need Windows let the install use all of the hard disk for Ubuntu. If not, you can install Ubuntu dual-boot, alongside Windows. The installer then finds the largest unallocated space and uses that for Ubuntu. The problem is that Windows quickly leaves the disk badly fragmented. Windows provides a disk defragmenter. I tried using that, but it did not produce enough unallocated space for Ubuntu. I don't use Windows much and wanted only about 40GB for it. I experimented but could never achieve this, so asked for help from the forum:   

[http://ubuntuforums.org/showthread.php?t=2061096](http://ubuntuforums.org/showthread.php?t=2061096)

OldFred and Jim Kyle in the thread above point out that chances of getting the the space you want for Ubuntu are best immediately following a fresh install of Windows before using it or installing programs onto it. Of course it is vital to backup all important files before installing or reinstalling an OS.

---

