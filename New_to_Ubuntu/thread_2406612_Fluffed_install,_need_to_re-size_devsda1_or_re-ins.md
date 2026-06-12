---
title: "Fluffed install, need to re-size dev/sda1 or re-install?"
date: 2018-11-23
forum: New to Ubuntu
---

### Post by nathanwilliams2 on 2018-11-23
Hello All,

In a bit of a bind here, I was rushing a dual-boot install, and seem to have give the boot drive a size of 10GB.


 [ATTACH=CONFIG]281746[/ATTACH][ATTACH=CONFIG]281747[/ATTACH]

Whilst documents can be stored in the new partition (dev/sda7), the user needs to install programs in the home directory (dev/sda1), ideally I would like for this partition to have all.

Please could you let me know what the options are here? Am I looking at a complete re-install?

Many thanks for input and advise,

Nathan

---

### Post by nathanwilliams2 on 2018-11-23
I ended up re-installing completely with the bulk of the storage in root rather than home, per user requirements.

---

### Post by Impavidus on 2018-11-23
It's a bit late now as you already reinstalled, but this may enlighten you.

Your sda1 in the second screenshot is an EFI partition. It contains hardly anything, but must be there for technical reasons.
sda2, I don't know.
sda3 is the main Windows partition. I guess that's where your Windows OS lives. Note that Ubuntu can read and write to Windows partitions, but it's generally not recommended to write to the Windows C partition, as it's very easy to damage Windows that way. If you want to share files between Windows and Ubuntu, best to use a separate NTFS data partition, which will probably be known to Windows as D:/.
sda5 is, as you say, your Ubuntu root partition. At 10GB it's a bit small.
sda6 is a swap partition. At 32GB it's ridiculously large. Unless you want to hibernate or do something that needs really a lot of ram, don't make swap larger than 2GB or so. If you want to enable hibernation (not really recommended), make swap slightly larger than ram. Think about how long it takes to write 32GB to swap space. That's something you never want to do.
sda7 is your /home partition. Good, it's considered best to keep user documents and the operating system on separate partitions. It's easier for backups and reinstalling the OS.
sda4 looks like a Windows recovery partition.

The best way to fix your problem would have been to shrink the swap partition and expand the root partition.

---

