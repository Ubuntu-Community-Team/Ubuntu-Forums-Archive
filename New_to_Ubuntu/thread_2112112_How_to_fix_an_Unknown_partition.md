---
title: "How to fix an Unknown partition"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by armb78 on 2013-02-03
Hi,
yesterday, I executed gparted and resized a partition. (108G to about 170G) But when it did 80% of the job, it just closed! I opened up gparted again, but there was an "Unknown" partition. e2fsck gives me:

```
 > sudo e2fsck /dev/sda1
e2fsck 1.42 (29-Nov-2011)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```How can I fix it?

---

### Post by armb78 on 2013-02-04
Anyone?

---

### Post by Cheesemill on 2013-02-04
I don't see what grub has to do with this, do you mean gparted?

---

### Post by armb78 on 2013-02-04
Oh! Yes, I mean gparted!

---

### Post by Cheesemill on 2013-02-04
The easiest method of fixing this is to start from scratch.

Wipe the drive, create and format whatever partitions you want and then restore all of your data from a backup.

---

### Post by armb78 on 2013-02-04
Unfortunately, I can't. There are about 80G files in it and I really need them. They're not for me.
I know that the superblock has been lost, and I know that if I find it, I can probably fix the partition. But I can't.

---

### Post by Cheesemill on 2013-02-04
Did you try the command that fsck mentioned?
```
e2fsck -b 8193 <device>
```

If this doesn't work you could try using testdisk to recover your data.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It can be installed with...
```
 sudo apt-get install testdisk
```and then running
```
 testdisk
```from a terminal.

Next time you use gparted you should read the warning (attached screenshot below).

---

### Post by armb78 on 2013-02-04
The partition is NTFS and TestDisk doesn't support it.

---

### Post by Cheesemill on 2013-02-04
Testdisk does support recovery of NTFS partitions, I've used it myself in the past.

You may, however have more luck with Mark Phelps' suggestions [here]("http://ubuntuforums.org/showpost.php?p=12490412&postcount=4").

---

### Post by armb78 on 2013-02-07
It worked. Thanks

---

### Post by Mark Phelps on 2013-02-07
Glad to see my suggestion could be of help.

Please use the Thread Tools to mark this thread as SOLVED.

Thanks

---

