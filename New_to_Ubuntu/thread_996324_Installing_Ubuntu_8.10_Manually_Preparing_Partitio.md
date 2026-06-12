---
title: "Installing Ubuntu 8.10 Manually Preparing Partitions Help!"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by CeBiff on 2008-11-28
Hi,

For a lot of reasons, I have to mannually prepare the partitions for my ubuntu 8.10 install

i have 32606 mb of free room
i have 2mb of ram so i'm thinnking
28000 mb for ubuntu storage
4000mb for swap

now, how do I create these partitions?

For the ubuntu one (not swap) should it be primary or logical?  Should it be beginning or end?  Where's the mount point?

Same questions for the swap

Thanks so much to whoever can help me

---

### Post by oldos2er on 2008-11-28
Do you have 2GB RAM? Assuming 2mb is a typo? Unless you plan to run a lot of memory intensive programs, you should not need more than 512MB for swap. 

 You can run Linux (and Linux swap) from logical partitions.

---

### Post by Rolcol on 2008-11-28
The ubuntu one should be at the mount point of /  ("root").  I think linux is fine with being a logical partition (as compared to windows) but it's best to have it in a primary partition.  The position of the partition doesn't matter since you can dualboot without it being at the very beginning.  The ubuntu partition must have a boot flag on it, however.  Swap is usually a logical partition.

---

### Post by a0u on 2008-11-28
> **oldos2er said:**
> Unless you plan to run a lot of memory intensive programs, you should need more than 512MB for swap.
You probably mean **not** more than 512MB swap...

---

### Post by Helios1276 on 2008-11-28
A separate home partition is always a nice safety net.

---

### Post by oldos2er on 2008-11-28
> **a0u said:**
> You probably mean **not** more than 512MB swap...

 Yes, thanks.

---

