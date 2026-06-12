---
title: "Mounted drives"
date: 2021-06-28
forum: New to Ubuntu
---

### Post by luke316 on 2021-06-28
Hi guys

Kind of new to ubuntu server, can you please help me, all the mounted drives was working perfectly and all of sudden it says cannot connect to server when trying to work from the mapped drives in windows 10, i logged into Ubuntu and i am not atvall able to mount any drive again ans i cannot access any data that i copied earlier

Please please help

---

### Post by TheFu on 2021-06-28
3 questions.

[LIST]
[*]Which Ubuntu release?   Different releases have different capabilities and defaults.
[*]NFS or CIFS?  Those are the 2 most popular network storage protocols. Windows typically uses CIFS.  Noobs typically use CIFS. Unix-people use NFS.
[*]Which file systems are involved on the Linux side?  Partitions that don't use native Linux file systems have limitations, so ext4, xfs, zfs, btrfs, f2fs would be preferred over NTFS, exFAT or FAT32 when connected to Linux.  Much more flexible.
[/LIST]

Oh - and 1 more question.  What did you do last time to have it work?  In Linux/Unix, there are 50-500 ways to accomplish the same thing, through each method will have slightly different to completely different outcomes and limits.

---

### Post by ActionParsnip on 2021-06-28
How are the "drives" connected? What file system do you use in them? Is this a dual boot system?

---

