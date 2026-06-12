---
title: "Missing Hard Disk!?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by twedellj on 2008-07-30
I ran the ubuntu live to test everything out before I did a complete install and everything was fine.

after i did the complete install one of my drives is missing.

i had c: - windows partition
e: slave drive that ubuntu is now on
d: dvd drive
g: usb 40gb drive 


any ideas on how to get this to show?

---

### Post by northern lights on 2008-07-30
Can you clarify which drive/partition is "missing"?

Can you post the output of ```
sudo fdisk -l
```
(that's a lower-case L)

And, as a hint for the future: rid yourself of the concept of drive letters.

---

### Post by twedellj on 2008-07-30
why rid drive letters? they are still labeled under my computer.

c: is the missing one which is my master drive. e: the slave drive and the usb and dvd drive all show but no c: all drives are ntfs

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45e645e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf83ef844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40000536576 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x915964be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4862    39053983+   7  HPFS/NTFS
twedell@twedell-desktop:~$

---

### Post by muteXe on 2008-07-30
well that shows you have 3 drives, so it's still there i think.

---

### Post by mcduck on 2008-07-30
Well, if you installed Ubuntu to the partition known as "e:" for Windows, it only makes sence that Windows now shows one partition less than before. Windows can't read Linux filesystems (without installing some extra third-party driver for it), so it now only has 3 drives it can show.

Most likely that change also caused windows to re-arraange the drive letters. And if you are still able to boot to windowes it's clear that thyour previous windows root partition ("c:") is still there, only with a different name now.

(and the reason why "northern lights" suggested you getting rid of the concept of drive letter is that only Windows uses drive letter to point to drives. They are rather useless in Linux..)

---

### Post by twedellj on 2008-07-30
which is why i think it's weird. because i can't access it from my computer

---

### Post by twedellj on 2008-07-30
ic. ty. so should i just reinstall linux on my master drive or can i just format that drive from within linux and have everything run fine?

---

### Post by mcduck on 2008-07-30
No. If your only problem is that your windows root partition is now known with a different name than "c:", you definitley don't need to do reinstall anything. You can change the drive letters as you wish from the Disk Management in Windows. They are rather meaningless names used by windows to represent different devies and partitions and can be changed as you wish.

If you now see drives c:n d:, e: and g:, and now see only c:, d: and g: I suppose windows had renamed your previous c: into e: (since it can't read the previous e: drive any more as it doesn't understand Linux file systems).

Like I said, if both operating systems are working there's nothing wrong.

---

