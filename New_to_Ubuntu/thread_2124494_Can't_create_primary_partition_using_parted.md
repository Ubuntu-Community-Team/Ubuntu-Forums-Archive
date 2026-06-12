---
title: "Can't create primary partition using parted"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by monsterdenny on 2013-03-11
I tried to create a new primary partition using parted. However system can't detect extra diskspace.

```


(parted) print
Model: ATA QEMU HARDDISK (scsi)
Disk /dev/sda: 5369MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1.05MB  256MB   255MB   primary   ext2         boot
 2      257MB   3220MB  2963MB  extended
 5      257MB   3220MB  2963MB  logical                lvm

(parted) mkpart primary 0MB 2000MB
Warning: You requested a partition from 0.00MB to 2000MB.
The closest location we can manage is 0.00MB to 1.05MB.
Is this still acceptable to you?
Yes/No? no



```

Help! Thanks.

---

### Post by Cheesemill on 2013-03-11
Of course you can't create a partition between 0MB and 2000MB, that space is already occupied by other partitions.

If you look at the output of print you can see that the only unused space lies between 0MB and 1.05MB, and between 3221MB and 5369MB.

If you are unsure about what you are doing when partitioning a drive may I suggest using gparted from a Live CD instead, it will give you a nice graphical overview of your drive which makes partitioning much easier.

---

### Post by monsterdenny on 2013-03-11
It's working now. Thanks.

---

