---
title: "XBMCbuntu - Hard Drive Partition Recovery"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by mwpeck on 2012-12-09
So I just finished my XBMCbuntu install, transferred all my media over to a 3TB drive, formatted in ext4.  I shutdown for the night, get back on in the morning and it tells me it cannot mount my external drive.

I try manually mounting it and it tells me something about a corrupt superblock and a bad magic number (can't remember the exact error now, it was hours ago originally).

After some searching, I've tried running through a few processes that other people have, as a result:  

Running: sudo fsck.ext4 -v /dev/sdb
Results in the above error I mentioned.

Running: sudo mke2fs -n /dev/sdb1
Results in a list of backup superblocks.

Running: sudo e2fsck -y -b block_number /dev/sdb
Results in a very long lasting process to attempt to fix it.

Currently it is attempt to recreate the journal (32768 blocks) and is take a pretty long time (20 minutes so far). The thing that worries me, is there is no indication that it is actually doing anything now. The e2fsck process is no longer appearing towards the top of the process list (&amp;quot;top&amp;quot; command), iostat -x seems to show values that are constantly going down (that is, read requests per second, read KB per second, etc) like it is showing an average and is no longer reading (or writing), causing the numbers to drop.

What commands do I need to run (to supply info to you much more experienced users) to get some more help on this issue? I would preferably not use a method that will wipe the drive (if I haven't already), because I do not have a backup.

The weird part is it was working fine last night, I shut the system down, started it up this morning and it suddenly was no longer working.

How long can I expect &amp;quot;Creating journal&amp;quot; to take on a 3TB drive?

Thanks.

---

### Post by mwpeck on 2012-12-09
> **mwpeck said:**
> Running: sudo fsck.ext4 -v /dev/sdb
For archiving purposes (in case someone runs into a problem and somehow lands here from google), I fixed the problem.

Changing the quoted command to:

sudo fsck.ext4 -**y**v /dev/sdb**1**

Fixed it (bold is what changed). It ran a similar process as the last command I mentioned earlier (sudo e2fsck -y -b block_number /dev/sdb), except it went much quicker (took only about 30 minutes to finish, earlier I never let it finish completely) and at the end of it I was able to mount the drive again.

I am now pulling a backup of all my data on it so I can mess with the drive and see if it is messed up (it fails to perform a SMART test right now), if so I'm off to return it (only bought it a few days ago).

Another interesting note, is after the fsck.ext4 command finished and I mounted the drive, it was ultra slow....taking 5-10 minutes just to browse into the drive (through a file manager GUI). Rebooting seemed to fix the problem though.

---

