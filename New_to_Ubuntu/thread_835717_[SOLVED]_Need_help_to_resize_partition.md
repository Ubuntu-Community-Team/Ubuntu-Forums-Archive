---
title: "[SOLVED] Need help to resize partition"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-20
I choose to Install Ubuntu on all hard disk (Second Partition Option) during format. Now, my SWAP partition is too big (about 2.8GB) and it is of Extended type. I would like to reduce this size about 1.5GB and would like the adjacent partition to take up the balance space. Shrinking SWAP partition is no problem but to expand /dev/sda4 is not possible because it is Logical partition. I believe there must be ways to overcome it but I just dont know how. Please give some advice

---

### Post by Duck2006 on 2008-06-20
Shrink your swap partition, then shrink your extended partition, then add the space to the primary partition.

---

### Post by wariskampar on 2008-06-20
How do I shrink my extended partition?


edit: ok! it was easier than i thought. Thank you so much

---

### Post by Duck2006 on 2008-06-20
This may help, have you been able to shrink your swap partition?

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

---

