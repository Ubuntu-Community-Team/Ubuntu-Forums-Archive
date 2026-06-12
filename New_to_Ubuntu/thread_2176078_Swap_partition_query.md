---
title: "Swap partition query"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by huxley2 on 2013-09-22
Hi, everybody

Just a quick Q about swap partitions. In Gparted I  noticed that my swap partition is inside an extended partition which is  the only partition to be marked with a triangle. Is swap inside an  extended partition normal and what does the triangle represent? 
[ATTACH]246441[/ATTACH]

Everythings working fine but since converting to linux I've got the learning bug. Ignorance is no longer an option :wink:

Regards,

Hux

---

### Post by deadflowr on 2013-09-22
You meant the down triangle.
I though you meant it had an error triangle.

The swap partition, when it was made by the Ubuntu installer is a logical partition.
Logical partitions sit inside an Extended partition, which is a container for logical partitions.

This might help more, or not
[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

---

### Post by huxley2 on 2013-09-22
Thanks, Flowr thats cleared up the extended partition function nicely, but I'm still flumoxed about the inverted triangle, I couldn't see it mentioned in the link.

---

### Post by deadflowr on 2013-09-22
Are you meaning the arrow next to "Extended Partition"?

The drop down arrow.

---

### Post by huxley2 on 2013-09-22
Luckily no one can see me blushing from embarrassment. Even in the absolute beginners section I'm feeling quite the fool now lol
On the plus side it's another thread solved so we can say no more about it

Thanks for not laughing at me, Flowr

---

### Post by oldfred on 2013-09-22
If you install with an encrypted /home, gparted will not see the swap correctly as it is encrypted also. Then it does show an error message, but is normal.

---

