---
title: "[SOLVED] Partition/Swap Problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by cheesypoof on 2008-06-01
I shrunk my swap partition from 1.4gib to 1gib after booting to the live cd. I then proceeded to expand my ubuntu partition to use this new unallocated space. When it was verifying for errors, it did not pass. The best I can recall what it said was to do something before something else. I was surprised because it seemed to have added the unallocated space to it's partition successfully. Before I did all of this, my system monitor was showing 22.1gib free out of 31.7gib. After I was done, I restarted and noticed that the same exact data was being shown. However, gparted was showing different numbers.
[[IMG]http://img233.imageshack.us/img233/3987/screenshotnt6.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=screenshotnt6.jpg)

Additionally, now my swap is not working automatically upon startup. It shows up as 0 bytes until I hit swapon in gparted. Then it correctly changes to 1 gib.

Hopefully someone can help me figure out how to make the swap partition load automatically and figure out how I can make use of that space I added to my ubuntu partition.

---

### Post by sayakb on 2008-06-01
To mount swap:
add this line to /etc/fstab:

**/dev/sda6 none swap sw 0 0**

if you want the UUID, find it with this:
[B]
ls -l /dev/disk/by-uuid[/B]

and add it to beginning like others

EDIT: Btw, did you reboot ;) ??

---

### Post by cheesypoof on 2008-06-01
Thanks so much, I rebooted and the swap mounted the way it should with your suggestion. Do you have any ideas though, why there seems to be a difference between gparted and system monitor about total space? I was looking at the sectors used by both the swap and ubuntu partitions. Is it weird at all that 64 sectors are missing in between them?

ubuntu partition
last sector: 319564979

swap partition
first sector: 319565043

---

