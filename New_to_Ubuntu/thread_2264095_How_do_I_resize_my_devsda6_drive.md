---
title: "How do I resize my /dev/sda6 drive?"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by CraftyHCU on 2015-02-05
i have like 140 gb but i whant to put it in the main drive plz help me the main drive has 7 gb but it is full and i tryed to resize with gparted but it wont allow me to it i need help
 		 			 				:confused: plzzzzzzzzzzzzz help me

---

### Post by yancek on 2015-02-05
You need to first unmount any partition you want to modify.
If you want to resize/enlarge a partition, you need unallocated space contiguous to it.
Post an image from GParted showing your partitions.

---

### Post by Mark Phelps on 2015-02-05
> i tryed to resize with gparted but it wont allow me toIf it's a partition that is in use, you can't modify it.  In that case, you need to boot from disk or USB media (Ubuntu installation media will do this) and run GParted from there.

---

