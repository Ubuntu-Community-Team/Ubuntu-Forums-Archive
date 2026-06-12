---
title: "Need help removing grub v. am idiot...hear me fail."
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Huzudra on 2011-10-16
Ok, long story typed on a small keyboard.

I tried to do a wubi install of 11.1 on my main PC which has 2 NVRAID arrays (both Raid0), long story short Wubi pops up that it can't install grub, so me being dumb I try to install it to some of the places it suggested. Prior I had 9.1 on Wubi with NO problems, must be a GRUB2 issue with this computer...but I digress. Now I've got broken grub spread across some different drives which points to nothing bootable and no clue what to do. 

So, part2: I get a trusty handy dandy good old XP retail disc, a floppy/floppy drive and sling it off the side of one PC to create the NVRAID driver floppy, shuffle across the room to the problem PC, install the floppy drive and boot the XP disc, load drivers from floppy, get to recovery console, run fixmbr and fixboot, and bootcfg, bootcfg says it's got some issues with stuff, dunno what to do so I reboot. back to the broken grub.:(

Ok....so I try to install Ubuntu 11.1, let it resize a bit of space on a non raid disc, it fails at...guess what? Installing GRUB!  OK, now I have more broken GRUB, but atleast I now have a normal GRUB command line, but still no clue what to do with it. 


What I want to do is nuke grub from anywhere it resides on the system, so I can run Windows Recovery Console and fix my Windows MBR. I need help with this, suggestions, a hand held, a hug, and a stiff drink.  I'll settle for just some of those, which ever gets me bootable.

Now, should I just try to install 9.10 or 10.04 (I have the resized space on there now) and see if GRUB will install correctly and see my windows install and get me booting or will that just screw things up more? 

I'm running out of idea's and patience and energy, I just want to be able to use my main machine again.  Don't get me wrong, I LOVE Ubuntu, but it just does not play with my RAID volumes and nearly all the games I like to play don't run or don't run well on Ubuntu (even with WINE). I still need Windows for now.

---

### Post by drs305 on 2011-10-16
From an Ubuntu LiveCD, if you download/run the boot info script and post the contents of the RESULTS.txt file it generates it will show us the status of your boot files.

You can get the script from the "BIS" link in my signature.

If you think you got 11.10 installed except for Grub, and it's on a non-raid disk, you can try to mount the partition Ubuntu is on and install Grub 2 from the command line. Substitute the proper values for XY. X is the drive, starting with 0; Y is the partition number, starting with 1.
```

sudo mount /dev/sdXY /mnt  # example: sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```
Don't include the partition number in the second command.

I'm not a Windows or RAID guy, so my assistance will be limited but there are others who will see your thread to assist.

---

### Post by Huzudra on 2011-10-16
I have 5 disks,4 in 2 arrays with 3 partitions on one volume, one on the other, and a single disc with 2 partions. I have NO clue how to (in ubuntu) tell what's what except that my "C" drive is a 200GB partition on the 1.16TB array.

---

### Post by drs305 on 2011-10-16
> **Huzudra said:**
> I have 5 disks,4 in 2 arrays with 3 partitions on one volume, one on the other, and a single disc with 2 partions. I have NO clue how to (in ubuntu) tell what's what except that my "C" drive is a 200GB partition on the 1.16TB array.

If you boot the Ubuntu LiveCD, you can open a terminal (ALT-F2 then click gnome-terminal) and run 
```
sudo fdisk -l # lowercase L
```
That will show you your drives and partitions.
You are looking for the "Linux" partition. There will probably be another one on the disk "Linux swap".

Once you mount it with the command from the previous post, you can take a look at the / folders with:
```
gksu nautilus  /mnt
```
and it should show folders such as "boot", "etc", "home" ...

---

### Post by Huzudra on 2011-10-16
I have a blinking cursor after 

grub>

What can I do from there? 10.04 isn't wanting to boot from a usb stick and I've burned like 15 CD's in 2 days now...

---

### Post by Huzudra on 2011-10-16
Let me make this clear, at this point I don't care about dual booting or linux, I just need to be at my windows desktop.

---

### Post by drs305 on 2011-10-16
> **Huzudra said:**
> Let me make this clear, at this point I don't care about dual booting or linux, I just need to be at my windows desktop.

I understand. And if you posted again needing more instruction I was going to suggest we were straying from your real goal.

However, if you can boot the LiveCD we really would like to see the RESULTS.txt 

That will give us a wealth of information which those experienced with Windows can use to help you get your system working again.

There is a way to restore the MBR to point to Windows from the LiveCD, but that method only works if your Windows boot files are correct. It sounds like they aren't.

What you want is to restore your Windows boot. While we are certainly willing to help, your efforts might be better rewarded on a Windows forum, especially since you aren't really interested in dual-booting - at least for now. 

Here are some of the links forum member *oldfred* on repairing Windows boot issues:
[http://ubuntuforums.org/showpost.php?p=11033163&postcount=14]("http://ubuntuforums.org/showpost.php?p=11033163&postcount=14")
And this thread:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Huzudra on 2011-10-16
Thanks, I'm going to come back at this tomorrow after work with a clear head. I'm too frustrated and exhausted at the moment and I feel like I'm just going in circles. One more try with 9.10 which seemed to work (wubi atleast) before. 10.04 USB wouldn't even boot, I can try 11.10 or 11.04 USB to run whatever that was for better information tomorrow. I just have no fight left in me.

---

### Post by Huzudra on 2011-10-16
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3281154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   420244334   210122136    7  HPFS/NTFS/exFAT
/dev/sda2       420244335   480231044    29993355    c  W95 FAT32 (LBA)
/dev/sda3       480231045  2500517249  1010143102+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfaeb0deb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1172214854   586107396    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba00f57

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/nvidia_fgebffce: 1280.3 GB, 1280270008320 bytes
255 heads, 63 sectors/track, 155650 cylinders, total 2500527360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xb3281154

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce1   *          63   420244334   210122136    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2       420244335   480231044    29993355    c  W95 FAT32 (LBA)
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3       480231045  2500517249  1010143102+   7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.

Disk /dev/mapper/nvidia_fgebffce1: 215.2 GB, 215165067264 bytes
255 heads, 63 sectors/track, 26158 cylinders, total 420244272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce1p2   ?   729050177  1273024900   271987362   74  Unknown
/dev/mapper/nvidia_fgebffce1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_fgebffce2: 30.7 GB, 30713195520 bytes
255 heads, 63 sectors/track, 3734 cylinders, total 59986710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 8704 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce2p1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p4   ?  2885681152  2885736650       27749+   d  Unknown
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_fgebffce3: 1034.4 GB, 1034386536960 bytes
255 heads, 63 sectors/track, 125757 cylinders, total 2020286205 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 62976 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce3p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/mapper/nvidia_baicbbdc: 600.2 GB, 600181440512 bytes
255 heads, 63 sectors/track, 72967 cylinders, total 1172229376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xfaeb0deb

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_baicbbdc1              63  1172214854   586107396    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/nvidia_baicbbdc1: 600.2 GB, 600173973504 bytes
255 heads, 63 sectors/track, 72966 cylinders, total 1172214792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_baicbbdc1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_baicbbdc1p2   ?   729050177  1273024900   271987362   74  Unknown
/dev/mapper/nvidia_baicbbdc1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_baicbbdc1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac1ab54c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1167138942   583569440    7  HPFS/NTFS/exFAT
/dev/sde2      1167140862  1250263039    41561089    5  Extended
/dev/sde5      1167140864  1241874431    37366784   83  Linux
/dev/sde6      1241876480  1250263039     4193280   82  Linux swap / Solaris

Disk /dev/sdf: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e051

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          62    15635593     7817766    b  W95 FAT32

```

---

### Post by Huzudra on 2011-10-16
```


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3281154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   420244334   210122136    7  HPFS/NTFS/exFAT
/dev/sda2       420244335   480231044    29993355    c  W95 FAT32 (LBA)
/dev/sda3       480231045  2500517249  1010143102+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfaeb0deb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1172214854   586107396    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba00f57

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/nvidia_fgebffce: 1280.3 GB, 1280270008320 bytes
255 heads, 63 sectors/track, 155650 cylinders, total 2500527360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xb3281154

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce1   *          63   420244334   210122136    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2       420244335   480231044    29993355    c  W95 FAT32 (LBA)
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3       480231045  2500517249  1010143102+   7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.

Disk /dev/mapper/nvidia_fgebffce1: 215.2 GB, 215165067264 bytes
255 heads, 63 sectors/track, 26158 cylinders, total 420244272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce1p2   ?   729050177  1273024900   271987362   74  Unknown
/dev/mapper/nvidia_fgebffce1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_fgebffce2: 30.7 GB, 30713195520 bytes
255 heads, 63 sectors/track, 3734 cylinders, total 59986710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 8704 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce2p1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce2p4   ?  2885681152  2885736650       27749+   d  Unknown
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_fgebffce3: 1034.4 GB, 1034386536960 bytes
255 heads, 63 sectors/track, 125757 cylinders, total 2020286205 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 62976 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fgebffce3p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fgebffce3p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/mapper/nvidia_baicbbdc: 600.2 GB, 600181440512 bytes
255 heads, 63 sectors/track, 72967 cylinders, total 1172229376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xfaeb0deb

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_baicbbdc1              63  1172214854   586107396    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/nvidia_baicbbdc1: 600.2 GB, 600173973504 bytes
255 heads, 63 sectors/track, 72966 cylinders, total 1172214792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_baicbbdc1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_baicbbdc1p2   ?   729050177  1273024900   271987362   74  Unknown
/dev/mapper/nvidia_baicbbdc1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_baicbbdc1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac1ab54c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1167138942   583569440    7  HPFS/NTFS/exFAT
/dev/sde2      1167140862  1250263039    41561089    5  Extended
/dev/sde5      1167140864  1241874431    37366784   83  Linux
/dev/sde6      1241876480  1250263039     4193280   82  Linux swap / Solaris

Disk /dev/sdf: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e051

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          62    15635593     7817766    b  W95 FAT32
ubuntu@ubuntu:~$ sudo mount /dev/sdXY /mnt  # example: sudo mount /dev/sdb1 /mntmount: special device /dev/sdXY does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sde5 /mnt  # example: sudo mount /dev/sdb1 /mntubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sde5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
ubuntu@ubuntu:~$ 

```











I think I made it worse? Well not any better. HAL says it can't do what I'm asking. What now?

---

### Post by drs305 on 2011-10-16
It does look like sde5 is your Ubuntu partition. If you think you have an intact Ubuntu installation there, these commands should work if you are running the same version on the CD as what you installed on your e drive:

We will first unmount everything, then try to install Grub. But again we are straying from your goal of being able to boot Windows. You appear to want to try to boot Ubuntu again, so:

```

sudo umount /dev/sde5
sudo mount /dev/sde5 /mnt
sudo grub-install --root-directory=/mnt /dev/sde
```
This should not generate partition errors or an error about installing to a partition. Don't use "/dev/sde5" in the third command.
Reboot and see if Ubuntu boots.

But again, the RESULTS.txt is what Windows gurus here are going to want to see (especially if Ubuntu still won't boot).

---

### Post by Huzudra on 2011-10-17
Thanks, I'll give that a go and do the script thing later in the week. I'm done messing with it for a few days, I'll revisit with a calm clear head. Will 11.10 Ubuntu be able to mount and recognize the disks on my RAID0 arrays? I'd like to recover my data off them and start fresh with a clean install of Win7 64bit. I've had 4GB of ram for 5 years only been able to use 3.5GB of it.

---

### Post by drs305 on 2011-10-17
> **Huzudra said:**
> Thanks, I'll give that a go and do the script thing later in the week. I'm done messing with it for a few days, I'll revisit with a calm clear head. Will 11.10 Ubuntu be able to mount and recognize the disks on my RAID0 arrays? I'd like to recover my data off them and start fresh with a clean install of Win7 64bit. I've had 4GB of ram for 5 years only been able to use 3.5GB of it.

I've found posts of users successfully using RAID0 with Grub 2. Using the latest G2 (1.99) will help, which is in Natty and later. I'm not saying it is incredibly easy to set up, but I've seen successful posts on the forum. I personally don't have any Grub 2 /RAID experience...

---

