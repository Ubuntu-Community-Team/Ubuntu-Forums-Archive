---
title: "need to increase ubuntu size"
date: 2018-07-24
forum: New to Ubuntu
---

### Post by totti10it2 on 2018-07-24
i was working on win 7/64 bit
i decided very  recently to try ubuntu alongside windows

i installed it successfully and working fine
the problem is the small size of the ubuntu partition
i tried to resize it using g-parted  inside ubuntu but i can't
.
any one can help me

[IMG]http://www8.0zz0.com/2018/07/24/22/541647535.png[/IMG]

---

### Post by deadflowr on 2018-07-24
You can't resize a mounted partition.
And you can't unmount the running system.
You need to do it from either another OS or from the Ubuntu installation media's Try Ubuntu Live session.

---

### Post by yancek on 2018-07-24
Use the windows Disk Management tool to shrink a windows partition which is contiguous with your Ubuntu partition.  From GParted, that would be the sda6 partition, not sure what it would be labelled in windows but you should be able to tell by the partition size.  Best run Disk Defragmenter first and after shrinking the windows partiton, reboot windows and run chkdsk until there are no errors.

---

### Post by Geoffrey_Arndt on 2018-07-24
For that PC, either get a second HDD or SSD, . . . . . or offload some of the large media (movie files) and use the newly available space for Ubuntu.

---

### Post by oldfred on 2018-07-24
NTFS works best if you have 30% free. At 20% it slows down and at 10% you just about cannot do a defrag as you have too little room.
You are not showing a lot of space on any partitions to make room. Best to either do a major houseclean or purchase larger drive.

---

