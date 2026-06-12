---
title: "Partition help"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by DiemWolf on 2008-06-11
I'm completely new at linux and i don't know too much about computers to begin with and i need some help with the whole partition thing for installing ubuntu. 

I started the install process and got to the screen that is titled "Prepare partitions"

In the box it says:

/dev/sda
  /dev/sda1  fat16   42MB    
  /dev/sda2  ntfs    56G
 */dev/sda3  ntfs    18G*
  /dev/sda4  fat32   4G
  unusable           8MB

and when i choose which partition i want to install ubuntu on (the one with stars around it) it tells me "No root file system is defined. Please correct this from the partitioning menu"  I can't figure how to do that, can someone try to walk me through this? Thanks!

---

### Post by KingTermite on 2008-06-11
Looks like the partition already exists and is formatted as NTFS. Use the partition tool and delete the partition so its just a free space partition.

---

### Post by Duck2006 on 2008-06-11
This may help with installing.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by cardinals_fan on 2008-06-11
Follow the guide at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

EDIT: Duck2006 beat me to it ;)

---

### Post by Paqman on 2008-06-11
First of all, partitioning is not compulsory for installing Ubuntu. You can use the Wubi installer to skip the partitioning. Just put your LiveCD in while running Windows to start Wubi. It'll create a virtual hard drive on your Windows partition and install Ubuntu in it.

If you do want to do manual partitioning you'll need to firstly back up all your data. Then defrag your NTFS partitions thoroughly. I like Auslogics Disk Defrag, it's a lot quicker than the default Windows defragger.

Before we get into the actual nuts-and-bolts of how to partition it's important that you have a plan. Do you know what partitions you want to make? 

In your case you already have four primary partitions, which is the most a drive can have. To create any more partitions you'll have to delete one of you current partitions and make an extended partition, which functions like a container that can include more partitions inside. That will allow you to break the four partitions limit. Ubuntu will need 2-3 new partitions.

---

### Post by DiemWolf on 2008-06-11
How do i make it the root file after it becomes free space?

---

### Post by Paqman on 2008-06-11
> **DiemWolf said:**
> How do i make it the root file after it becomes free space?

Create a new partition > Format as ext3 > select partiton > Use as > /

---

### Post by DiemWolf on 2008-06-11
After i format as ext3 and use as / how do i make a swap drive?

---

### Post by Duck2006 on 2008-06-11
Would he/she have to make two partitions? One for / root and the other one for swap.

---

