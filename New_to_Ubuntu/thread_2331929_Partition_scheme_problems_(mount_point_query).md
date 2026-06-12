---
title: "Partition scheme problems (mount point query)"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by pasha8 on 2016-07-26
Hi all,

I have been using ubuntu for a few years now and have only enjoyed it. I recently upgraded to a new machine and followed the partition scheme advise here ([https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)). When I boot to ubuntu only the / partition is available (with very limited storage) while my /home resides under "other locations," essentially treated like an external drive or my windows partition. 
Is there a way to consolidate my partitions so that all of my data is in one location? (I currently have two /home's, one under / and another in a different partition, /media/my_name/long_string_of_numbers/home. 

The output of fdisk -l is:
Device          Start        End    Sectors   Size Type
/dev/sda1        2048     821247     819200   400M Windows recovery environment
/dev/sda2      821248    1353727     532480   260M EFI System
/dev/sda3     1353728    1615871     262144   128M Microsoft reserved
/dev/sda4     1615872  361471999  359856128 171.6G Microsoft basic data
/dev/sda5  1892689920 1953513471   60823552    29G Microsoft basic data
/dev/sda6   361472000 1763737599 1402265600 668.7G Linux filesystem
/dev/sda7  1859274752 1892689919   33415168    16G Linux swap
/dev/sda8  1763737600 1859274751   95537152  45.6G Linux filesystem

Partition table entries are not in disk order.


It is the 45.6GB partition that appears under "files" and I have to elaborately navigate to the 668.7GB one.

Thank you in advance for any advice!

---

### Post by yancek on 2016-07-26
> (I currently have two /home's, one under / and another in a different partition, /media/my_name/long_string_of_numbers/home. 


If you have a separate data partition and you named it home, you should change it to something more logical, like data.  Having two separate /home entries is going to be confusing.  You simply create a mount point for the second "home" which contains your data and then put an entry in the /etc/fstab file so that it mounts and is accessible on boot.

Create the mount point with:   ```
sudo mkdir /mnt/data
```  Change data to some other name if you want.  An example fstab entry for a data partition below.  Change the "/dev/sda9" part to the correct partition in your case or use a UUID.  Lots of sample entries for fstab if you do an online search.

```
/dev/sda9 /mnt/data ext4 auto,user,rw 1 2
```

---

