---
title: "Determine is filesystem is Etx2 or Ext3 or Ext4?"
date: 2010-06-11
forum: Programming Talk
---

### Post by Tomato-kun on 2010-06-11
Hello.

How can i correctly determine the type of fyle system? What fields i should compare? As i understand,it is imposible to do this by revision_level field from superblock =\ Any ideas?...

Thanks.

---

### Post by DanielWaterworth on 2010-06-11
If it's mounted, you should be able to get the filesystem type from a plain mount command. First line of mine is:

$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

---

### Post by Tomato-kun on 2010-06-11
> **DanielWaterworth said:**
> If it's mounted, you should be able to get the filesystem type from a plain mount command. First line of mine is:

$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

Hm. And how i can do it except this? Just have superblock fields values and other technical information. I mean, i have a some hex editor and i can waching through the file system. How can i resolve the type?)

---

### Post by Tony Flury on 2010-06-11
What is wrong with running mount - or something like that ?

---

### Post by arrange on 2010-06-11
I don't think there is a simple way to do this (like looking at a specific byte in the superblock).
You can use *blkid* or *file -s* without having to mount the partition.

---

### Post by BoneKracker on 2010-06-11
'blkid', 'mount', 'cat /proc/mounts' are all good ways

Another is 'cd /proc/fs' or 'cd /sys/fs' and look around (the devices will be listed under the filesystem type).

'tune2fs -l <device>' is the best way to tell absolutely.  It will tell you the filesystem magic number.  Unfortunately, then you've got to figure out what filesystem that corresponds to.  (This is how the system actually knows what filesystem it is.  However, you can also tell by glancing at the filesystem features.

---

### Post by nvteighen on 2010-06-12
Ugh... looking at /etc/fstab doesn't seem a bad idea if the filesystem is internal.

---

### Post by BoneKracker on 2010-06-12
Ugh... fstab is user-generated and not authoritative.  In other words, it could be wrong.

---

### Post by arrange on 2010-06-12
[COLOR="Silver"]'tune2fs -l <device>' is the best way to tell absolutely. It will tell you the filesystem magic number.[/COLOR]

It does not work for me. I have the same *magic numbers* for different filesystems.
```
arrange@lucid-lean:~$ sudo tune2fs -l /dev/sdb2 | grep magic
Filesystem magic number:  0xEF53
arrange@lucid-lean:~$ sudo tune2fs -l /dev/sdb1 | grep magic
Filesystem magic number:  0xEF53
arrange@lucid-lean:~$ sudo blkid /dev/sdb2
/dev/sdb2: LABEL="hh" UUID="87435c1d-6517-4c85-b68d-2841ae91fa43" SEC_TYPE="ext2" TYPE="ext3" 
arrange@lucid-lean:~$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="Dokumenty" UUID="304a520a-0a97-4f94-abe1-a8fc6858040a" TYPE="ext4" 
```

---

### Post by BoneKracker on 2010-06-12
> **arrange said:**
> [COLOR="Silver"]'tune2fs -l <device>' is the best way to tell absolutely. It will tell you the filesystem magic number.[/COLOR]

It does not work for me. I have the same *magic numbers* for different filesystems.
```
arrange@lucid-lean:~$ sudo tune2fs -l /dev/sdb2 | grep magic
Filesystem magic number:  0xEF53
arrange@lucid-lean:~$ sudo tune2fs -l /dev/sdb1 | grep magic
Filesystem magic number:  0xEF53
arrange@lucid-lean:~$ sudo blkid /dev/sdb2
/dev/sdb2: LABEL="hh" UUID="87435c1d-6517-4c85-b68d-2841ae91fa43" SEC_TYPE="ext2" TYPE="ext3" 
arrange@lucid-lean:~$ sudo blkid /dev/sdb1
/dev/sdb1: LABEL="Dokumenty" UUID="304a520a-0a97-4f94-abe1-a8fc6858040a" TYPE="ext4" 
```

It seems I have an incorrect understanding of the magic number -- it does not distinguish between different ext filesystems.  I have confirmed this on my own systems (both a system using the ext4 driver for all ext systems and another system that does not do this).

Disregard what I said about using the magic number for this purpose.  (I think you can still use to type filesystems, but not to distinguish between ext sub-types.)  Sorry for the confusion.

---

### Post by Tomato-kun on 2010-06-12
Thanks, guys.

But i have to get this information not from linux-powered machine :) I mean, i shoud get it having only hdd and hex representation of information that it stores. So, all variants using some utils aren't suitable for me.

---

### Post by arrange on 2010-06-13
It's quite easy. :) Just follow the code in *ext.c* - package *util-linux-ng* :popcorn:

---

### Post by Tomato-kun on 2010-06-13
> **arrange said:**
> It's quite easy. :) Just follow the code in *ext.c* - package *util-linux-ng* :popcorn:

Thanks. I'll discover this way tomorrow.

---

