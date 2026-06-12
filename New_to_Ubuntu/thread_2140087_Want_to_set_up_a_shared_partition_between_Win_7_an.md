---
title: "Want to set up a shared partition between Win 7 and Ubuntu"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by yixiaxian on 2013-04-28
Hi! I just installed Ubuntu 12.04LTS alongside with Win 7. There are two hard drives in my computer, and I use the first hard drive to install Win 7 and Ubuntu. For the second hard drive, I want to have one partition for Win 7 and have another one partion for shared data and programs (if program could be shared). However I'm not sure how to do this. I've used gparted to resize the second hard drive into two parts. The first partition has some data generated in Win 7, and the second part has not be allocated. Could anyone tell me what to do next? Or is this a good configuration for double system? Thank you!

Below is some code I get from the system:
```

chong@chong-Ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      240974      120456   de  Dell Utility
/dev/sda2   *      241664    21831679    10795008    7  HPFS/NTFS/exFAT
/dev/sda3        21831680   433240063   205704192    7  HPFS/NTFS/exFAT
/dev/sda4       433242110   488280063    27518977    5  Extended
/dev/sda5       484433920   488280063     1923072   82  Linux swap / Solaris
/dev/sda6       433242112   484433919    25595904   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18337581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1985  1318631264   659314640    f  W95 Ext'd (LBA)
/dev/sdb5            2048  1318631264   659314608+   7  HPFS/NTFS/exFAT
chong@chong-Ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   240912, Id=de
/dev/sda2 : start=   241664, size= 21590016, Id= 7, bootable
/dev/sda3 : start= 21831680, size=411408384, Id= 7
/dev/sda4 : start=433242110, size= 55037954, Id= 5
/dev/sda5 : start=484433920, size=  3846144, Id=82
/dev/sda6 : start=433242112, size= 51191808, Id=83
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     1985, size=1318629280, Id= f
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=     2048, size=1318629217, Id= 7
chong@chong-Ubuntu:~$ 



```

---

### Post by oldfred on 2013-04-28
My preference with two drives is to have an operating system on each drive and some data on each drive. Eventually a drive will fail and then you can still boot the other. Hopefully you then have good backups for failed drive.
Windows cannot easily read & write to Linux partitions. But Linux reads & writes to NTFS partitions. But usually best not to write into a Windows system partition. Often best just to set it as read only or not ever write into it.

Programs cannot be shared, but some data can be. I moved my Firefox & Thunderbird profiles into a shared NTFS data partition and installed Firefox in both XP and several of my Ubuntu installs using the same profile. I even copy profile to my laptop when traveling to shared NTFS partition on it.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by yixiaxian on 2013-04-28
Thank you oldfred! So I reinstall the system at your advice. The first hard drive (250GB) is used to install Win 7 only, and the second hard drive disk (1TB) I make 2 primary partitions (Data, UData) and one extent partition (containing two logical partitions, ext4 and linux-swap). I install Ubuntu 12.04LTS on ext4 partitiona (bootloader still in the the first hard drive). I intend to use Data to store data from Windows, and use UData as a shared partition. 

Rightnow I see OS, Data, UData on the left panel of my desktop, and from gparted I see them mounted to /media. The question I have is how can I change the type of mounting to read-only for OS and Data, if possible? Thanks!

> **oldfred said:**
> My preference with two drives is to have an operating system on each drive and some data on each drive. Eventually a drive will fail and then you can still boot the other. Hopefully you then have good backups for failed drive.
Windows cannot easily read & write to Linux partitions. But Linux reads & writes to NTFS partitions. But usually best not to write into a Windows system partition. Often best just to set it as read only or not ever write into it.

Programs cannot be shared, but some data can be. I moved my Firefox & Thunderbird profiles into a shared NTFS data partition and installed Firefox in both XP and several of my Ubuntu installs using the same profile. I even copy profile to my laptop when traveling to shared NTFS partition on it.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by yixiaxian on 2013-04-28
Thank you oldfred! So I read some articles talking about mounting Windows partitions [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions), and the meaning of umask [http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask). From what I understand, I should write the following in \etc\fstab:
```


UUID=519CB82E5888AD0F  /media/Data  ntfs  defaults,umask=222  0 0

```

which will mount my Windows-only data as a read-executive-only partition for anyone (including owner), but one thing I don't understand is why the last number be set to 0. That, from what I read, means the partition won't be checked at booting. Then will it still be mounted? Or can I set it to 2 to let it checked? Will that take long time at booting? Thanks!

---

### Post by yixiaxian on 2013-04-28
OK I get it. For additional partitions, it's not necessary to check at boot. So here is my plan for mounting my OS, Data, and WinData: I want to mount OS and WinData under /mnt so that they won't show up in file manager left panel, and I want to set them to be read-only so nothing could change them in Ubuntu. For Data I want to mount it under /media with type of ntfs-3g so that Ubuntu and Win 7 could share data. Below is my preparation work on /fstab, could anyone take a look at them and tell me what I should put to replace "windows_names" in the /etc/fstab <option>, and if I do it wrong in other places? Thank you!

Step 1: Check system information
```


chong@Chong-Ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      240974      120456   de  Dell Utility
/dev/sda2   *      241664    21831679    10795008    7  HPFS/NTFS/exFAT
/dev/sda3        21831680   488275967   233222144    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18337581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   835577855   417787904    7  HPFS/NTFS/exFAT
/dev/sdb2       835577856  1474459647   319440896    7  HPFS/NTFS/exFAT
/dev/sdb3      1474459648  1953523711   239532032    5  Extended
/dev/sdb5      1474461696  1928615935   227077120   83  Linux
/dev/sdb6      1928617984  1953523711    12452864   82  Linux swap / Solaris
chong@Chong-Ubuntu:~$ 


chong@Chong-Ubuntu:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07DB-0315" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="54A6DB9DA6DB7E44" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="8044DDEB44DDE446" TYPE="ntfs" 
/dev/sdb1: LABEL="WinData" UUID="76D7E15B27339005" TYPE="ntfs" 
/dev/sdb2: LABEL="Data" UUID="78C9E135200CDC88" TYPE="ntfs" 
/dev/sdb5: UUID="337dff9e-2c67-4887-be68-d27216ad668c" TYPE="ext4" 
/dev/sdb6: UUID="ba74dfa1-bc93-4687-8ba2-ed4df24a3d0e" TYPE="swap" 
chong@Chong-Ubuntu:~$ 


chong@Chong-Ubuntu:~$ sudo mkdir /media/Data
chong@Chong-Ubuntu:~$ ls /media
Data



```

Step 2: Open to edit fstab:
```

chong@Chong-Ubuntu:~$ sudo cp /etc/fstab /etc/fstab.orig
chong@Chong-Ubuntu:~$ gksudo gedit /etc/fstab


```

Step 3: Edit fstab by putting the following below the file:
```

UUID=78C9E135200CDC88  /media/Data  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0

```

---

### Post by oldfred on 2013-04-28
If you are following the suggestion by Morbius1 which I also use, it look good. What is the question on Windows names. You want to to prevent invalid characters.

After any editing of fstab always run:
sudo mount -a

It will then remount with new entries or give error messages. Best to resolve errors before rebooting as then it could be a major issue.

       Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not. I prefer /mnt and link folders from the data partition into /home.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

