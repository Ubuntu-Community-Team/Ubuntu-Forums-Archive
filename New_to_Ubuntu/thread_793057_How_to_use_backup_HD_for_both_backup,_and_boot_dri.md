---
title: "How to use backup HD for both backup, and boot drive for Fluxbuntu"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by swarup on 2008-05-13
I've got a dual boot laptop with Ubuntu Hardy/XP. And I have a backup HD which in the past I have formatted with two partitions--an ext3 & an NTFS--for backing up the internal drive. But actually mine is an older laptop--celeron 433 mhz processor and 256 Ram--and I want to put a nice, fast, small distro (fluxbuntu/Antix/Tinyflux/Tinyme) on the external drive to experiment with. At the same time, I'd like to have that drive be available for backing up my main drive's dual boot (Ubuntu/XP). I've just written zero's to the external drive, and am about to partition it. Question: what will be the best setup of that drive for it to fulfill its new dual role as bootup disk for a tiny linux os and also backup drive for my dual boot. 

Possible options:

1. Make it a single ext3 partition and have fluxbuntu (or similar small OS) take up the whole partition. Can I put backup folders in that partition for my Ubuntu home folder and my XP data? And if I do it like this, can I set up my internal drive's NTFS partition to be able to read and pull data from that ext3 partition if needed?

2. Set it up with two partitions: one ext3 partition with fluxbuntu (or similar small OS) on that, and to which my Ubuntu internal drive would back up its home folder. And a second partition of type NTFS, to which my internal XP partition would back up its data.

Or would some other design be better?

---

### Post by bodhi.zazen on 2008-05-13
Personally , now that I know how to partition, I like to keep the data separate from the OS. so I say a "small" ext3 partition for the OS, a swap partition, and a data partition.

The data partition could be Ext3 or NTFS, not sure it makes much difference. Of the two I would go with NTFS.

---

### Post by swarup on 2008-05-13
> **bodhi.zazen said:**
> Personally , now that I know how to partition, I like to keep the data separate from the OS. so I say a "small" ext3 partition for the OS, a swap partition, and a data partition.

I see. So the data partition would house data from the small boot OS on that drive, as well as the backup data from my Ubuntu and XP OS's on the current internal drive?

> **bodhi.zazen said:**
> The data partition could be Ext3 or NTFS, not sure it makes much difference. Of the two I would go with NTFS.

Very interesting. So if I make the data partition NTFS, then obviously that works for the XP partition. And for the Ubuntu and Fluxbuntu (or Tinyflux/AntiX), they will also be able to write to the NTFS partition just fine? In the past I have sometimes had issues with writing to an NTFS partition from Linux. Is that now trouble-free?

---

### Post by bodhi.zazen on 2008-05-13
Personally , now that I know how to partition, I like to keep the data separate from the OS. so I say a "small" ext3 partition for the OS, a swap partition, and a data partition.

The data partition could be Ext3 or NTFS, not sure it makes much difference. Of the two I would go with NTFS.

---

### Post by bodhi.zazen on 2008-05-13
Personally , now that I know how to partition, I like to keep the data separate from the OS. so I say a "small" ext3 partition for the OS, a swap partition, and a data partition.

The data partition could be Ext3 or NTFS, not sure it makes much difference. Of the two I would go with NTFS.

---

