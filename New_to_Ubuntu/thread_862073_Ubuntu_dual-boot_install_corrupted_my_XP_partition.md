---
title: "Ubuntu dual-boot install corrupted my XP partition!"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by mingle on 2008-07-17
Hi,

Not sure if this is a bug, or just my bad luck!

I booted the Ubuntu 8.04 CD and installed it along side my current XP SP3 install. During the Ubuntu partition phase I resized the XP (NTFS) partition by dragging the partition 'divider' bar and made it slightly larger than the suggested size (that the installer showed).

Once Ubuntu was installed, all seemed okay and I booted into Ubuntu to run the software updates and get it all configured.

However when I tried to boot into XP, it crashed (a warm reset) just after the XP logo and progress bar appeared. Even safe mode wouldn't work.

I booted from my rescue CD and had a quick look at the partitions on the hard disk. Partition Magic reported three errors and also said that the partitions were overlapped.

In the end the only way I could get XP working was to remove the Ubuntu partition (after an hour of install and updates! boo-hoo!) and boot from my XP CD and rewrite the MBR using the recovery console.

I'm very wary of trying it again.

Has anyone else run into this type of problem and are there any know issues with the Ubuntu partitioning tool?

Cheers,

Mike.

---

### Post by Canis familiaris on 2008-07-17
Hi Mike
Did you defragment the WinXP partition you resized before you installing Ubuntu?

---

### Post by mingle on 2008-07-17
Hi there,

No defrag. I wouldn't have thought that would cause any issues. The partitioning tool should shuffle any used blocks out of harms way.

I've done this on another machine (dual boot Ubuntu & XP) without any issues (and that had a smaller hard drive with less free space...

Cheers,

Mike.

---

### Post by lisati on 2008-07-17
It probably won't hurt to delete temporary files before you defrag, and sometimes defragging two or three times can make a difference too. 

A Windows command-line utility (with FreeBasic source) to remove some of the temporary files that the standard Windows disk cleanup utility misses is attached.

---

