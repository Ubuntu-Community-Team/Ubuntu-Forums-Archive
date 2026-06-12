---
title: "Mounting issue with external drive"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Blojic on 2008-05-07
Hello,

I have an old 2.5" HDD I've salvaged from my old Viao laptop (30GB in two 15GB partitions (XP-NTFS)). I've been trying to retrieve the data from it before I skip it (photos etc) but I'm having problems seeing the first partition.

I put it into an IDE enclosure to see if the drive could be seen via USB. In windows it recognised it as an external drive but gave the usual "This drive is not formatted, do you...." spiel.

In Hardy (AMD64) it seemed to automount lovely, but only the second partition apears in the file manager - no sign of the primary (XP) partition.

Does anyone know of a way around this? - I've read elsewhere on this forum that there can be issues if Windows wasn't shut down correctly, and this is quite probably true - I remember I had problems with that laptop overheating for months (two years ago!) and it got to the stage - after thumping it! - that it wouldn't boot.

I understand it's probably a gonner but, as the secondary partition is visible, I thought I'd give you geniuses a try just in case before it gets the hammer and all my treasured memories are lost forever...

Cheers,

---

### Post by glennric on 2008-05-07
When you have the disk in try running
```
sudo fdisk -l
```
from a terminal.  Post the output here.

---

### Post by Blojic on 2008-05-07
> **glennric said:**
> When you have the disk in try running
```
sudo fdisk -l
```
from a terminal.  Post the output here.

That was quick.

I won't be in front of the machine until 1900BST (5 hours, but I will then.

Thanks for the swift reply.

Cheers,

---

### Post by Blojic on 2008-05-07
```
blob@blob-desktop:~$ sudo fdisk -l
[sudo] password for blob: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29142913

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000979d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9660    77593918+  83  Linux
/dev/sdb2            9661       10011     2819407+   5  Extended
/dev/sdb5            9661       10011     2819376   82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a3aa445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1828    14683378+   7  HPFS/NTFS
/dev/sdc2            1829        3648    14619150    f  W95 Ext'd (LBA)
/dev/sdc5            1829        3648    14619118+   7  HPFS/NTFS
blob@blob-desktop:~$ 
```

This is what I get.

I have no idea how to manually mount volumes and so (as I've been brainwashed by DOS <C: A: etc> for 20-odd years) any explanation or a pointer to an easy-to-read tutorial of the Linux filesystem principles would be appreciated.

Cheers,

Blob

---

### Post by Blojic on 2008-05-08
Bump!):P

---

### Post by njparton on 2008-05-08
Is it /dev/sdc1 that you're trying to access?
 
Do you have ntfs-3g installed?

---

### Post by Blojic on 2008-05-08
Not too sure. I've got it plugged into my lapThis istop this morning. This is the new fdisk output...
> blob@Laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x341b341b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         615        4145    28362757+   7  HPFS/NTFS
/dev/sda2               1         614     4931923+  12  Compaq diagnostics
/dev/sda3            4146        9373    41993910   83  Linux
/dev/sda4            9374        9729     2859570   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a3aa445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1828    14683378+   7  HPFS/NTFS
/dev/sdb2            1829        3648    14619150    f  W95 Ext'd (LBA)
/dev/sdb5            1829        3648    14619118+   7  HPFS/NTFS
blob@Laptop:~$ 
It's sdb but this drive is 30GB drive - sdb adds up to 45?

I assume it's sdb1 but not sure. ny ideas?

I haven't installed ntfs-3g - I thought NTFS read/write was built in now?

Thanks,

---

### Post by Blojic on 2008-05-08
```
blob@Laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/oldc
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
blob@Laptop:~$ 
```
I've just tried this.

Does this mean that it's had it?

---

### Post by vanadium on 2008-05-08
Your fdisk -l output suggests that the partition table of the drive is OK. However, if even Windows cannot open partition sda1, then there are severe problems with it.

In this case, I am afraid that the situation is pretty bad. You won't be able to repair it under Windows using standard tools because the partition is not anymore recognized as an ntfs file system, even not by Windows. Apart from using specialized tools to recover data, your only option will be to reformat the partition.

---

### Post by Blojic on 2008-05-08
:(

Thanks anyway. What's annoying is that sdb5 mounts fine in Ubuntu automatically. XP can't even see that, not even in Disk Manager - it thinks it's a blank unpartitioned space.

I knew that the drive was a bit flakey - it makes all sorts of noises! Never mind, I'll rescue the data from hdb5 and recycle the drive.

One point of confusion - the 3 partitions on the drive add up to more than the total volume. What's that all about?

Thanks for your time,

Blob

---

### Post by talsemgeest on 2008-05-08
Probably one count taking one gigabyte as being 1000 megabytes, another taking it as 1024 megabytes (or 1073741824 bytes)

---

### Post by vanadium on 2008-05-08
```

the 3 partitions on the drive add up to more than the total volume

```

Where do you see that?

---

### Post by Blojic on 2008-05-08
Hmmm, sorry - me being thick.
I was being confused by the Blocks column. I need to do some serious reading if I'm going to master this Ubuntu thing!!!

Ta,

---

