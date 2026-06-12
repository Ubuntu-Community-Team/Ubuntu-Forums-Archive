---
title: "[SOLVED] mount drive on startup"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by ibbill on 2008-11-06
All are mounted but the hilighted drive I can not get it to mount up the others mount up on boot up attaching pic 

one drive with 4 partitions xp on 1 partition ubuntu 8.10 and 2 spare partitions for music and pictures.

also have a external drive with 2 partitions with stuff saved on both.

all mount on boot up but the 33.5 gb media.

---

### Post by porchrat on 2008-11-06
in order to automount a volume it needs to be added to the /etc/fstab file.  However before you do this you need the drives UUID.  To discover which drives are which please run these 2 commands:

```
sudo fdisk -l
```

```
sudo blkid
```

can't remember if you need sudo for the blkid command (I don't think you do, but I'm not in front of the ubuntu machine at the moment).

---

### Post by dracayr on 2008-11-06
please post the output of "cat /etc/fstab". 

and *please* write in full sentences and correct grammar. I see you come from Canada, so you should be able to manage that.

dracayr

---

### Post by ibbill on 2008-11-06
> **porchrat said:**
> in order to automount a volume it needs to be added to the /etc/fstab file.  However before you do this you need the drives UUID.  To discover which drives are which please run these 2 commands:

```
sudo fdisk -l
```

```
sudo blkid
```

can't remember if you need sudo for the blkid command (I don't think you do, but I'm not in front of the ubuntu machine at the moment).
thanks for your help
Here is my output from the above 2 commands

ibbill@ibbill-desktop:~$ sudo fdisk -l
[sudo] password for ibbill: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4073    32716341    7  HPFS/NTFS
/dev/sda2            4074        6623    20482875   83  Linux
/dev/sda3            6624        8918    18434587+   7  HPFS/NTFS
/dev/sda4            8919        9725     6482227+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fa40d87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11535    92654856    7  HPFS/NTFS
/dev/sdb2           11536       19457    63633465    7  HPFS/NTFS
ibbill@ibbill-desktop:~$ sudo blkid
/dev/sda1: UUID="2AF02D5BF02D2E8F" TYPE="ntfs" 
/dev/sda2: UUID="dc1b56e5-46a3-4617-9440-2dc204cefa0e" TYPE="ext3" 
/dev/sda3: UUID="068CC7C28CC7AA8F" LABEL="New Volume" TYPE="ntfs" 
/dev/sda4: UUID="222CD04C2CD01D1B" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="B44A88FE4A88BF1C" TYPE="ntfs" 
/dev/sdb2: UUID="D860619960617F5E" LABEL="New Volume" TYPE="ntfs" 
ibbill@ibbill-desktop:~$ ~

---

### Post by ibbill on 2008-11-06
> **dracayr said:**
> please post the output of "cat /etc/fstab". 

and *please* write in full sentences and correct grammar. I see you come from Canada, so you should be able to manage that.

dracayr

Okay will do better next time.

Post of the output of "cat /etc/fstab".

ibbill@ibbill-desktop:~$ "cat /etc/fstab". 
bash: cat /etc/fstab.: No such file or directory
ibbill@ibbill-desktop:~$ "cat /etc/fstab"
bash: cat /etc/fstab: No such file or directory
ibbill@ibbill-desktop:~$ sudo "cat /etc/fstab"
[sudo] password for ibbill: 
sudo: cat /etc/fstab: command not found
ibbill@ibbill-desktop:~$

---

### Post by ibbill on 2008-11-07
> **porchrat said:**
> in order to automount a volume it needs to be added to the /etc/fstab file.  However before you do this you need the drives UUID.  To discover which drives are which please run these 2 commands:

```
sudo fdisk -l
```

```
sudo blkid
```

can't remember if you need sudo for the blkid command (I don't think you do, but I'm not in front of the ubuntu machine at the moment).

thanks for your help I used this program to mount the drive

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

---

