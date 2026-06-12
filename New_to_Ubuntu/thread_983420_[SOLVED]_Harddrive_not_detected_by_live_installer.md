---
title: "[SOLVED] Harddrive not detected by live installer"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by NESFreak on 2008-11-15
I decided to install 8.10 and to completely erase my ubuntu partition (made a backup of my homedir), only for some reason the livecd cannot access my harddrive. fdisk -l shows "Cannot open /dev/sda"
and both de installer and gparted show my complete harddrive as "unallocated" Which (i'm sure) isn't the case, since whenever i reboot grub starts normally and both vista and ubuntu 8.04 still work.
How come the installer doesn't detect my harddrive's geometry/how do i fix it?

thanks (btw it's a dell xps m1330 with a 320Gb harddrive model ATA WDC WD3200BEVT-7)
----
[http://ubuntuforums.org/showthread.php?t=982896](http://ubuntuforums.org/showthread.php?t=982896)
mentions the same problem. it didn't show up in the search results of my query i did before posting for some reason, but someone replied to that thread some minutes ago so...

---

### Post by Duck2006 on 2008-11-15
You did try,

sudo fdisk -l

---

### Post by NESFreak on 2008-11-15
> **Duck2006 said:**
> You did try,

sudo fdisk -l

lol i forgot(thought the livecd was ROOT, but it just doesn't asks for a pwd after you sudo), but that still doesn't explain the gparted/installer problem

---

### Post by Duck2006 on 2008-11-15
Have you tryed the live cd of gparted or parted magic?

---

### Post by NESFreak on 2008-11-15
i think i found the problem
For some reason one of my partitions is named both sda1 and sda5
```
Command (m for help): v
Warning: partition 1 overlaps partition 5.
269780 unallocated sectors

Command (m for help): p

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       29055   222772461    7  HPFS/NTFS
/dev/sda4           29056       38914    79185538    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           29056       38193    73400953+  83  Linux
/dev/sda7           38194       38586     3156741   82  Linux swap / Solaris

Partition table entries are not in disk order

```

is it save to just remove /dev/sda5?

---

### Post by Duck2006 on 2008-11-15
> **NESFreak said:**
> i think i found the problem
For some reason one of my partitions is named both sda1 and sda5
```
Command (m for help): v
Warning: partition 1 overlaps partition 5.
269780 unallocated sectors

Command (m for help): p

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       29055   222772461    7  HPFS/NTFS
/dev/sda4           29056       38914    79185538    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           29056       38193    73400953+  83  Linux
/dev/sda7           38194       38586     3156741   82  Linux swap / Solaris

Partition table entries are not in disk order

```

is it save to just remove /dev/sda5?

> /dev/sda5           38587       38914     2620416   dd  Unknown

This is the partition you mean?

You could and make a new partition or add it to one of the other partitions.

---

### Post by NESFreak on 2008-11-15
> **Duck2006 said:**
> This is the partition you mean?

You could and make a new partition or add it to one of the other partitions.
yes, that's the one. Adding it to one other wouldn't make much sense, would it? Since it's just a duplicate reference to one already occupied area. But my question is. Would removing it just remove the duplicate reference or would it remove all the data in sda1?

---

### Post by Duck2006 on 2008-11-15
As far as i know yes it would.

---

### Post by NESFreak on 2008-11-15
turned out /dev/sda1 was causing the problems. so now i removed them both. See this partition contained dell mediadirect which is some never-to-be-used mediacenter thing. in order to install ubuntu i had to move sda1 to sda5 (extended partition since all four partitions were already in use at the default setup, so just resizing wouldn't help. So i guess mediadirect didn't like that and screwed up my setup)

anyway removing 'both' mediadirect partitions killed grub, but that was easy to fix. So..

SOLVED

---

### Post by Duck2006 on 2008-11-15
Nice to hear.

---

