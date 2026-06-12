---
title: "What to do and how to manage a dual-boot Ubuntu?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by rexdino5 on 2013-04-08
Hello, my friend had recently got interested with Ubuntu because I was supposively told Linux games where cheaper on steam. Whether or not thats true I've installed and created a partition on a NTFS hard drive. I can't seem to determine my partition for my Ubuntu system that I made. I'm using the "Disk Management" to see my partitions. I wanted to reduce my partition size. I installed Ubuntu from a disk in which I burned the Ubuntu Iso to. My partitions are:
-System Reserved (E:)
-WIN7 (C:) 839.28 GB NTFS
-14.18 GB Healthy (Primary Partition)
-69.98 GB Healthy (Primary Partition)
-7.97 GB Healthy (Primary Partition)

I don't remember how much memory I dedicated to my Ubuntu and non of the partitions are labeled.

If someone could help me with this. I would appreciate the help very much. (My harddrive I partitioned is a TB)

P.S. On the GRUB launcher how do I know which sda to run Since it shows 3 sda's for windows 7?

---

### Post by mikewhatever on 2013-04-08
You can use the Disk Utility in Ubuntu to see the partition layout. What you posted above doesn't tell much. The last three partitions could be Ubuntu related - possible root, home and swap - but that's only a guess.
sda, or /dev/sda is the way Ubuntu designates HDD devices. Are you saying there are three of them, all designated as sda?

---

