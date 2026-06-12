---
title: "Attempting an uninstall"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Crono139 on 2008-05-28
Don't worry. This will be followed by a clean reinstall.


I followed the step-by-step guide on this forum. On Windows, I performed the mbrfix, which I believe worked, but there was no message to confirm it.

After that, I booted from the Ubuntu LiveCD, and opened up GParted. Some of the drivers were listed as read-only (a message popped up in the terminal). GParted loaded, so I tried to delete the Linux swap, and ext3 partitions, but that failed. swap is locked, and ext3 tells me to unmount any partitions having a higher number than 5. 

Now, when I reboot my system, it loads right into Windows. The GRUB doesn't load.

Suggestions?

---

### Post by quelx on 2008-05-28
Ubuntu was installed in extended partitions, you need to remove the extended partition container (probably /dev/sda2)

From the live CD open a terminal and type ```
sudo swapoff /dev/sda5
``` (I'm guessing here but swapoff won't hurt anything) then try gparted again.

---

### Post by Crono139 on 2008-05-28
> **quelx said:**
> Ubuntu was installed in extended partitions, you need to remove the extended partition container (probably /dev/sda2)

From the live CD open a terminal and type ```
sudo swapoff /dev/sda5
``` (I'm guessing here but swapoff won't hurt anything) then try gparted again.

```
ubuntu@ubuntu:~$ sudo swapoff /dev/sda5
swapoff: /dev/sda5: Invalid argument
```

sda5 is ext3, and sda6 is swap.

---

### Post by quelx on 2008-05-28
then ```
swapoff /dev/sda6
```

---

### Post by Crono139 on 2008-05-28
That did the trick. It is now listed as 5.77GB of unallocated space under /dev/sda2 Extended, and the flag shown is lba.

How do I combine this space with my Windows partition?

---

### Post by Crono139 on 2008-05-28
Bump.

---

### Post by quelx on 2008-05-28
You can't combine it, but if it's free now you can grow the windows partition.

---

### Post by Crono139 on 2008-05-28
> **quelx said:**
> You can't combine it, but if it's free now you can grow the windows partition.

GParted says the Windows partition is at its maximum size with no free space to work with.

---

### Post by quelx on 2008-05-28
then the other partitions have not all been deleted.  open a terminal and post the output of ```
sudo fdisk -l /dev/sda
```

---

### Post by Crono139 on 2008-05-28
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8845    71047431    7  HPFS/NTFS
/dev/sda2            8846        9598     6048472+   f  W95 Ext'd (LBA)
/dev/sda3            9599        9729     1052257+  d7  Unknown
```

---

### Post by quelx on 2008-05-28
what is on /dev/sda2 (the fat32 partition)?

---

### Post by Crono139 on 2008-05-28
> **quelx said:**
> what is on /dev/sda2 (the fat32 partition)?

Nothing. That is the partition that Ubuntu was installed on.

---

### Post by quelx on 2008-05-28
> **Crono139 said:**
> ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8845    71047431    7  HPFS/NTFS
/dev/sda2            8846        9598     6048472+   f  W95 Ext'd (LBA)
/dev/sda3            9599        9729     1052257+  d7  Unknown
```

Delete partition 2 and 3 with fdisk and see if gparted will let you resize then.

from the terminal

```
sudo fdisk /dev/sda
```

(hit **Enter** after each step)
**d** > **2** > **d** > **3** > **w**

fire up gparted, see if you can resize

---

### Post by Dougie187 on 2008-05-28
That should all be stuff you can do with gparted though. gparted should allow you to delete all the partitions first and then resize the windows partition.

---

### Post by Crono139 on 2008-05-28
I deleted sda2, and combined the newly found free space with the Windows partition.

I left sda3 because I **believe** that it's the HP QuickPlay partition that I use in Windows.

Thanks for your help!

---

