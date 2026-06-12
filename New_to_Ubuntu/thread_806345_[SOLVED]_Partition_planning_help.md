---
title: "[SOLVED] Partition planning help"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by StupidMonkey on 2008-05-24
Im trying to map out partitions effectively, and want to make sure im on the right track. With the Linux partitions, I would like to be able to re-install them with out losing much.

With a 320 GB Harddrive, this is what I have come up with so far:

1 Primary NTFS WindowsXP
1 Primary NTFS for Programs/Games (Wine)/Backups (to reinstall XP whenever, without losing much)
1 Logical Ubuntu
-- 1 EXT3 partition for root
-- 1 EXT3 partition for /home
1 Logical OtherLinux (not yet determined)
-- 1 EXT3 partition for root
-- Share Ubuntu's /home partition
1 SWAP

I have 4 GB of RAM, should my swap really be 8 GB?

And is it possible to have a shared partition for Linux programs? So I dont have duplicates of programs for use on both distros.

---

### Post by perce on 2008-05-24
> **StupidMonkey said:**
> 
I have 4 GB of RAM, should my swap really be 8 GB?


No, with 4 GB of RAM you'll probably never use any swap. The only thing a 
swap partition is worth for you is hibernate (aka suspend to disk). If you want to be able to suspend to disk, your swap must be a little bigger than your RAM, but it doesn't have to be the double. 4,1 GB will be enough.

> 
And is it possible to have a shared partition for Linux programs? So I dont have duplicates of programs for use on both distros.

It's going to be a mess: the two distros will have different libraries, and maybe even different package managers. I think it is techically possible if you work hard enough, but you'd have a huge chance to brake your system every time you install some software.

---

### Post by CloudFX on 2008-05-24
This will not work.  A harddrive can only have up to 4 main partitions and 1 extended partition.

---

### Post by perce on 2008-05-24
> **CloudFX said:**
> A harddrive can only have up to 4 main partitions and 1 extended partition.

No, up to 4 partition, at most one of which can be extended. But an extended 
partition can contain several logical partitions, so if he does his partition correctly he can do what he wants.

---

