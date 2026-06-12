---
title: "saturday night Partition trouble"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Mudguard on 2008-11-29
Just finished an xp ubuntu dual boot, the plan was to set up a shared disk partition to share between the two, but unfortunately i've now got both xp and ubuntu working but have no access to the 35gb partition inbetween...
Would be good to get it back to use either in ubuntu or xp..

Does anyone know can it be done at this stage or do i need to reinstall!? any advice would be great...

---

### Post by Xiong Chiamiov on 2008-11-29
I'm a bit confused as to what your current disk setup is, and what you want it to be.

Does GParted show any free (unpartitioned) disk space?

What is the output of
```

sudo fdisk -l

```

---

### Post by Mudguard on 2008-11-29
Sorry.. Could've been clearer there! Was wondering does anyone know if partition can be edited with Gpart, the ubuntu partitioning tool, think i messed up on the mount point.. can this be edited or perhaps formatted the partition now at this stage..

---

### Post by Mudguard on 2008-11-29
I've now got 20gb xp ntfs, 20gb ubuntu ext3, and 32gb reiserfs, flaged lba, mount point /home.. i wanted to set it up as a fat32 but was unable to and from reading other threads... set it up as it now is..

---

### Post by Xiong Chiamiov on 2008-11-29
So the ext3 partition is where Ubuntu is installed, and the reiser if mounted as /home?  The output of that fdisk command I gave you earlier would really be helpful.

---

### Post by Mudguard on 2008-11-29
Again sorry, gettin tired here!!..
here it is..

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          10       80293+   6  FAT16
/dev/sda2              11        2560    20482875    7  HPFS/NTFS
/dev/sda3            2561        9318    54283635    f  W95 Ext'd (LBA)
/dev/sda4            9319        9729     3301357+  82  Linux swap / Solaris
/dev/sda5            2561        6768    33800728+  83  Linux
/dev/sda6            6769        9318    20482843+  83  Linux

---

### Post by Xiong Chiamiov on 2008-11-29
No worries, we all get tired when we're trying to fix things.

You have 2 ext3 drives, it looks like, inside of an extended partition, along with your swap.  Your FAT partition is extremely small, but I'm not sure if you'll need to keep that for your bootloader.

Could you also do me a favor and post the output of
```

mount

```

---

