---
title: "Uninstall and partition merge"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by hmich176 on 2008-10-30
Hi.  I wasn't sure where to post this, so here I am.  

I'm currently on my desktop, which has XP and Ubuntu 7.10 on it.  I also have a laptop with Ubuntu 8.04.  

I need to keep XP for school reasons, so what I want to do is uninstall the 7.10 on my desktop and fold the 10gb Ubuntu partition into the 28gb XP partition.  I need it for space, and since I run Ubuntu 8.04 on my laptop, I don't see the need to have both at this point and time.  

I hate to uninstall Ubuntu under any circumstances, but my computer is 6 years old, only has a 40gb hard drive, and I have lots of music on my XP side.  So I want the ten gigs back.  

What is the best way of doing this?  Is it possible to be done, number one, and number two, if I can't merge them together, can I turn the Ubuntu partition into a B or F drive?  

Thanks for the help!

---

### Post by schauerlich on 2008-10-30
Boot into gparted and delete the ext3 partition, then grow the ntfs partition.

---

### Post by aeiah on 2008-10-30
yea its not too complicated. the only risk would be enlarging the windows partition, which could end in some kind of error in rare cases. either way you'd just use a windows partition program, or gparted livecd, or an ubuntu livecd to:

- remove the ubuntu partition and the swap partition
- create a new partition if you want an extra windows partition and format it to ntfs or:
- resize the windows partition to fill the rest of the disk. this may cause problems in rare cases and you should back up to your laptop if you're gonna do this.

once you've removed ubuntu you may find that your computer panics because it cant find grub. if you like grub, you could use supergrub or something and install it to a small partition, or more realistically, use your windows install cd to repair windows, reinstalling the windows master boot record.

if you are concerned that you may be left for a few days without windows if something goes wrong, since its for school and all, you might want to consider restoring the windows mbr before removing ubuntu and grub.

---

### Post by hmich176 on 2008-10-30
I think, because my laptop is currently being loaned out, I'll just keep the partition as a separate drive.  

I need a livecd to do this?  Any good windows partition programs that I could use?

---

### Post by schauerlich on 2008-10-30
In that case, just delete the ext3 and the swap partition and make a new ntfs partition with the free space.

---

