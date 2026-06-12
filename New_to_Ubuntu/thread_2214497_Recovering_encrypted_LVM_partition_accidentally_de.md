---
title: "Recovering encrypted LVM partition accidentally deleted with gparted"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by d_brown23 on 2014-04-01
Hi,

In a moment of absent-mindedness while reformatting a usb flash drive with gparted I accidentally selected the main harddrive on my laptop, and proceeded to delete the encrypted LVM partition which contains my root, home and swap volumes. The boot partition is at the beginning of the drive and of course unencrypted. The LVM takes up the rest of the disk. While gparted failed almost instantly with the reformat (I presume because the partition in question was mounted) it did "delete" it, so that the space it occupied was defined as unallocated. I am a bit of a noob and not too sure on my terminology, but I think this means that it has been removed from the partition table? Perhaps someone can correct me if I am wrong on this.

I backed up a few of my critical documents (I did not have space on external drives for much more), but after rebooting I got the message "evms_activate is not available" where I would normally unlock the physical volume. I have booted with a live USB and tried a few things suggested in other posts to those with similar problems, but I am not really confident enough to adapt the advice to my own situation, nor to take the jump and change anything. Below are a few of the outputs from the various commands and tools:

 fdisk -l gave the following output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 256.1 GB, 256060514304 bytes
92 heads, 60 sectors/track, 90601 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ba65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      503807      250880   83  Linux
```

sfdisk -l gave the following:

```
ubuntu@ubuntu:~$ sudo /sbin/sfdisk -l /dev/sda

Disk /dev/sda: 31130 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/92/60 (instead of 31130/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 2826240 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     91-     91-    250880   83  Linux
        start: (c,h,s) expected (0,34,9) found (0,32,33)
        end: (c,h,s) expected (91,24,48) found (31,91,60)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
```

A quick search with testdisk gave the following:

```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
     Partition               Start        End    Size in sectors
>* Linux                    0  32 33    31  91 60     501760
 P Linux                   31  91 61    31 156 61       4096

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext2 blocksize=1024 Sparse superblock, 256 MB / 245 MiB
```

The second partition had the following details:

```
LUKS 1 (Data size unknown), 2097 KB / 2048 KiB
```

and was listed as damaged.

A deep scan with testdisk gave the following:

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63
     Partition               Start        End    Size in sectors
>  Linux                    0  32 31    31  91 58     501760
   Linux                    0  32 33    31  91 60     501760
   Linux                   24  89  2  7318 223  9  117186560
   Linux                   31  91 61    31 156 61    4096

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext2 blocksize=1024 Sparse superblock Backup superblock, 256 MB / 245 MiB
```

The second, third and fourth partitions had the following details:

```
ext2 blocksize=1024 Sparse superblock, 256 MB / 245 MiB
ext4 blocksize=4096 Large file Sparse superblock, 59 GB / 55 GiB
LUKS 1 (Data size unknown), 2097 KB / 2048 KiB
```

The first was damaged, the second was the boot partition, the third had contents of my root partition, with one of the entries in red, listed below:

```
lrwxrwxrwx     0     0        29 14-Jan-2014 13:01 vmlinuz.32685
```

If anyone can provide help on how I might recover this partition I would be most grateful. If you need any further information please let me know, although please tell me the commands I will need to run to get that information as well. I also apologise if any of the terminology I have used is incorrect or misleading.

---

### Post by oldfred on 2014-04-02
If data was encrypted, testdisk will not be able to drill down and find anything (or it better not).

You probably had two physical partitions? A /boot and the LVM. The inside the LVM were all your logical partitions.

So I would try to recover the two partitions and see if then it works. Otherwise with encryption good backups are your only way to recover data as that is the entire purpose of encryption is to prevent anyone from reading it.

---

### Post by d_brown23 on 2014-04-07
Thanks oldfred for the advice. I bit the bullet in the end after reading a bit more about testdisk and realising that I could write the LUKS partition to the partitioning table without drastically altering the data on the disk. I didn't realise initially that LUKS was the encryption method on the LVM, and that the 2MB partition was the header for this. All of the info for the LVM was in there, and once I had written it to disk it was simply a matter of extending that partition with fdisk to fill the rest of the disk, and booting in as normal (with the encryption pass). I would note that in this case I was positive that the LVM partition took up the whole of the disk after the boot partition, so this made things simpler. Once inside, fdisk was still claiming that the logical volumes did not have correct partition tables, although they seemed to be functioning correctly. Anyway, I used the opportunity to back up the rest of my data and start over with a fresh install.

With regard to your comment about testdisk not being able to 'drill down' and find anything in the LVM, I was actually a bit surprised that in the deep scan it found at least a partial partition that seemed to display the first-level contents of my root partition. I imagined that encryption meant that even this level of data would not be available.

---

### Post by oldfred on 2014-04-07
I would expect it would see the /boot partition, but not the encrypted LVM partition.

I do not think fdisk works on anything but basic MBR(msdos) partitions. So I would not expect it to work on LVM parititions. You need LVM tools for that.

I have not used LVM.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

