---
title: "Problems installing Ubuntu Desktop 16.04.4"
date: 2018-04-18
forum: New to Ubuntu
---

### Post by thenatehawes on 2018-04-18
Hi all, new user here. Sorry for the epic long post here- I've tried tackling this issue for about 4 hours on my own.

I'm piecing together some old hardware for a small desktop PC and I want to load Ubuntu on it (no Windows dual boot Ubuntu only) and I've been running into lots of problems. I have the problematic combo of 1) Older (~2010) hardware w/ true BIOS not UEFI and 2) A true Hardware RAID 0 setup for my boot drive. I am 100% sure all the hardware works fine, most of the hardware was running in an old Windows box ~3 months ago.

I downloaded the 16.04.4 ISO from the Ubuntu website, then downloaded Rufus to make the USB bootable, I selected the "MBR partition scheme for BIOS or UEFI" setting when I made the bootable USB. I successfully was able to boot the computer off the USB. I attempted to install Ubuntu directly from the USB using the standard settings, but 80% through the installation I got a "Fatal Error" that it was unable to install Grub to dev/sda. It asks me to select a new partition to install Grub on, but there is some sort of bug which will not let me select any option (even the option to cancel the installation). I have tried selecting options both with mouse and with tab/enter on keyboard, neither allows me to get past this screen. Since I'm on a RAID setup dev/sda is not an option for me.

So after that failed I tried to install w/ manually configured partitions (using the option in the installer). I set up an Ext2 1000 MB partition and mounted to /boot, a 8500 MB partition for swap (8 GB of RAM), a 64 GB partition mounted to /, and finally the rest of the drive mounted to /home. I selected the 1000 MB "boot" partition for where to install Grub (perhaps this was my mistake?). The installation worked just fine, but Ubuntu would not boot, after the POST it just gave a black screen with a blinking cursor, I tried waiting a while, it doesn't help.

So finally I decided to "Try" Ubuntu using the USB stick. Ubuntu booted up nicely, and I opened a terminal and opened up gparted. I tried manually making all the partitions I just mentioned above (I was sure to check the boot flag for the /boot partition). I followed the instructions from [here]("https://fitzcarraldoblog.wordpress.com/2017/02/10/partitioning-hard-disk-drives-for-bios-mbr-bios-gpt-and-uefi-gpt-in-linux/") for the BIOS-MBR option 1. Then I started up the installation and chose to manually configure partitions. I mounted the partitions the same way, and selected the boot partition for Grub. The installation was again "successful" and when I booted from my RAID device I had a black screen that said something to the effect of Grub can't find Hd0. When I typed ls it returned no entries. I did notice when I was choosing how to mount things in the manual installation that all my partitions appeared doubled for some reason (i.e. the RAID0 array is 2*120 GB, and I saw ~480 GB of partitions on the list). I assumed the second set of partitions was just because of it being RAID 0, gparted only saw 1 set of partitions.

Anyway.. I'm pretty exhausted at this point. If I weren't so stubborn I would have probably given up and gone for a different distro/windows. I just want it to work that badly I guess. :)

PLEASE HALP!

---

### Post by oldfred on 2018-04-18
It used to be that Ubuntu desktop would not even see nor install to RAID drives. Then then updated it, but have not yet fixed the install of grub.

Back with 12.04 there was an alternative installer that did work. They discontinued it and said to use Server installer and if desktop desired you could just install that also.
Someone posted Lubuntu still has an alternative installer, do not know anything about it.

Have you tried Boot-Repair?
       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

RAID 0 is not recommended. It was for fast performance for systems just used to compile programs or run games, but all data would be on another system. Now SSD are much faster than rotating drives.
       
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by thenatehawes on 2018-04-18
Thanks for the help, you guys are extremely quick! I'll look into boot repair and post the summary report this evening. I will also read up on Ubuntu Server and may decide to install that instead if Desktop is too much of a headache.

I put the drives into RAID-0 simply because they're a pair of old small 120 GB SSDs and it's all I have available at the moment. I used RAID-0 simply to tie the drives together to make a "single" larger drive instead of splitting things across multiple drives. I am aware of the downsides of RAID-0, but this computer is really just used for a few small software projects (all cloud backup), browsing the internet, and playing the occasional steam game. I won't be heartbroken if I lose my install at some point in the future.

---

