---
title: "Entire hard drive is unallocated space, but my partitions are still there."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by FuzzieLogic on 2008-08-17
Hi everyone,

This isn't EXACTLY Ubuntu related, but the only way I can really use my computer right now is through the Ubuntu Live CD, so I really hope you folks can help me out a little. Thanks in advance.

I had a dual boot of Windows and Ubuntu on my computer, and Windows was getting all slow and nasty so decided to just reinstall it. I booted from the Windows XP install CD and deleted my Windows partition, hoping to recreate the NTFS partition, reinstall Windows on it, and life would go on, etc. 

EXCEPT - the Windows installer wouldn't let me recreate an NTFS partition in the (now) unallocated space, because I had reached my maximum number of partitions or something. So I thought I'd use GParted on the Ubuntu Live CD to sort my partitions out, but now the entire hard drive just shows up as unallocated space.

However, *sudo fdisk -l* shows this:

```

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2            5228        5619     3148740   db  CP/M / CTOS / ...
/dev/sda3            5620       19452   111113572+   5  Extended
/dev/sda4           19192       19452     2096482+  82  Linux swap / Solaris
/dev/sda5            5620       17852    98261509+  83  Linux
/dev/sda6           17853       18224     2988058+  83  Linux
/dev/sda7   *       18225       19191     7767396   83  Linux

```

So it looks like my partitions are still there. There's got to be a way to recreate my NTFS partition and get my computer back to the way it was before - could anyone please be kind enough to help?

Also, I realize now that once I reinstall windows, the computer will just act as if Ubuntu doesn't exist because GRUB won't be there anymore - any ideas on how to go about fixing that would also be greatly appreciated.

---

### Post by ingeva on 2008-08-17
> **FuzzieLogic said:**
> 
omitting empty partition (5)


To me it looks like this:
There are two primary partitions on the disk.
The third one is unallocated (from cylinder 6 to 5227), and I guess that's the one that makes Windows misunderstand the partition structure.
The first partition is a Dell service partition. The partition type is undetermined (Dell special). You can probably remove it without getting into trouble, but I think that it might be a good idea to call Dell service and ask them if you risk anything. Probably not.
The second partition is probably a remnant of an old Windows partition, and the strange partition type is probably caused by something going wrong earlier. If you don't mind deleting old Windows files, just let that go too.

If you remove these two partitions, check that you have one consecutive unallocated area on the disk. Create a new primary partition there. It could be anything. If you install Windows in it it will be made active. Use a live CD to activate (make bootable) the linux partition instead. GRUB is probably there already and you may ber able to boot Linux. If not its because the partition number has changed, and you will have to make some changes in the GRUB startup definitions. I'm not the right person to tell you, because I run a clean Ubuntu system and don't use grub.

Good luck!

EDIT: Come to think of it; fdisk actually tells you that there is a partition in the "unallocated space" but it's empty. By using gparted from a live CD you might be able to figure it out and correct the situation.

---

### Post by FuzzieLogic on 2008-08-17
Hi ingeva, thank you for the quick response.

I see the unallocated space in cylinders 6 - 5227. How exactly do I create a new partition in there, and format it as NTFS? GParted on the ubuntu live CD just shows the entire disk as unallocated space, which isn't really going to help me.

> The second partition is probably a remnant of an old Windows partition, and the strange partition type is probably caused by something going wrong earlier. If you don't mind deleting old Windows files, just let that go too.

Are you talking about sda2, with the system "CP/M / CTOS / ..."? If it is indeed a messed up windows partition, I have no problem getting rid of it.

**EDIT:** Never mind, I decided to just scrap some of my linux partitions (root, /swap, /home) so Windows would let me recreate the NTFS partition, and now GParted shows my partitions again. Weird. Anyway, thanks for your help.

---

### Post by ingeva on 2008-08-17
> **FuzzieLogic said:**
> shows my partitions again. Weird. Anyway, thanks for your help.

I would just add this:
I think it's a good idea to not make more partitions than needed. The larger a partition the better the space will be utilized. However, there are other considerations (for instance if a large partition fails you lose more), and when you share with Windows in a dual-boot configuration, you might want to share at least one partition between them. I would recommend NTFS in that case, since Ubuntu can read and write on it, and it's fairly stable (Well, it IS Windows .... :) )

The definition of partitions is such that a disk can have max 4 partitions. However, some time in the old ages when disks became larger than 32MB, someone came up with the idea of the extended partition, which can be divided into logical ones. Windows can utilize one primary partition and one extended, plus logical partitions. I'm not sure if it can use more than one primary partition, but theoretically it's possible (other systems do).

I see that you have found a solution, and that's fine. I just hope my little partition seminar could be useful for someone! :)

You should mark the thread as solved.

---

