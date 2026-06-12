---
title: "Volume Partition Help Requested"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Ernie Linux on 2008-04-27
Hello All!  

I'm using Ubuntu 7.10 and I have two drives - my primary partition which I let Ubuntu take over completely on install, and my secondary partition called "File Storage" which I left in NTFS format with all of my documents/music/files from Windows.  

I just bit the bullet and moved everything from File Storage over to the primary partition and then used GNOME Partition Editor to repartition File Storage.  I setup one big extended partition (230 gig) and then under that I created one big logical partition in ext3 format.

Here is the problem:  once the partitions are created I can't access or rename them.  I want to rename the extended partition as "File Storage" instead of "232.9 GB Volume" and rename the logical partition "Ernie's Files" instead of "disk".  I'd like the partitions to auto mount when I login as well so I can use them just like I did with Windows.

Any ideas?

](*,)

---

### Post by bluefrog on 2008-05-13
you want to label a partition.

for ntfs
ntfslabel /dev/sdxx new-name

for ext3
e2label /dev/sdxx new-name

---

