---
title: "ubuntu on logical partition just like its swap are there any performance issues ?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by piadex2 on 2014-09-11
Dear Forummates,

I would like to install ubuntu 14 dualboot on a raid0 array with windows 7. Actually its already there but the problem is. I need an other partition. But that would be the 5th so it is not possible.
I am thinking of reinstall the system in the following way:
extended partion:
1st logical: ubuntu and programs
2nd logical: ubuntu's swap partition
primary partitioin:
1st primary: a partition for certain system files (100MB), automatically generated when installing windows 7
2nd primary: windows 7 and programs
3rd primary: data

Using this setup are there any performance issues? (highlighting the logical partitions)

Thank You.

piadex2

---

### Post by grahammechanical on 2014-09-11
If you are sure that you do not have GPT and that you can only have 4 primary partitions, Then the 4th primary partition should be an extended partition and inside that extended partition you can have as many logical partitions as you like. You will not notice any performance issues from running Ubuntu from a logical partition or from having swap on a logical partition. Or having data in a logical partition for that matter. The data transfer rate of the hard drive is the important factor. Not whether the partition is primary or logical.

Ubuntu is often installed on logical partitions. I have several versions of Ubuntu installed and using logical partitions is the only way that I can install them because I do not GPT on my machine.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Regards.

---

### Post by Impavidus on 2014-09-12
I've got no experience with this myself, but I read that Windows doesn't like it to have logical partitions before its own partition. It wants to be in the first partition itself. That would mean that you have to place the logical partitions after the second or third primary partition.

But contrary to Windows, Ubuntu doesn't care being installed in a logical partition. No performance issues.

---

### Post by piadex2 on 2014-09-12
Dear Helpers,

First of all thank You for Your answers. To sum up no penalty when putting linux on logical partition but windows does not like logical partition go before its own partition.
After many experimental installations: no logical partitions !
When windows 7 creates its own 100MB partition for things I manually delete it and then create the NTFS work partition that I need. In this way there are only 4 partitions: 1 ext4, 1 swap, 1 win7, 1 data.
In this way everything is fine.
My next question is totally different so I create another thread for that.

Thank You again a lot.
Cheers.

---

