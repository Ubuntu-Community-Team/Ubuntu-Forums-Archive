---
title: "Dual boot windows and ubuntu 12.04 create SWAP Partition"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by ranrag on 2012-06-14
This is my first attempt at installing ubuntu 12.04 on my Acer D270 netbook(2 GB RAM).

First of all my partition table looks like [**this**]("http://i.stack.imgur.com/FE0UM.png").


Now the *48.83 GB* partition is an *ext4 partition* created using *GParted(ubuntu live CD)*. Now when I try to install ubuntu in this partition by clicking *install now* it prompts **No SWAP partition created**.

Now when I try to click on the ext4 partition to create SWAP nothing happens. I tried the options provided by the ubuntu installer **Add,Change** without any luck.

So, my question is how to create the SWAP partition. I understand that I cannot create more than **4 partitions** but now what needs to be done to create SWAP.

PS: This is my first attempt at installing linux.

---

### Post by jocefus on 2012-06-14
You need two partitions: one for file system and one for swap space
 
Swap space in linux is like a windows page file, however linux uses a seperate dedicated partition. The swap partition should be at least as large as your system's ram or a little larger IMO.
 
It would be easiest to delete the partition you created so it is unallocated space. Then use the ubuntu install cd and select "install alongside windows." It should automatically create the needed partitions.

---

### Post by prshah on 2012-06-14
> **ranrag said:**
> my question is how to create the SWAP partition. I understand that I cannot create more than **4 partitions** but now what needs to be done to create SWAP.

You are partially right in thinking you cannot have more than 4 partitions. However, if one of the 4 partitions is a logical partition, it can then have (nested) multiple partitions within it.

As suggested, the easiest way is to let the installer create the partitions for you; delete your manually created ext4 partition, and choose the unallocated space during installation when prompted.

If you MUST create the partitions manually, create an EXTENDED partition, first, then create two LOGICAL partitions within it, one 2.2 (or 4) GB swap partition, and the balance as an ext4 partition with mount point "/".

Please post back if you need more assistance.

---

### Post by darkomano on 2012-06-14
There is an extended partition already there ("holding" logical "d:") - no need to create. 
Just delete the ext4 partition and run Ubuntu installation it will create the needed partitions (logical) in the freed space.
 
There can be only 4 primary or 3 primary and one extended partition.
 
The extended partition can "hold" up to 128 logical partitions.
The logical partitions are chained starting from the root of the extended partition.

---

