---
title: "ntfsresize &quot;Failed to empty $FILE_LogFile/$DATA&quot;"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by sudo_chop on 2008-10-31
I am trying to resize my Windoze partition on my laptop to make room for Intrepid. It has a couple bad sectors so I have to use CLI instead of gparted, and it is giving me the following output:

```

ubuntu@ubuntu:~$ sudo ntfsresize -n -b -v -s 80549M /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 320070480384 bytes (320071 MB)
Current device size: 320070483968 bytes (320071 MB)
New volume size    : 80548995584 bytes (80549 MB)
Checking for bad sectors ...
Bad cluster:  0xbc80d - 0xbc80e    (2)
WARNING: This software has detected that the disk has at least 2 bad sectors.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 70549 MB (22.0%)
Collecting resizing constraints ...
Needed relocations : 15382441 (63007 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Failed to empty $FILE_LogFile/$DATA: Input/output error.
ERROR(5): Failed to reset $LogFile: Input/output error
ubuntu@ubuntu:~$ 

```

I have never used ntfsresize outside of gparted before, and I am pretty new to linux, so if anybody can help me figure this out, that would be great.

Thanks.

-sudo chop

---

### Post by bumanie on 2008-10-31
Have you got xp or vista?

---

### Post by sudo_chop on 2008-10-31
> **bumanie said:**
> Have you got xp or vista?

Vista

---

### Post by bumanie on 2008-10-31
You would be best using vista's in-built partitioner. It can shrink as well as expand partitions. But before you try any shrinking, it is best to defrag at least twice. Right click on my computer - choose manage and then choose manage storage devices. Right click on the partition you want to shrink. Choose shrink and shrink and shrink to whatever size you want. As for the bad sectors - see what vista's partitioner does with them. If successful, use gparted to format the unallocated space to ext3, ready for ubuntu.

---

### Post by sudo_chop on 2008-10-31
> **bumanie said:**
> You would be best using vista's in-built partitioner. It can shrink as well as expand partitions. But before you try any shrinking, it is best to defrag at least twice. Right click on my computer - choose manage and then choose manage storage devices. Right click on the partition you want to shrink. Choose shrink and shrink and shrink to whatever size you want. As for the bad sectors - see what vista's partitioner does with them. If successful, use gparted to format the unallocated space to ext3, ready for ubuntu.

Whoa. I had NO idea Vista had the ability to resize partitions. I am defragmenting now, hopefully the resize works.

Thanks!

-sudo chop

---

