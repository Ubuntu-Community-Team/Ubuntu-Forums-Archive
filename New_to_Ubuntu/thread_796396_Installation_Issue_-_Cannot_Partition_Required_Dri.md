---
title: "Installation Issue - Cannot Partition Required Driver, Deterioration Problem."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Henrywantstobeapenguin on 2008-05-16
Hello there

I have made a live CD of v8.04, done MD5Checksum and checked CD Integrity - all of which are fine.

Trying to install Ubuntu on a friends laptop, however when it comes to the partition section of the process, we cannot adjust the drive  size. Using the live disk desktop to examine the drive gives this error message 

"This disk has bad sector, this means physical damage on the disks surface, caused by deteroitation manufacturing faults or other reason. Reliability may stay stable, or degrade fast." 

Then it suggests we make a backup. 

Then it says to run "CHKDSK on windows and reboot twice, then we can resize the NTFS drive by additionally using the bad sectors option"

The problem is, his windows installation is broken. Thus we cannot access CHKDSK via safe mode, or any of the different boot options.

Any help would be muchly appreciated, 

Thanks 

Henry

---

### Post by linuxonbute on 2008-05-16
> **Henrywantstobeapenguin said:**
> Hello there

I have made a live CD of v8.04, done MD5Checksum and checked CD Integrity - all of which are fine.

Trying to install Ubuntu on a friends laptop, however when it comes to the partition section of the process, we cannot adjust the drive  size. Using the live disk desktop to examine the drive gives this error message 

"This disk has bad sector, this means physical damage on the disks surface, caused by deteroitation manufacturing faults or other reason. Reliability may stay stable, or degrade fast." 

Then it suggests we make a backup. 

Then it says to run "CHKDSK on windows and reboot twice, then we can resize the NTFS drive by additionally using the bad sectors option"

The problem is, his windows installation is broken. Thus we cannot access CHKDSK via safe mode, or any of the different boot options.

Any help would be muchly appreciated, 

Thanks 

Henry
Don't know a lot about MS Windows but if you have the Windows install disc
you might be able to boot from it and run chkdsk from there.

---

### Post by Henrywantstobeapenguin on 2008-05-16
Thanks Linuxonbute, 

Unfortunately we currently have no disk, otherwise we would have attempted this already. If we were to install Ubuntu on the entire drive, would we be able to wipe it with a windows installation when  we procured such a disk? 

I would imagine we would eventually end up partitioning it and dual boot, but it would be nice to know if we could revert it if required. 

Many thanks

Henry

---

