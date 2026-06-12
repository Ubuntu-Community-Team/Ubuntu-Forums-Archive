---
title: "Question on Disk Partitions"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by clovisdecruz on 2012-06-11
Hello,

I have created one Linux swap (0x82) partition and 3 Linux (0x83 ext4 version 1.0) partitions using Disk Utility . I want to create more partitions, with my extra space but now I am unable. Do I have to change some of the existing partitions to extended type to do so? Can anyone suggest a solution (if possible) to create more partitions without deleting the existing ones? Also confusing is that there are so many partition types to choose from. I wanted to created separate partitions for my documents, pictures, music and videos in addition to the exisiting OS & swap file partition.

Can anyone help?

Clovis

---

### Post by carl4926 on 2012-06-11
You can only have 4 primary partitions.
You need to create extended space for logical partitions to have more.

NB: A extended partition is a Primary

---

### Post by clovisdecruz on 2012-06-11
Hey thanks for the quick reply carl4926,

So am I right in saying that an extended partition will contain logical partitions?

---

### Post by carl4926 on 2012-06-11
> **clovisdecruz said:**
> Hey thanks for the quick reply carl4926,

So am I right in saying that an extended partition will contain logical partitions?
Correct                         :D

---

### Post by fantab on 2012-06-11
> **clovisdecruz said:**
> I have created one Linux swap (0x82) partition and 3 Linux (0x83 ext4 version 1.0) partitions using Disk Utility . I want to create more partitions, with my extra space but now I am unable. Do I have to change some of the existing partitions to extended type to do so? Can anyone suggest a solution (if possible) to create more partitions without deleting the existing ones? Also confusing is that there are so many partition types to choose from. I wanted to created separate partitions for my documents, pictures, music and videos in addition to the exisiting OS & swap file partition.

Like Carl4926 says above you can have only FOUR Primary Partitions. 

So what you can do is CREATE Three (3) PRIMARY Partitions and an EXTENDED PARTITION. An Extended Partition is only a 'container' that houses LOGICAL Partitions. You can have more that 4 Logical Partitions. 

If I am not mistaken Logical Partition starts its numbering from 5, ie it will always number itself from, say, /dev/sda5 and the next Logical Partition will be numbered /dev/sda6 and so on. 

I don't think you need separate partitions for Documents, Videos etc. But its your choice.  If I were you, I would create one 20GB Primary for '/' ext4 for Ubuntu, another 20GB Primary ext4 (in case you need to install any other Distro and dual boot), and the rest of the HDD space will be allocated to Extended Partition with one Logical Partition for SWAP about 2-4GB and another Logical Partition with remainder of Space formatted as just ext4 to store all your DATA. You will have to manually mount this Data Partition after every Ubuntu Boot or you can choose to automount it as ubuntu boots.

---

