---
title: "Mounting Issues"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-27
One of my HD's won't mount/does mount but can't be accessed/found/dated etc.

here's FDISK -L :- 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156286976    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78148604   83  Linux
```

If i try to unmount the disk i get told : - 

```
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /media/disk: not mounted

```

Which confuses me cos partition manager says it's mounted and i can't unmount it, but it's not mounted according to the above. Hmmm..

Obviously i don't wanna be messing with my fstab (is that right?) unless i know what i'm doing.

Is there a way to unmount then remount and 'fix' this mounting issues.

I think i over used the word 'mount'. Hmm.... lol

---

### Post by scorchgeek on 2008-10-27
This doesn't sound like Linux, but have you tried rebooting?

---

### Post by Xiong Chiamiov on 2008-10-27
First, it's fdisk -l, with a lowercase.  You obviously entered it correctly, but be aware that Linux is case-sensitive.

Your problem is that you're adding a colon (:) at the end of the path.  In the fdisk output, the colon is simply specifying that there is information following it; umount, however, assumes that everything preceeding the colon is a host name (used when mounting remote drives).

You can also umount using the /dev name:
```

sudo umount /dev/sdb1

```

EDIT:
Actually, I'm not quite sure what you're doing when trying to unmount.  Use the syntax I put above, though.

---

### Post by joey-elijah on 2008-10-27
> **Xiong Chiamiov said:**
> First, it's fdisk -l, with a lowercase.  You obviously entered it correctly, but be aware that Linux is case-sensitive.

Your problem is that you're adding a colon (:) at the end of the path.  In the fdisk output, the colon is simply specifying that there is information following it; umount, however, assumes that everything preceeding the colon is a host name (used when mounting remote drives).

You can also umount using the /dev name:
```

sudo umount /dev/sdb1

```EDIT:
Actually, I'm not quite sure what you're doing when trying to unmount.  Use the syntax I put above, though.

Lol thanks for the reply, but i wrote FDISK -L in capitals for purposes of the post - it was all lover case in the terminal hence getting the output. 

The semi-colon is also just part of my post - it's a grammar thing: when you're giving an example that's a paragraph/break away you use ': - " that's all. I didn't enter this into the terminal. 

I have already tried unmounting with the 'umount' command - but i get the same error as above: that it's busy/is in use.

I have rebooted several times, but still no joy.

---

