---
title: "[SOLVED] Unknown Filesystem Errors in Grub due to Format Change in Partition"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by greenmm on 2013-03-12
This is completely user Noob error

I was installing Ubuntu 12.04 side-by-side with my Windows 8 setup via a LIVEUSB setup onto an ext-4 partition. I changed the secure boot settings and installed boot-repair and it was all running smoothly. So I booted Windows and decided to see if my USB drive would still work by dragging a document into it. In my haste, I put the document into the Ubuntu partition and Windows told me the partition was not formatted properly (must've not recognized the ext-4 filesystem?) and prompted me to reformat it into either NTFS or FAT-32. I quickly clicked reformat to NTFS and subsequently face-palmed myself realizing it was the Ubuntu partition I had reformatted, not my USB drive. Here is what I am getting on my screen:

```
error: unknown filesystem.
grub rescue> ls
(hd0) (hd0,gpt1) (hd0,gpt2) ... (hd0,gpt8)
grub rescue> ls (hd0)/
error: unknown filesystem.
grub rescue> ls (hd0,gpt1)/
error: unknown filesystem.
```

It continues on like this and gives the same error for all the partitions. I have no idea what to do. Any help would be GREATLY appreciated!

---

### Post by fantab on 2013-03-12
Well, you messed it up AFAIK. **REINSTALL UBUNTU**. Recovery may not work.

Windows does not recognize Linux File-systems and it will ask if you want to re-format. That should have been your first clue.
Lets say you have learnt an important lesson in dual booting. I hope you will be careful in future.

---

### Post by greenmm on 2013-03-12
A lesson learned indeed. Held down F2 F8 F10 F12 at the same time to open BIOS and boot liveUSB. Reinstalled

---

