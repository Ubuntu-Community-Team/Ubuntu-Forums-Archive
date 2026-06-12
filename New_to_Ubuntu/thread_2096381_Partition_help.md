---
title: "Partition help"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Evocore on 2012-12-19
I don't know if this is the right forum, but I will ask anyway. I made a seperate partition from my C: drive that was 15 gb for ubuntu and kept my C drive for windows, thinking I could just use that while in linux to play my games. I am asking if I can make my ubuntu partition bigger (as I have made 100 gb of free space to do so), or if that is not possible, to just copy the ubuntu folder in that partition, delete that partition, then make a bigger partition, and then paste the folder in the new partition. Would this work at all? Please help me. This is really hard... :p

---

### Post by offgridguy on 2012-12-19
> **Evocore said:**
> I don't know if this is the right forum, but I will ask anyway. I made a seperate partition from my C: drive that was 15 gb for ubuntu and kept my C drive for windows, thinking I could just use that while in linux to play my games. I am asking if I can make my ubuntu partition bigger (as I have made 100 gb of free space to do so), or if that is not possible, to just copy the ubuntu folder in that partition, delete that partition, then make a bigger partition, and then paste the folder in the new partition. Would this work at all? Please help me. This is really hard... :p
Welcome to the forum.
The copy and paste idea is something i have no knowledge of.
   You can make your partition bigger, however 15 gb is not small for ubuntu, so
depending on your requirements you may not need more space at least for now.

For editing linux partitions i use a live CD of parted magic, which contains gparted. Boot from the live CD and use it to expand partitions, as you can't
edit partitions with ubuntu while the partition is in use,

Parted magic can be found in the software center,  you can use gparted to
perform the same function, however i could never get gparted to shutdown
without forcing a hard shutdown.{holding the power button} that's why i use
parted magic.

Again if you don't actually need the space now, there are a lot of threads in this forum re; partitioning,  you may want to spend some time reading and
learning about the process.

Also a screen shot of your partition setup is always helpful when asking for help in this forum,re;partitions, use the paper clip icon and it will upload as a thumbnail.:)

---

### Post by VideoRoy on 2012-12-19
> **Evocore said:**
> I don't know if this is the right forum, but I will ask anyway. I made a seperate partition from my C: drive that was 15 gb for ubuntu and kept my C drive for windows, thinking I could just use that while in linux to play my games. I am asking if I can make my ubuntu partition bigger (as I have made 100 gb of free space to do so), or if that is not possible, to just copy the ubuntu folder in that partition, delete that partition, then make a bigger partition, and then paste the folder in the new partition. Would this work at all? Please help me. This is really hard... :p

Copying and pasting will probably not work.  I have done a lot work with partitions and dual booting and I have expanded my linux partition before but you should use native tools to do so.  I have expanded and shrank partitions for test work without issues.

Here are some steps.

1. First backup data before playing with partitions.  Tools are good these days but you mess up in a hurry.

2. Go to Windows Administrator tools / Disk Management.  When there you can click on the Windows partition and you can find the shrink option from the menu or right clicking if I remember correctly.  Most of the time this works if you just want to get some space but once in a while the Windows Swap file is located at the end of the partition and will keep you from going to far.  It is possible to turn it off, delete, shrink and recreate without damage but that is an advanced topic.

3. Assuming you were able to get some free space, create a GpartED CD or boot to the Ubuntu Live CD and load GpartED from there.  You can install GpartED on the live system but you cannot make changes to an active booted system.

4. In GpartED you can highlight the partition you want to expand and choose expand from the menu or right click here as well.

Those are the basic steps if you want to do this and there are plenty of guides available as well.

---

### Post by Bashing-om on 2012-12-20
All good advise. Another thought you may consider is leaving the ubuntu install partition as is and formatting the 100 GB of free space as a storage partition (depending on your needs, might even format it to ntfs and share it with windows)[or some part of it].

Partitioning can be a very personal thing !

[INDENT][INDENT]my 2 pounds worth <== BDQ

[/INDENT][/INDENT]

---

