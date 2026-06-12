---
title: "Missing disk space: messed up partitions - mounts - configuration"
date: 2020-04-24
forum: New to Ubuntu
---

### Post by robin5 on 2020-04-24
I have 18.04.4 Ubuntu Server installed on a Rpi 4.  It uses berryboot, so first boots Raspian, then it boot Ubuntu form the SSD.  This bit works OK. Then I wanted to add Gnome desktop so I entered
 sudo apt-get install ubuntu-gnome-desktop
After about an hour, I started to get out of disk space errors.  I should have 234 Gb. I only have 3.x Gb.

A Linux expert will surely see what  needs fixing.  Perhaps it is not mounted. Or perhaps the partition needs stretching
Below are various outputs:

How do I fix it?

Please help.
Thanks


Loading Gnome ....

 Selecting previously unselected package libreoffice-calc.
 Preparing to unpack .../0922-libreoffice-calc_1%3a6.0.7-0ubuntu0.18.04.10_arm64.deb ...
 Unpacking libreoffice-calc (1:6.0.7-0ubuntu0.18.04.10) ...
 dpkg: error processing archive /tmp/apt-dpkg-install-TFwCbo/0922-libreoffice-calc_1%3a6.0.7-0ubuntu0.18.04.10_arm64.deb (--unpack):
  cannot copy extracted data for './usr/lib/libreoffice/program/libsclo.so' to '/usr/lib/libreoffice/program/libsclo.so.dpkg-new': failed to write (**No space left on device**)

 No apport report written because the error message indicates a disk full error
                                                                               dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)

-------------------------------------


 **5.5.1.1Free disk space using df**

 Filesystem     1K-blocks    Used Available Use% Mounted on
 dev              1774520       0   1774520         0%          /dev
 none             3616888 3,582,884K           0  100%    /                                            3.58Gb used?
 tmpfs            1906184       0   1906184       0%         /dev/shm
 tmpfs            1906184     572   1905612   1%          /run
 tmpfs               5120       4      5116                1%          /run/lock
 tmpfs            1906184       0   1906184       0%         /sys/fs/cgroup
 tmpfs             381236       0    381236          0%         /run/user/1000


 **5.5.1.2Partitions**

 ubuntu@ubuntu:~$ cat /proc/partitions

 major     minor   #blocks name
    1        0       4096 ram0
    1        1       4096 ram1
    1        2       4096 ram2
    1        3       4096 ram3
    1        4       4096 ram4
    1        5       4096 ram5
    1        6       4096 ram6
    1        7       4096 ram7
    1        8       4096 ram8
    1        9       4096 ram9
    1       10       4096 ram10
    1       11       4096 ram11
    1       12       4096 ram12
    1       13       4096 ram13
    1       14       4096 ram14
    1       15       4096 ram15
    7        0     476980 loop0
  179        0    3872256 mmcblk0
  179        1     130048 mmcblk0p1
  179        2    3741184 mmcblk0p2
    8        0  234,431,064 sda             234Gb


 **5.5.1.3Using parted**

 $ (parted) print all
 Error: /dev/sda: unrecognised disk label
 
 
 Model: ASMT ASM105x (scsi)
 Disk **/dev/sda**: 240GB       <-------------- Ok  The SSD
 Sector size (logical/physical): 512B/512B
 Partition Table: unknown
 Disk Flags:
 
 
 Model: SD SU04G (sd/mmc)  <--------- the SD chip??
 Disk **/dev/mmcblk0**: 3965MB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags:
 
 
 Number  Start   End     Size    Type     File system  Flags
  1      1049kB  134MB   133MB   primary  fat16        lba
  2      134MB   3965MB  3831MB  primary  ext4
 
 
 ubuntu@ubuntu:/$ df -H
 Filesystem      Size  Used Avail Use% Mounted on
 dev             1.9G     0  1.9G   0% /dev
 none            3.8G  3.7G     0 100% /
 tmpfs           2.0G     0  2.0G   0% /dev/shm
 tmpfs           2.0G  586k  2.0G   1% /run
 tmpfs           5.3M  4.1k  5.3M   1% /run/lock
 tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
 tmpfs           391M     0  391M   0% /run/user/1000


 **5.5.1.4 Using lsblk**

 ubuntu@ubuntu:/$ lsblk
 NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
 loop0         7:0    0 465.8M  1 loop
 [COLOR=#c9211e]sda           8:0    0 223.6G  0 disk      <----- [/COLOR] 
 mmcblk0     179:0    0   3.7G  0 disk
 &#9500;&#9472;mmcblk0p1 179:1    0   127M  0 part
 &#9492;&#9472;mmcblk0p2 179:2    0   3.6G  0 part
 
 
 **5.5.1.5fdisk -l**

 ubuntu@ubuntu:/etc$ sudo fdisk -l
 Disk /dev/ram0: 4 MiB, 4194304 bytes, 8192 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 
 
 Disk /dev/ram1: 4 MiB, 4194304 bytes, 8192 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 ...
 Disk /dev/ram15: 4 MiB, 4194304 bytes, 8192 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
 Disk /dev/loop0: 465.8 MiB, 488427520 bytes, 953960 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 Disk /dev/mmcblk0: 3.7 GiB, 3965190144 bytes, 7744512 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0xf7b52d56
 Device         Boot  Start     End Sectors  Size Id Type
 /dev/mmcblk0p1        2048  262143  260096  127M  e W95 FAT16 (LBA)
 /dev/mmcblk0p2      262144 7744511 7482368  3.6G 83 Linux
 
 
 **Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors**
 **Units: sectors of 1 * 512 = 512 bytes**
 **Sector size (logical/physical): 512 bytes / 512 bytes**
 **I/O size (minimum/optimal): 512 bytes / 33553920 bytes**
 ubuntu@ubuntu:/etc$
 
 
 **5.5.1.6 Using cat fstab**

 ubuntu@ubuntu:/etc$ cat fstab
 #LABEL=writable          /               ext4   defaults        0 0
 #LABEL=system-boot       /boot/firmware  vfat    defaults        0       1
 
 
 **5.5.1.7 Using mount**

 All files accessible in a Unix system are arranged in one big tree, the file hierarchy, rooted at /. These files can be spread out over several devices. The mount command serves to attach the file system found on some device to the big file tree.
 The standard form of the mount command, is
 mount -t type device dir  
 This tells the kernel to attach the file system found on device (which is of type type) at the directory **dir**. The previous contents (if any) and owner and mode of dir become invisible, and as long as this file system remains mounted, the path name **dir** refers to the root of the file system on device.  
 For example, to mount the */dev/sdb1* file system to the */mnt/media directory* you would use:
 sudo mount /dev/sdb1 /mnt/media
 ubuntu@ubuntu:/etc$ mount
 proc on /proc type proc (rw,relatime)
 sysfs on /sys type sysfs (rw,relatime)
 dev on /dev type devtmpfs (rw,relatime,size=1774520k,nr_inodes=443630,mode=755)
 none on / type overlay (rw,relatime,lowerdir=/mnt/shared:/squashfs,upperdir=/mnt/data/Ubuntu_server_arm64_18.04.3.img192,workdir=/mnt/data/Ubuntu_server_arm64_18.04.3.img192.work,redirect_dir=on)
 securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
 tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
 devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
 tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
 tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
 tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
 cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
 cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
 cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
 cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
 cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
 cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
 cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
 cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
 cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
 cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
 debugfs on /sys/kernel/debug type debugfs (rw,relatime)
 systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=39,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
 tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
 mqueue on /dev/mqueue type mqueue (rw,relatime)
 configfs on /sys/kernel/config type configfs (rw,relatime)
 lxcfs on /var/lib/lxcfs type fuse.lxcfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
 fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
 tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=381236k,mode=700,uid=1000,gid=1000)

---

### Post by Tadaen_Sylvermane on 2020-04-24
Everything is pointed at your sd card. That is the problem. Yes you have a 240gb ssd but it isnt even mounted, much less being used. So your 4gb sd card is all you have. Need to reinstall and partition ssd and mount somewhere for it to be used.

I dont know much about rpis but i think you should get at least a 32gb card and do it like that. Unless you have a sata interface your ssd wont exactly be a speed demon i wouldnt expect due to usb limits.

---

### Post by TheFu on 2020-04-25
Can't rpi v4 boot from USB?  Why not do that and completely ignore the flash storage?
[https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=198258&sid=3f98dcfe12d0ada4a76ea497ffaa415d](https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=198258&sid=3f98dcfe12d0ada4a76ea497ffaa415d)

---

### Post by robin5 on 2020-04-25
The boot part is OK.  It boots to the 4Gb microSD and presents a list of OS's to load (I just have Ubuntu 18.04.4). After a few seconds wait for input and if there is none, it just re-boots from SSD and runs Ubuntu.  Ubuntu seems to run OK, but clearly the disk storage is not configued correctly.

The SSD was populated by downloading an Ubuntu 18.04.4 image from berryboot.  So the SSD is formatted and has files and boots OK. 

But it does not seem to have the SSD mounted.

I have tried
[LEFT] [I][FONT=Carlito][SIZE=3]$ sudo mount -t ext4 /dev/sda /
[/SIZE][/FONT][/I][FONT=Carlito][SIZE=3]but get[/SIZE][/FONT][I][FONT=Carlito][SIZE=3]
[/SIZE][/FONT][/I]
[/LEFT]
 mount: /: wrong fs type, bad option, bad superblock on /dev/sda, missing codepage or helper program, or other error.


What is broken?
How to fix it?
Help!

---

### Post by TheFu on 2020-04-25
I cannot provide steps, since your setup is unique. I've never heard of berryboot.  I can say a few things.

sda is the entire disk.  Use a partition, that would be sda1 - sda99.  Partitions need to be created in a partitioning tool - parted, fdisk, gparted are a few.  Never use an entire disk for anything except the create a partition table when necessary.

A partition needs to have a file system on it.  Linux systems have a bunch of possible file systems, but only a few can be booted.  ext4 is one and the default for Ubuntu systems for some good reasons.  Use mkfs to create a file system - sudo mkfs -t ext4 /dev/sda99 is similar to what you want. I specifically use 99 in my example to force you do look up the specific partition for your situation.  File systems like exFAT, vFAT, NTFS cannot be used to contain anything except data. They cannot be used for /home or any OS program or settings storage.

You cannot mount onto / while an OS is running.  Mounts for / must be configured in the /etc/fstab file.  Google "ubuntu fstab" for guides that do that.  All Linux systems use a UUID to mount storage because the device names can change from boot to boot.  blkid is the command to see the UUID to device mapping for each boot.  The UUID won't change between boots.  LABEL= can also be used, which is a little easier for humans. LABELs must be unique when attacked to the system.

In short, nothing is broken. Your knowledge level was just not sufficient to accomplish the goal.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good primer book for Linux systems. I always suggest that people read and work the exercises for the first 250 pgs, then skim the rest to become aware of where to look when they need other capabilities.

---

