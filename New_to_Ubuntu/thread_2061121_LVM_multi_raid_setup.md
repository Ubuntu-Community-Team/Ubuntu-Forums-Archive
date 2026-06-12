---
title: "LVM multi raid setup?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by I8NY on 2012-09-21
I know Linux has great capabilities over the years of using it but I can't seem to find an exact name or setup for this scenario.  I want to do [Matrix RAID]("http://en.wikipedia.org/wiki/Intel_Matrix_RAID") (that is not the correct general name but it was as close as I got) on two HDD.  I want to put the OS in RAID 1 for redundancy and then have another partition or folder as RAID 0 for TV recordings both on two HDD.  BIOS RAID won't support this and I don't want to get a $150 RAID card so I want Linux to do a software RAID using LVM and/or something I don't know about.

---

### Post by SaturnusDJ on 2012-09-23
With mdadm it's possible to create RAID setups by combining partitions instead of devices/hard disks.

---

### Post by I8NY on 2012-09-27
> **SaturnusDJ said:**
> With mdadm it's possible to create RAID setups by combining partitions instead of devices/hard disks.
Great, I'll just make two partition on each HDD and join 2 partitions in RAID 1 and 2 others in RAID 0.

---

