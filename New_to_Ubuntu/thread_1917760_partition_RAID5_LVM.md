---
title: "partition RAID5 LVM"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by dvks on 2012-01-30
I post this set of questions on creating LVM over RAID 5 after searching multiple posts, I understand that there are multiple ways to get things done but I couldn't find a clear complete solution for the process of setting LVM over RAID5 with all the details for a beginner like myself:
 
I just installed UBUNTU on a 40GB SATA - sdd, I have additional 3 SATA drives 1.5 TB each = sda, sdb,sdc  and I want to set LVM over RAID 5, I intend to assign the whole drive for the RAID.
 
1. Do I need to partition the drives for setting the RAID or I can go ahead and set the  RAID5 over the whole drive devices, from my search I understand that both is possible but not clear on which is better and why? 
 
2. Assuming the above is that I need to partition. Which command is the best for using script to do the partitioning:  paerted or sfdisk  (or other command...)
 
3. What should be the partition type FD  or   DA  or other type?
 
4. If I am using "parted" command to do the partitioning how do I set the type to FD or DA etc using parted or I must use sfdisk for doing RAID and LVM?
 
5. I understand that sfdisk  can't handle large drives, can I still use it and set on each of my drives multiple / smaller partitions each can be created by sfdisk and create multiple RAID5 arrays based on the partitions and than assign all the RAIDs to the LVM so the LVM still see the whole storage? Does this extra partitioning and RAIDs affect performance?

---

