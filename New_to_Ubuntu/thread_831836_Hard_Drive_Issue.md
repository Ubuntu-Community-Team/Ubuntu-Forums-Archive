---
title: "Hard Drive Issue"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-06-17
Ok.  I will try to keep this as short as possible.

**First, current hard drive purposes**
1st hard drive:
XP
Ubuntu 8.04

2nd hard drive:
Vista
File Storage Partition
Installed Programs Partition

3rd hard drive:
Backup

**Now for what happened:**

I was in XP and the computer froze...(XP freezing, big surprise huh..lol).  When i rebooted i got an Error 17 with grub.  I then changed my boot order to let the 2nd drive have boot order priority in the bios(2nd hard drive maintains its on MBR because of emergency's like this, but grub usually boots it and bypasses it if i ever need vista).  I booted into vista and i got the error that Chkdisk was aborting due to corrupt Master File Table for the XP partition.  Since that partition has nothing on it that i need due to backups, i reformatted the partition and it is now useable.  My linux partition seems to be intact, however i know i will need to reinstall grub after i reinstall xp back in its partition.  My main question is:  with this problem of the Master File Table with the NTFS partiton, is this purely a data problem of the disk or has the physical integrity of the disk been comprimised? Also any advice from this point would be appreciated.  

Thanks a million in advance!
(and btw the ubuntu community is definately the most supportive online community i have ever witnessed.  Keep it up!!)

---

### Post by SteveHillier on 2008-06-17
It is my understanding that reinstalling Windows will assume it has the whole disk to play with that will thus remove the Linux Partition.
Whenever I have done this sort of thing before I have sacrificed the Linux partition and then rebuilt it.
That is why I no longer dual boot.
This is symptomatic of the wider problem.  Linux acknowledges the existence of Windows but Windows does not recognise Linux.

---

### Post by torgrot on 2008-06-17
I would definitely be looking at doing some hardware diagnostics on that disk.  At the risk of starting a war, NTFS is a fairly robust file system.  To corrupt the Master File Table is not an easy thing for most users to be able to do.  If money is no object, I would just replace the drive.

torgrot

---

### Post by hyper_ch on 2008-06-17
> **SteveHillier said:**
> It is my understanding that reinstalling Windows will assume it has the whole disk to play with that will thus remove the Linux Partition.

No, you can mnaually select into which partition you want to install windows...

---

### Post by ukripper on 2008-06-17
> **hyper_ch said:**
> No, you can mnaually select into which partition you want to install windows...

thats' right as hyper_ch mentioned. you have to manually create partitions after booting with windows installation cd then you will be given options for partitioning your hdd

---

### Post by Mauler5858 on 2008-06-17
> **torgrot said:**
> I would definitely be looking at doing some hardware diagnostics on that disk.  At the risk of starting a war, NTFS is a fairly robust file system.  To corrupt the Master File Table is not an easy thing for most users to be able to do.  If money is no object, I would just replace the drive.

torgrot

What tools would you reccomend for hardware diagnostics?

---

