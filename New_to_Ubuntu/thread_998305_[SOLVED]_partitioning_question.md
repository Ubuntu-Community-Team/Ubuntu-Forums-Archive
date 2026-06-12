---
title: "[SOLVED] partitioning question"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Redbeard09 on 2008-11-30
I am in the process of defragging a hard-drive in preparation for partitioning before install. My question is that as windows compacts files to the left hand side, usually there is a large block of free space on the right side of the disk usage bar. However there is a large block of immovable files in the middle of this free space.

my question is whether or not this will be a problem in the partitioning process?

---

### Post by bhadotia on 2008-11-30
> **Redbeard09 said:**
> I am in the process of defragging a hard-drive in preparation for partitioning before install. My question is that as windows compacts files to the left hand side, usually there is a large block of free space on the right side of the disk usage bar. However there is a large block of immovable files in the middle of this free space.

my question is whether or not this will be a problem in the partitioning process?

If there is some error an error will be reported by the partitioner. 

Of course you will leave some free space on the partition you are going to resize, correct?

---

### Post by unutbu on 2008-11-30
Yes, that would be a problem. The partition editor can only shrink a partitions in such a way that allows all files to remain together in one contiguous block of hard drive space.

The immovable files may be due to windows paging files. In this case, "disable virtual memory" or "disable the paging file", and then defrag again.
See [http://ubuntuforums.org/showthread.php?p=1689709](http://ubuntuforums.org/showthread.php?p=1689709)

Also, if you are using Vista, use the Vista partition editor to resize the Vista partition. 
I believe Vista puts some partition information
in some unusual place, so only the Vista partition editor edits it properly. See
[http://ubuntuforums.org/showpost.php?p=5749382&postcount=11](http://ubuntuforums.org/showpost.php?p=5749382&postcount=11)

---

### Post by Redbeard09 on 2008-11-30
@unutbu: Its seems that the swap(page) files might be the issue. Being that this is the first time that this has been a problem I didn't even think of that. Using XP btw.

---

