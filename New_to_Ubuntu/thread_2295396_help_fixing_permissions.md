---
title: "help fixing permissions"
date: 2015-09-18
forum: New to Ubuntu
---

### Post by joe185 on 2015-09-18
Sorry if this isn't the right place for the post,please redirect if not.

I have a acer c710 chromebook that i installed ubuntu with crouton.I'm having an issue properly writing,or executing on my external usb drives.I've asked for help on crouton forum on google + only to be told i shouldn't be messing with the system because i can't figure out why it's behaving the way it is.So i thought i would ask here.I'm not a total newbie,but i'm not very fluent other than playing some games,and writing some docs.I've used ubuntu (12 i think) for awhile,also a ver of debian,and unity.

I see the same problem i have experienced all over google and such with some answers,but it's a mixed bag of success.As for me,i'm not having ANY success!Any help would be greatly appreciated.I attached my output of sudo fdisk -lu .I'm not sure where to go with this.

The device i'm trying to gain proper permissions on is the 67.1 gb.
```
(trusty)williamsclan@localhost:~$ sudo fdisk -lu
[sudo] password for williamsclan: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
256 heads, 63 sectors/track, 1939 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    31277231    15638615+  ee  GPT

Disk /dev/mapper/encstateful: 3377 MB, 3377442816 bytes
255 heads, 63 sectors/track, 410 cylinders, total 6596568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/encstateful doesn't contain a valid partition table

Disk /dev/sdb: 67.1 GB, 67108864000 bytes
2 heads, 63 sectors/track, 1040253 cylinders, total 131072000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001ef334

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64   131071999    65535968    b  W95 FAT32

Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
256 heads, 63 sectors/track, 1929 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *        2048    31116287    15557120    c  W95 FAT32 (LBA)
```

---

### Post by sotiris2 on 2015-09-18
Browse to the partition and open a terminal there via right click-> open in terminal then enter the following > ls -l Post the output.

---

### Post by yancek on 2015-09-18
Run the ls -l (that's a Lower Case Letter L) command suggested on the /media directory like this:  ls -l /media/williamsclan  That is if williamsclan is the actual user name.  You should see the permissions and owner:group which are significant.  If you don't understand the output, post it here and someone will explain it.  You might also run ls -l on /media to check your user owner:group and permissions.

---

### Post by slickymaster on 2015-09-18
> **yancek said:**
> Run the ls -l (that's a Lower Case Letter L) command suggested on the /media directory like this:  ls -l /media/williamsclan  That is if williamsclan is the actual user name.  You should see the permissions and owner:group which are significant.  If you don't understand the output, post it here and someone will explain it.  You might also run ls -l on /media to check your user owner:group and permissions.

This ^^^

And please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to post output from the terminal because code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by joe185 on 2015-09-18
i can 
```
sudo -s
```

which gives me 
```
(trusty)root@localhost:~# 
```

i cannot access the partitions at all!i can view them in the disk app,but nothing else!

---

### Post by joe185 on 2015-09-18
the ls-l outputs this

```
(trusty)root@localhost:~#  ls -l /media/williamsclan
total 0
(trusty)root@localhost:~# 

```

---

### Post by sotiris2 on 2015-09-18
Lets see if you can actually mount the partition or there is a problem. Open up a terminal and make a new directory ```
mkdir ~/disk
``` Then try mounting it ```
sudo mount /dev/sdb1 ~/disk -o rw,exec,uid=$(id -u),guid=$(id -g) -v
``` If it works you should not get any output and you can open it in nautlus and try opening and creating files. ```
 nautlus ~/disk &
``` Otherwise post any terminal output back here.

---

