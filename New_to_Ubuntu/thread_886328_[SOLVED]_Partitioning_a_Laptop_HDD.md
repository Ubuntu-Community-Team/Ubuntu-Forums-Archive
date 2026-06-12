---
title: "[SOLVED] Partitioning a Laptop HDD"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by getitright on 2008-08-11
My laptop HDD has three partitions, Un-named, C and D. I used the Vista facility to create free space on D. I was the able to create a /home primary partition, but the remaining free space is then labeled unusable so preventing me creating more partitions.

---

### Post by ramnarayan on 2008-08-11
> **getitright said:**
> My laptop HDD has three partitions, Un-named, C and D. I used the Vista facility to create free space on D. I was the able to create a /home primary partition, but the remaining free space is then labeled unusable so preventing me creating more partitions.

Are you trying to Install Ubuntu - if so which version 

Assuming thats what you want to do - boot the LIve Ubuntu CD / DVD and check your partitions through System -> Administration -> Partition Editor. this will give you some idea of what has happened.

Also try df -hT at the command line
open Applications ->Accessories-> terminal and type "df-hT" with out the inverted " - post this here and we can let you whats happening. Some times  the Partition Manager does not allow creation of more than 4 partitions in which case you need to first make one Logical partition for Linux and then subdivide them into "/" /boot and /home (minimum on the safe side

"/" is where you Linux OS will reside.

Preferably if you are installing linux do the partition through Linux. It will read your Vista OS and keep those sections intact.

Google for key words - there is a lot of help out there.

Post back what happens

ram

---

### Post by SZ07 on 2008-08-11
I think I know what you are talking about. I had this problem in Vista too. In Vista a certain amount of space is unusable as it keep it for additional OS space (I think).

How big is the unusable space? If it's a couple of gigs (2-5) then I think that is normal. You can always use GParted (in an installed ubuntu OS or from the live CD) to divide up the disk as you see it, although it can be a bit slow if you make major changes.

---

### Post by kansasnoob on 2008-08-11
Even though the first partition is "unlabeled" it must still be counting against the four primary partition limit.

You may need to create one larger "extended partition" and then create all of your Linux partitions (as logical partitions) inside that "extended partition" like I did:

[ATTACH]81087[/ATTACH]

---

### Post by mcduck on 2008-08-11
Yep, sounds like the four primary partition limit. You can only have 4 primary partitions, or 3 primary partitions + 1 extended partition. The extended partition can then contain as many logical partitions as you wish.

---

