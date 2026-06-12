---
title: "when I try to install linux mint it asks me to remove ubuntu"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by samalaa on 2012-09-12
Hi 
I'm trying to triple boot win7 ubuntu 12.04 and linux mint but when try to install the linux mint it asks me to remove ubuntu why this is happening ?
How can I install linux mint without removing ubuntu

---

### Post by Gone fishing on 2012-09-12
Have you tried manually partitioning? I would guess that when you try to install that mint is trying to use the existing linux partitions.

The solution is to manually partition - start on a live CD and run partition editor (gparted), make enough space to add a new partition this may involve shrinking a partition (this could take some time.) Once you have done this add a ext4 partition for your Mint / (root) partition and another for /home (you don't need to add another swap). 

Now when you install mint choose manual partitioning and then choose the partitions you have just created.

Remember if you are changing partitions to back up your data just in case (it is unlikely anything will go wrong but just in case)

---

### Post by Bucky Ball on 2012-09-12
You have four primary partitions already is my guess. You need to delete one and replace it with an extended partition. You can then create as many logical drives inside that as your hardware can handle.

This is an educated guess at your problem. Win usually takes two primary partitions, you have Ubuntu on another no doubt and /swap partition or data partition as another. You're done.

Just another wild guess: If you have a separate /home partition for your existing Ubuntu install you can use that for the Linux Mint install also. Choose 'Something Else' when you get to the partitioning section of the install and choose to use /home but NOT format it. ;)

---

