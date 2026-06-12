---
title: "[SOLVED] a couple of things..."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by allenbradley on 2008-09-16
Recently, ubuntu has been acting up for me. I tried the automount tutorial : [http://ubuntuforums.org/showthread.php?t=802699,but](http://ubuntuforums.org/showthread.php?t=802699,but) it does not seem to work. The lines are added at the end of fstab, but the partitions do not automount.
 Secondly, when i boot into ubuntu and manually mount my Data partition, it says I do not have the required permissions, though i am the only user in my machine. How do I solve these problems?

---

### Post by Malac on 2008-09-16
Post the contents of /etc/fstab and output of fdisk -l (lower case L not digit 1)

---

### Post by iaculallad on 2008-09-16
> **allenbradley said:**
> Recently, ubuntu has been acting up for me. I tried the automount tutorial : [http://ubuntuforums.org/showthread.php?t=802699,but](http://ubuntuforums.org/showthread.php?t=802699,but) it does not seem to work. The lines are added at the end of fstab, but the partitions do not automount.
 Secondly, when i boot into ubuntu and manually mount my Data partition, it says I do not have the required permissions, though i am the only user in my machine. How do I solve these problems?

Do post your:

```
cat /etc/fstab
sudo blkid
sudo fstab -l
```

---

### Post by allenbradley on 2008-09-16
Output of fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10450    83891430    7  HPFS/NTFS
/dev/sda3           10465       30401   160143952+   5  Extended
/dev/sda5           10465       27528   137066548+   7  HPFS/NTFS
/dev/sda6           30140       30401     2104483+  dd  Unknown
/dev/sda7           27529       28026     4000153+  82  Linux swap / Solaris
/dev/sda8           28027       28648     4996183+  83  Linux
/dev/sda9           28649       30139    11976426   83  Linux

Partition table entries are not in disk order

Output of /etc/fstab :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=36bc0496-64d1-43b7-98bb-b95713940bc3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=11c7d012-14e0-4519-a399-c5424ae12718 /home           ext3    relatime        0       2
# /dev/sda7
UUID=6a04f32a-f535-4f69-af70-144eda76d839 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=9E5EB87C5EB84F31 /media/backup ntfs defaults,umask=007,gid=46 0 0 

UUID=64846CA4846C7B06 /media/backup ntfs defaults,umask=007,gid=46 0 0 

Output of blkid :
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0518" TYPE="vfat" 
/dev/sda2: UUID="9E5EB87C5EB84F31" LABEL="VISTA" TYPE="ntfs" 
/dev/sda5: UUID="64846CA4846C7B06" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: LABEL="MEDIADIRECT" UUID="07D8-0518" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="6a04f32a-f535-4f69-af70-144eda76d839" 
/dev/sda8: UUID="11c7d012-14e0-4519-a399-c5424ae12718" TYPE="ext3" 
/dev/sda9: UUID="36bc0496-64d1-43b7-98bb-b95713940bc3" TYPE="ext3"

---

### Post by iaculallad on 2008-09-16
> **allenbradley said:**
> 
[B][COLOR="DarkRed"]UUID=9E5EB87C5EB84F31 /media/backup ntfs defaults,umask=007,gid=46 0 0 
UUID=64846CA4846C7B06 /media/backup ntfs defaults,umask=007,gid=46 0 0 [/COLOR][/B]

Output of blkid :
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0518" TYPE="vfat" 
/dev/sda2: UUID="9E5EB87C5EB84F31" LABEL="VISTA" TYPE="ntfs" 
/dev/sda5: UUID="64846CA4846C7B06" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: LABEL="MEDIADIRECT" UUID="07D8-0518" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="6a04f32a-f535-4f69-af70-144eda76d839" 
/dev/sda8: UUID="11c7d012-14e0-4519-a399-c5424ae12718" TYPE="ext3" 
/dev/sda9: UUID="36bc0496-64d1-43b7-98bb-b95713940bc3" TYPE="ext3"


You're using similar mount points for 2 separate partitions. Try this in your terminal:

Create your mount points:

```
sudo mkdir /media/Disk_1
sudo mkdir /media/Disk_2

```

Next thing for you to do is open and edit your fstab file, remove the the texts colored dark red above and replace it with:

```
UUID=9E5EB87C5EB84F31 /media/Disk_1    ntfs    defaults,umask=007,gid=46 0       1
UUID=64846CA4846C7B06 /media/Disk_2     ntfs    defaults,umask=007,gid=46 0       1

```

Save and close the file. While on the terminal:

```
sudo mount -a
```

---

### Post by allenbradley on 2008-09-16
Thanks a lot! I presume this will happen everytime i boot my computer.

---

