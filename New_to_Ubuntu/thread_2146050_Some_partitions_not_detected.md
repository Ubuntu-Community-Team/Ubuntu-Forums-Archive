---
title: "Some partitions not detected"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2013-05-17
My friend was using Windows 7 and it crashed suddenly, after that he  installed Windows XP, and he was not able to access some partition which  were detected by windows. Then we tried live os using Ubuntu 11.10.  Some partitions were not detected by ubuntu and gparted disk utility  shows those partition as Unknow filesystem. 

I checked the fstab blkid and here are the results. We need to retrieve  the data from the partitions before formating them. Please give some  guidance 

Thanks 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b69bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   102402047    51097600    7  HPFS/NTFS/exFAT
/dev/sda2       102402048   204795903    51196928    7  HPFS/NTFS/exFAT
/dev/sda3       204796620   625137344   210170362+   f  W95 Ext'd (LBA)
/dev/sda5       204796683   409593239   102398278+   7  HPFS/NTFS/exFAT
/dev/sda6       409593303   625137344   107772021    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="CE40C59D40C58CA1" TYPE="ntfs" 
/dev/sda6: LABEL="Entertainment" UUID="3E76339676334E41" TYPE="ntfs" 
/dev/sdc1: LABEL="TRANSCEND" UUID="96F4-CC43" TYPE="vfat"

ubuntu@ubuntu:~$ cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ mount
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/TRANSCEND type vfat  (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


```

---

### Post by dino99 on 2013-05-17
General comment: 
- always try to resolve an OS issue with the its own cd/dvd tools (not with an other OS)
- as the first screenshot is showing : "disk have a few bad sectors" , then you need first to fix that issue (or try to fix it)
- no need to disturb the OS with some usb devices plugged if you does not really need them

[http://www.wondershare.com/disk-utility/fix-bad-sectors.html](http://www.wondershare.com/disk-utility/fix-bad-sectors.html)
[http://www.wikihow.com/Repair-Bad-Sectors](http://www.wikihow.com/Repair-Bad-Sectors)

---

### Post by Mark Phelps on 2013-05-17
IF those partitions were formatted for MS Windows filesystems, and you're willing to spend some money ... read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by 1991sudarshan on 2013-05-19
> **Mark Phelps said:**
> IF those partitions were formatted for MS Windows filesystems, and you're willing to spend some money ... read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.


Thank you so much. It works. My friends is able to retrieve the data.

---

