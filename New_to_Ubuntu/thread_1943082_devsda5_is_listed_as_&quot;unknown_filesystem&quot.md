---
title: "/dev/sda5 is listed as &quot;unknown filesystem&quot; (trying to shrink partition with GParted)"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by UnicornBacon on 2012-03-18
-My objective: I'm trying to shrink my /dev/sda1 partition in order to free up 40 GB of unallocated space, in which to install Windows 7 Ultimate 64-bit in a dual boot configuration.

-The dilemma: While attempting to carry out the procedure detailed in this article ---> ["How to resize Linux partition using GParted"]("http://www.simplehelp.net/2008/11/04/how-to-resize-linux-partitions-using-gparted/") I ran in to situation which is preventing me from following the directions in the article with 100% accuracy.

-The details: I can't proceed with steps #16-18 of the tutorial because my /dev/sda5 partition is listed as having an "Unknown File system", and as a result the "Resize/Move" option in the contextual menu for that partition is unavailable (grayed-out.)

A few threads that I have read seem to suggest that my home folder being encrypted might have something to do with the unknown file system status. I considered changing the format of sda5 to "linux-swap" in GParted after reading post #2 in this thread ---> ["GParted shows swap as unknown file system..."]("http://ubuntuforums.org/showthread.php?t=1937779") However I don't know what kind of repercussions would result from taking that action, and I didn't want to act too hastily.

---

### Post by oldfred on 2012-03-19
Gparted does show encrypted partitions as unallocated as it cannot see the encryption nor handle it.

Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by UnicornBacon on 2012-03-19
Thank you very much for responding oldfred, and also for linking those 2 tutorial threads. After skimming the threads I'm fairly certain everything I need to fix the problem is in those guides, so I guess we can consider this thread closed.

---

