---
title: "How do i format an mp3 player?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Funky91 on 2008-05-05
I have a samsung yp-z5 which used to work fine but has now stopped letting me write to it in Ubuntu (tho i can in windows).

From reading other posts on this forum it seems like it's worth formatting it to see if that helps.

How do I go about doing this?

---

### Post by fahadsadah on 2008-05-05
Please mount the MP3 player (plugging it in should do), then please post the output of ```
sudo fdisk -l
``` here.
Thank you very much.

---

### Post by Funky91 on 2008-05-05
```
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b024b01

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14690   117997393+   7  HPFS/NTFS
/dev/hda2           14691       14946     2056320    f  W95 Ext'd (LBA)
/dev/hda5           14691       14946     2056288+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10240274432 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x827ff18c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1186     9526513+  83  Linux
/dev/hdb2            1187        1244      465885    5  Extended
/dev/hdb5            1187        1244      465853+  82  Linux swap / Solaris

Disk /dev/sda: 970 MB, 970321920 bytes
252 heads, 8 sectors/track, 940 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         941      947552    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(928, 251, 8) logical=(940, 11, 8)

```

---

### Post by fahadsadah on 2008-05-05
The command would be 
```
sudo mkfs.vfat /dev/sda1
```

---

### Post by Funky91 on 2008-05-05
Thanks, that seems to have done the trick!!

---

### Post by fahadsadah on 2008-05-05
You're welcome!
Please mark this thread as 'Solved'.

---

### Post by Funky91 on 2008-05-05
i really should know this but....

how do i mark it as solved??

---

