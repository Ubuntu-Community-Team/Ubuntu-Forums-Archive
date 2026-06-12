---
title: "grub rescue"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by dhruv8 on 2016-05-26
unfortunately i have deleted my linux partition and now it is showing that error:no sduch partition.
help me

---

### Post by ajgreeny on 2016-05-26
We can't help you with that lack of information, I'm afraid.

Was this a dual boot system with Ubuntu and Windows?  If so, which version of each OS?  Do you have the repair or installation DVD for Windows?
It will be helpful if you can run a live Ubuntu system, and from that open a terminal and run command ```
sudo parted -l
``` then post back here the output from that command in code tags please.  See my signature below for a **How-To**.

---

### Post by Mark Phelps on 2016-05-26
It also matters a lot HOW you deleted it.

If you just accidentally deleted it using something like GParted and have done nothing else to the disk since that, you might be able to restore the partition using something like TestDisk.

But, if you installed something (like another OS), and that overwrote the partition, you are not likely going to get it back.

As indicated, we need more details from you to provide detailed help from this end.

---

