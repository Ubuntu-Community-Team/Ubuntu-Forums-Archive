---
title: "Swap Partition Sleep/Hibernate"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by levinmiester on 2008-09-15
Hey guys, i just started out with my first linux system ever yesturday :)

A litte confusing, but I'm getting the hang of it. One thing I've noticed is that hibernate does not work the way it is supposed to.
The other thing I've been doing is exploring is the swap partition, the swap and the hibernate are linked... So I'm guessing something is wrong with my swap?

When i do ```
sudo fdisk -l
```

it returns: 

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d8db492

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32468   260799178+   7  HPFS/NTFS
/dev/sda2           37184       38913    13896225    7  HPFS/NTFS
/dev/sda3           32469       37183    37873237+   5  Extended
/dev/sda5           32469       36984    36274738+  83  Linux
/dev/sda6           36985       37183     1598436   82  Linux swap / Solaris

Partition table entries are not in disk order

```

So what to do? And I'm perfectly fine with taking space away from vista!

its a core2duo 2.5ghz  with 4 gigs of ram hp

edit: also, shouldnt sda3 and 5 be one in the same? ext3 and linux?...



thanks in advance!

---

### Post by Harisz750 on 2008-09-15
sda3 is an extended partition that contains sda 5 & 6

your ram is 4 giga... so your swap partition should be twice the ram ... in other words.. 8 giga.. that causes problem with the hibernate thing

---

### Post by levinmiester on 2008-09-15
> **Harisz750 said:**
> sda3 is an extended partition that contains sda 5 & 6

your ram is 4 giga... so your swap partition should be twice the ram ... in other words.. 8 giga.. that causes problem with the hibernate thing

ahh brilliant response, thank you very much, can you guide me to how to accomplish that?

---

### Post by Thelasko on 2008-09-15
> **Harisz750 said:**
> sda3 is an extended partition that contains sda 5 & 6

your ram is 4 giga... so your swap partition should be twice the ram ... in other words.. 8 giga.. that causes problem with the hibernate thing

That only applies if the OP uses all 4 Gigs + swap.  If you never use all 4 gigs, you can get by with a swap as large as your RAM, or a 4 gig swap.

The twice your RAM rule comes from the days when computers didn't have as much RAM as they do today.  When you put your computer into hibernate it simply puts all of the information that's stored in RAM into the swap.  Therefore, you need at least as much swap space as RAM.  Twice as much swap as RAM is better.

---

### Post by Harisz750 on 2008-09-15
use ubuntu live cd and use gparted to shrink a bit ext3 partition.. this will make unlocated space.. just merge unlocated with the swap partition.. anyway.. there are many threads to guide you   :)

---

### Post by levinmiester on 2008-09-15
Hey guys I've been trying to use gparted, it comes up with errors in every mode that I run it in when it tries to resize and move the partitions. Is there any program I could use as a replacement, maybe some program in vista even?

---

### Post by Harisz750 on 2008-09-16
are you using it from the live cd? try to unmount the partitions first and then do the resize... if you still can't do it.. personally i use hiren's boot cd ... it has many partition tools, i use partition paragon.Just remember, you have to boot from the hiren's cd...

---

### Post by Thelasko on 2008-09-16
> **Harisz750 said:**
> are you using it from the live cd? try to unmount the partitions first and then do the resize... if you still can't do it.. personally i use hiren's boot cd ... it has many partition tools, i use partition paragon.Just remember, you have to boot from the hiren's cd...

Yes, I can't emphasize this enough.  You must use a Live CD.  The drive can't be mounted while you resize it.  If you can't get Ubuntu's live CD to work, you can try downloading [GParted's.]("http://gparted.sourceforge.net/livecd.php")

> Is there any program I could use as a replacement, maybe some program in vista even? 

Vista has a partition manager but I don't believe it supports ext3 (the Linux file system).  Therefore, I advise against using it for anything other than resizing NTFS (Windows NT, XP, Vista) and FAT (Windows 3.1, 9X) partitions.

---

### Post by scorchgeek on 2008-09-16
Stupid question here. I assume you're running the partitioner with sudo?

---

