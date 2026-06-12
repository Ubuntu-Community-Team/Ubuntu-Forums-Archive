---
title: "System Restore Point?"
date: 2016-06-27
forum: New to Ubuntu
---

### Post by Vincent_Massi on 2016-06-27
Xenial Xerus is running great on a partition on my Windows 7 desktop. However, it wants me to upgrade some drivers. Can I set a System Restore Point first?

---

### Post by DuckHook on 2016-06-27
Welcome to the forums, Vincent_Massi.

Though entirely understandable, it is important not to bring your Windows expectations into Linux. It may help to read the link in my sig: Linux is Not Windows.

As to your question:

It is possible to do something like Windows' system restore point with Ubuntu, but you would have had to originally install in a very different and more complicated way, which I doubt that you did. You would have had to install your system on an LVM partition. Although a selectable option at time of install, 99% of people don't know enough about Linux to choose it, so it is rarely used. If you are dual booting Windows, it is unwise to add further complexity with LVM anyway. Unless you *really* know what you are doing and carefully set the partition up beforehand, choosing LVM during install will wipe out Windows.

This is a convoluted way of saying that, for all practical purposes, in your case, there is no system restore point function.

The good news is that it is much easier to install Ubuntu than Windows. If the drivers bork your system, a reinstall is not that difficult. Since this is new install, I don't imagine that you have much critical data on your Ubuntu partition. Make sure you back up such data before allowing the driver updates and you should be fine.

Also, if you don't need the drivers (i.e. if the community video drivers are working fine for you) then don't install them.

---

### Post by QIII on 2016-06-28
An important question, since Linux is a different animal than Windows:

What drivers are you trying to upgrade?

---

### Post by mastablasta on 2016-06-28
> **DuckHook said:**
> 
It is possible to do something like Windows' system restore point with Ubuntu, but you would have had to originally install in a very different and more complicated way, which I doubt that you did. You would have had to install your system on an LVM partition. Although a selectable option at time of install, 99% of people don't know enough about Linux to choose it, so it is rarely used. If you are dual booting Windows, it is unwise to add further complexity with LVM anyway. Unless you *really* know what you are doing and carefully set the partition up beforehand, choosing LVM during install will wipe out Windows.
.

actually there is an easier way if you use:

BTRFS 
ZFS for Linux

Both of these advanced file systems have a snapshot functionality built in. so if something does go wrong, you can easilly restore a previous full system snapshot. which is better than just a "system restore point". in any case both of these file system are considered an overkill for home user, although i believe OpenSuse's default is now BTRFS.

by the way if things go wrong with GPU drivers, they can be purched form text only mode and the defautl opensource drivers should be available on reboot. no need to create a restore point. furtheremo there are old kernels available in GRUB menu (hold shift to access it)

---

### Post by grahammechanical on 2016-06-28
If things are working fine you can remove the tick mark against those drivers and then the upgrade to the drivers will not take place. If you do the upgrade and then have a problem loading to a working desktop. There are things that you can do.

At the Grub boot menu select Advanced options for Ubuntu. At the sub-menu select a Linux kernel with recovery mode. Then at the recovery menu select Resume normal boot. That will often load to a working desktop without using a proprietary video driver. Once at the desktop we can use Additional Drivers to change video drivers.

The recovery menu is where we can get a root shell prompt and use it to purge the proprietary video driver and then the default open source video driver will take over.

The Advanced options for Ubuntu sub-menu is where we choose an earlier kernel that may load to a desktop when an update to the kernel proves to break the system.

There is something that people should know about the btrfs file system. It will do snapshots and roll backs of the entire system but it is command line. We do not have a GUI utility to manage snapshots from the desktop. At least we did not have the last time I used btrfs. But the Advanced options sub-menu will give an option  called apt-snapshots - revert to old snapshot & reboot. And it does work.

Regards.

---

### Post by Vincent_Massi on 2016-06-28
Wow, I appreciate all the answers, and I learned from them. Originally designed for Windows 7, my rig has XP, 8, 10, and now Linux on four different partitions. Linux is running the fastest and most smoothly. I've decided that at this point in time, I will not upgrade the drivers.

---

### Post by oldfred on 2016-06-28
Even a restore point saved on same hard drive is not a good backup, as when hard drive fails you lose restore & install. You need to backup to separate devices and have multiple copies so even if you delete or change a file you have access to it.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/) 
     
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by Vincent_Massi on 2016-06-28
Duck Hook, I just read your article "Linux is not Windows." It is a very well-written, helpful article.

---

### Post by pauljw on 2016-06-28
I have been using SystemBack in my 14.04 system with great success.  I see it's also available for 16.04.  This is a PPA, so keep that in mind, especially when doing upgrades to new versions of the OS.  SystemBack does create restore points and they do work as advertised.  I was able to use it to restore my system to a prior state with no issues.

[https://launchpad.net/~nemh/+archive/ubuntu/systemback](https://launchpad.net/~nemh/+archive/ubuntu/systemback)

---

### Post by DuckHook on 2016-06-28
> **Vincent_Massi said:**
> ...my rig has XP...So long as you are aware that XP is years past end-of-life and is a malware sieve. I will only run mine within a well-sandboxed virtual machine.
> **Vincent_Massi said:**
> ..."Linux is not Windows." It is a very well-written, helpful article.It is a nice summary of how big the differences are, but most importantly, it sets expectations up properly.
> **pauljw said:**
> I have been using SystemBack in my 14.04 system with great success...Thank you for this. I did not know that it existed. For new users: the usual warnings about PPAs apply.
> **mastablasta said:**
> actually there is an easier way if you use:

BTRFS 
ZFS for Linux

Both of these advanced file systems have a snapshot functionality built in. so if something does go wrong, you can easilly restore a previous full system snapshot. which is better than just a "system restore point". in any case both of these file system are considered an overkill for home user, although i believe OpenSuse's default is now BTRFS.I was under the impression that ZFS only started shipping with Ubuntu in Xenial. Older versions had to be specially installed after the initial install.

@OP All alternate files systems, whether LVM, BTRFS or ZFS have more limited tools than EXT4. I'm not that familiar with BTRFS or ZFS, but I have read that gparted, fdisk and fsck don't currently work on these two.

> **grahammechanical said:**
> ...There is something that people should know about the btrfs file system. It will do snapshots and roll backs of the entire system but it is command line....as are many interesting tools and utilities in Linux.

@OP

We are in danger of overloading you with options and details here. While all of these options are nice to have, please note that what will work for you is what is easiest to implement/administer. I would recommend that you forego all of the fancy alternatives and just have a good backup routine. As *oldfred* states the most important element in this discussion is the need for full backups. Once you have those, all alternate file systems become just nice-to-haves.

---

