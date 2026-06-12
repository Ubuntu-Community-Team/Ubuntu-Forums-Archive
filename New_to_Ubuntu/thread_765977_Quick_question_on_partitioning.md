---
title: "Quick question on partitioning"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by SigmaHog on 2008-04-24
I wanna create a partition to store all my files in. I tried two different partitions with xp and ubuntu but can't find a way to access each partitions easily. How should I set up my partitions? And which formats?

---

### Post by Joeb454 on 2008-04-24
Unless you want files > 4GB in size, go with FAT32, it can be read natively by each OS :)

---

### Post by Paqman on 2008-04-24
> **Joeb454 said:**
> Unless you want files > 4GB in size, go with FAT32, it can be read natively by each OS :)

So can NTFS, which can have big files, and won't get as fragmented. Before we had NTFS support, FAT32 was the way to go. It's pretty obsolete now, though.

---

### Post by sam_delta on 2008-04-24
you can resize modify and create new partitions with gparted under ubuntu.
if you havnt it installed, install it using synaptic 

id recomend to make the 3rd partition for storing files for both, XP and ubuntu with FAT32 filesystem as mentioned above so ull end up having

partition 1 = windowsXp (NTFS)
partition 2 = ubuntu (ext3)
partition 3 = file storage (FAT32)

sam

---

### Post by SigmaHog on 2008-04-24
Could I load something like WoW on that hard drive could I play it on the xp partition? or do I need to put it on the partition with xp?

---

### Post by Joeb454 on 2008-04-24
> **Paqman said:**
> So can NTFS, which can have big files, and won't get as fragmented. Before we had NTFS support, FAT32 was the way to go. It's pretty obsolete now, though.

The reason I suggested FAT32 is that NTFS can be picky sometimes if it isn't unmounted cleanly. If it isn't, ntfs-3g will refuse to mount it.

---

### Post by sam_delta on 2008-04-24
> **SigmaHog said:**
> Could I load something like WoW on that hard drive could I play it on the xp partition? or do I need to put it on the partition with xp?

dont think so, when you install windows programs, they install on their own partition

---

### Post by Joeb454 on 2008-04-24
Some applications allow you to specify the install path. Though whether Windows will allow you to run it from a different drive is a different matter ;)

---

### Post by Paqman on 2008-04-24
> **Joeb454 said:**
> The reason I suggested FAT32 is that NTFS can be picky sometimes if it isn't unmounted cleanly. If it isn't, ntfs-3g will refuse to mount it.

Only very, very occasionally in my experience. A quick boot and shutdown of Windows solves the problem. FAT32 is pretty horrible, and should be pushed off a cliff if you ask me.

---

