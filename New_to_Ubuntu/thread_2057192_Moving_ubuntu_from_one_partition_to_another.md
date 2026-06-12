---
title: "Moving ubuntu from one partition to another?"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by matematicomarpla on 2012-09-13
May I move an installed ubuntu system, from one HDD (or logical disk) to another?
If answer is yes, how to do it?

---

### Post by audiomick on 2012-09-13
I have never done this, but I think I can help.

You can clone a Linux installation. I have read a number of threads from people who have succesfully done so. I believe clonezilla might be one application that could do the cloning. You would then have to update your boot manager (grub) to make it look for the new partition.


Wait on, I just went looking in the Ubuntu documentation and found this

[https://help.ubuntu.com/community/MovingLinuxPartition]("https://help.ubuntu.com/community/MovingLinuxPartition")

Note also the link down at the bottom of that page regarding using gparted to move a partition.

---

### Post by mips on 2012-09-13
> **audiomick said:**
> 
Wait on, I just went looking in the Ubuntu documentation and found this

[https://help.ubuntu.com/community/MovingLinuxPartition]("https://help.ubuntu.com/community/MovingLinuxPartition")

Note also the link down at the bottom of that page regarding using gparted to move a partition.

That's a pretty good guide and should work.

---

### Post by matematicomarpla on 2012-09-17
> **audiomick said:**
> I have never done this, but I think I can help.

You can clone a Linux installation. I have read a number of threads from people who have succesfully done so. I believe clonezilla might be one application that could do the cloning. You would then have to update your boot manager (grub) to make it look for the new partition.


Wait on, I just went looking in the Ubuntu documentation and found this

[https://help.ubuntu.com/community/MovingLinuxPartition]("https://help.ubuntu.com/community/MovingLinuxPartition")

Note also the link down at the bottom of that page regarding using gparted to move a partition.

Thanks, Michael!  Very, very useful!

---

