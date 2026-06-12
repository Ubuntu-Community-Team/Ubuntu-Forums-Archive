---
title: "unable to allocate space to my /home directory"
date: 2016-05-15
forum: New to Ubuntu
---

### Post by Megh_Tripathy on 2016-05-15
I have / root directory has file system /dev/sda1 with 19G space
I want to add space  some more space to /home directory but unable to do it while running below command
$sudo mkfs -t ext4 /dev/sda2
mke2fs 1.42.9 (4-Feb-2014)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
 filesystem with 0 blocks, specify higher inode_ratio (-i)
 or lower inode count (-N).

#lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0    55G  0 disk 
&#9500;&#9472;sda1   8:1    0    19G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0  1022M  0 part [SWAP]
sr0     11:0    1    33M  0 rom 
  

Please suggest 


Thanks,
Megh

---

### Post by steeldriver on 2016-05-15
Is sda2 an extended partition by any chance (i.e. just a container for the sda5 swap partition)? please post the output of

```

parted /dev/sda print

```
or
```

fdisk -l /dev/sda

```

(and please use CODE tags)

---

### Post by HermanAB on 2016-05-15
Note that you cannot change a mounted partition.  So boot off a CD or USB memory schtick to do that.

---

### Post by Megh_Tripathy on 2016-05-15
Model: VMware, VMware Virtual S (scsi)
Disk /dev/sda: 59.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  20.4GB  20.4GB  primary   ext4            boot
 2      20.4GB  21.5GB  1072MB  extended
 5      20.4GB  21.5GB  1072MB  logical   linux-swap(v1)

---

### Post by grahammechanical on 2016-05-15
If /home is a directory/folder under root ( / ) on sda1 (20 GB) then you cannot increase the size of /home unless you increase the size of / (sda1).

---

### Post by Impavidus on 2016-05-15
The easy way is to run gparted (from a live disk if you wish, but it should be possible from the installed system), disable swap and expand sda2 to the right end of the disk. Then create a new ext4 partition (will be called sda6) to the right of the swap partition. Finally [move /home to the new partition]("https://help.ubuntu.com/community/Partitioning/Home/Moving"). This will give you a 20GB root partitions and a 38GB /home partition, which is quite decent. If you want something different, it gets more complicated (although doable), so you'd better start from scratch.

---

### Post by Megh_Tripathy on 2016-05-15
then how to increase the size of sda1?

---

### Post by Impavidus on 2016-05-16
If you want to expand sda1 (which is not what I suggest), you have to boot from a live disk. Then switch swap off, delete sda5 and sda2, recreate sda2 (extended) and sda5 (swap) near the end of the disk, switch swap on and expand sda1. Make sure you have a backup of everything in sda1, as modifying partitions may cause data loss when something goes wrong (power failure for example, or clicking the wrong button). Then update your /etc/fstab so that your system finds the swap partition, which now has a new UUID.

---

