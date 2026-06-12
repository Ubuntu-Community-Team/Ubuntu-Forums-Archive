---
title: "Stuck on manual partitioning 12.04.3 Alternate"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by linuxperson on 2013-11-27
I can't believe how many threads I have read about this but I can't get it to do what I want.  I can install Pangolin L easily on a dedicated external drive or if I wanted to use the whole computer but that is not what I need.  I can't figure out how to manually partition my computer drive to do something that you guys will think is easy.  Here goes and remember I am just showing up here.  I have installed several flavors of Linux and enjoy them alot.  I want to install 12.04.3 L on a machine that has several fully encrypted windows partitions and a TrueCrypt bootloader.  I don't want to mess with them at all.  I have a usb flash formatted in Fat32 (wiped clean too) and I am going to use that to boot my Ubuntu system.  I do not want to change the bootloader/MBR from its current state.  I won't have to using the flash for access to Ubuntu.

Partitioning (I am stuck):  I have 35 Gig of unallocated free space at the end of the only one hard disk in the computer.  I want to use all that space for this Ubuntu system and I absolutely need to use DM Crypt and Luks to encrypt the system before/during install.  I have been running 12.04 for awhile now using an external drive and my machine runs perfectly with Ubuntu.  The drivers, mouse, etc... work better than Windows ever does.  Can someone please link me or give me a "connect the dots" list of partitioning steps for what I want?  I have spent alot of time on this and done several installs, all of which don't produce what I want.  I don't know why PARTITIONING is getting the better of me.  Part of the confusion is how to partition and at the same time prepare for DM/Luks too.  All of the guided partitioning options seem to assume you are dedicating a machine or entire device.  That is why the install on my external went so easily.  The manual approach is beating me up!

You guys don't know how much it pains me to ask for help on something I should be able to figure out.  One other thing that concerns me is how to make a duplicate usb flash to boot Ubuntu in case the original ever gets stolen/lost.  Suggestions there too?

---

### Post by DuckHook on 2013-11-27
Hi linuxperson,

Welcome to the forums even if your first exposure has to be under such stress.

Yours appears, at least to me, to be a very sensitive if not outright fragile install. In my experience, when a user mixes repartitioning with already encrypted partitions, what sounds like super-critical data, absolute need for privacy/descretion, etc. he us walking on eggshells. You've got *this* bear spooked at any rate. Are you sure you want to be monkeying around on a system this sensitive? Why not just stick with Ubuntu on the external and leave well-enough alone?

Before proceeding a step further make sure that you avert complete disaster by having current backups of all your data as well as your Windows install disks and license keys. I cannot emphasize this enough. Partitioning is the number one cause of hair-loss and premature aging on these forums.

Okay, now it's time for *oldfred* to step in. Ha-ha... 

More info is absolutely necessary before even oldfred can help you, especially:

1. your current partition scheme,
2. number of HDDs and how they are laid out,
3. whether you are partitioned w/ GPT or old DOS tables,
4. what version of Win it is,
5. whether you have secureboot and fastboot turned on,
6 is BIOS legacy or EFI.

You must provide answers for every one of these questions. If it is easier, post output of```
sudo parted -l
``````
df -h
```Also, if you can, tell us why encryption at install is so essential? The built-in encryption default in 12.04 is ecryptfs, not LUKS or DM Crypt. I am aware of whole-disk encryption options using ecryptfs (it' easy and you invoke it at initial install), but I have no experience with LUKS or DM Crypt.

In theory, it is not hard to boot from a flash drive and even to make backups, but let's get a better understanding first.

---

### Post by oldfred on 2013-11-27
oldfred has both the hair loss and ageing issues. But he tries to avoid encryption and LVM as they are a lot more complicated on the already somewhat difficult Linux install for a new user.

I think we have seen a user or two with either LVM or LVM with encryption erase entire drive. Not sure if installer issue or user selected the wrong defaults.

All I can offer is a few links.
 Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
[http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by linuxperson on 2013-11-27
Guys I appreciate the responses.  My system has one hard drive.  I have two encrypted windows partitions (TrueCrypt) and use the TC bootloader as my MBR.  I have a ONE disk setup aligned as old dos (not GPT).  My machine boots legacy and I have all the system disk boot files inside the C drive.  I re-did the drive from scratch and moved all boot files to inside the system disk to avoid pesky issues with TrueCrypt.  The machine works flawlessly in 7 Pro.  No issues of any kind.  I also have a third partition (200 Gig Fat32) and I resized it to have 35 Gig of unallocated at the drive end to create the Ubuntu system on.  I am completely at home with windows.  I have multiple backups including intelligent copy and several sector/partition images using Macrium Pro.  I can flawlessly restore (by sector) the window partitions in under 30 minutes each if anything happens.  I wouldn't even flinch at doing so.  I can also write out the intelligent copy and then re-encrypt the TC partitions.  Each technique has been used dozens of times.  Backups are current and I have NO fears.

I have already employed ecryptfs to encrypt both home and swap without any issues using straight 12.04 distro's such as Zorin or other non-alternate methods.  Its about as easy as it gets.  Just select the flash for boot and then create the Ubuntu system on the free space I mentioned above.  Once installed and updated I then encrypted using simple ecryptfs commands for home and swap.   Super easy.  Seems to work fine and I notice no overhead on an i7 machine.

However; I really study encryption and security and I believe DM Crypt/Luks is a safer and more secure approach.  Sector by sector with LVM interests me.  I am in the process of studying it and in the meantime I just want to experiment with it on a bare metal system.  I am amazed that I can't figure out how to manually create what is needed to do what I already do all day long with the non-alternate distro's.

While I work on that I would also like to hear how to create a duplicate boot flash in case I lose the original one.  My Macrium Pro does great sector imaging for the OS, but I need to just make a separate boot file or actual flash (since they are like 5 bucks).  I have high end USB hardware so full sector images write in both directions in under 30 minutes.  Its easy and never fails.

---

### Post by linuxperson on 2013-11-27
I also forgot to add the obvious other fact.  DM /Luks is full disk encryption of every sector and not just HOME.  I realize that statement could ignite an argument that we will not likely resolve in this thread.  We run the same threads over on TrueCrypt forums with file encryption vs WDE.

So how to get this done on a 4th partition (or I can leave it free space until install)?  Grub/boot to the flash too?  I do not want to change the first 3 partitions, although I could very quickly resize Part 3 since its not encrypted.  Consider 1 & 2 static and not changeable.  As mentioned before; the external drive is smoking fast but it means I have to always carry it with me.  Not my first choice.

---

### Post by oldfred on 2013-11-27
The only truecrypt info in my notes:
 Restore lost partiiton that was truecrypt
[http://ubuntuforums.org/showthread.php?t=1874260](http://ubuntuforums.org/showthread.php?t=1874260)

I think I have suggested a dd type backup of the truecrypt MBR, any default install of grub, installs to sda and then overwrites whatever boot loader you have in that partition.

I have also in some cases suggested with manual install to install grub2's MBR to a flash drive. You can just specify that as part of a manual install, but I have never used LVM or LVM with encryption. 

I also have just installed grub to a flash drive (MBR & /boot/grub) , but then you have to manually create your own grub.cfg as it has no operating system with the scripts to auto update it.


 chroot & reinstall grub encrypted LVM
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

      
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

   [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)
Only the latest version of Gparted (0.14) supports resizing LVM physical volumes. The version that ships with Ubuntu 12.10 or 13.04 does not support it.

---

### Post by linuxperson on 2013-11-28
I wanted to thank you again for trying to help me.  It looks like I am going to be stuck using a conventional distro with only home and swap encrypted.  That will majorly limit my willingness to place certain operations and data on my linux system.  I consider ecryptfs like a bathroom door lock.  Its OK for privacy but for absolute security I would want a better lock.  There is too much outside of _home_ on linux that I don't like unencrypted.  DM/Luks would have been that but the installer is a nightmare unless you use their "canned" approach.

I would suggest the alternate installer is not too friendly for special/manual installation needs.  It should be so easy to install linux on a partition/free space anywhere on a drive and then place the grub/boot on a USB flash.  I can do it with my eyes closed using non-alternate installs of 12.04.  I just don't like the trade off.  I will have to surrender my top notch security just because the installer won't do what all the regular flavors do SOP.  Hmmmmmmmm!

---

