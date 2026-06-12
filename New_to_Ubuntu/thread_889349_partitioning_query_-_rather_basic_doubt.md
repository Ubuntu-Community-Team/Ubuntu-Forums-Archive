---
title: "partitioning query - rather basic doubt"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by rainInSpain on 2008-08-14
as i see it the only two partitions that are really required to be made are the root and the swap partitions...right?
if i choose to also create one for /usr and another for /home, why does the partition mounted at / show up seperately? shouldnt it encompass /home and/usr and then some???

---

### Post by bobnutfield on 2008-08-14
Actually, you can even do without a swap partition if you have loads of memory.  You can install your entire system on one partion for /.  However, should you need to re-install your system files for any reason, you will have to back up your home directory if your want to save your data.  Having a separate home partition saves me a lot of time for such things.  I have never found the need for a separate /boot or /usr partition, but others find doing that useful.

---

### Post by mandrill on 2008-08-14
> **rainInSpain said:**
> as i see it the only two partitions that are really required to be made are the root and the swap partitions...right?
if i choose to also create one for /usr and another for /home, why does the partition mounted at / show up seperately? shouldnt it encompass /home and/usr and then some???

I agree - separate /home is good..../boot is for more complicated situations, like needing to keep your windows MBR intact. I do, however, suggest using at least a swap portion equal to your memory - it makes everybody happy, costs nothing, and will, as suggested above, probably be 
unnecessary. Its just the right way to do it.

Happy Hunting.

---

