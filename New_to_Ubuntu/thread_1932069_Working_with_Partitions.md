---
title: "Working with Partitions"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Dandyman10 on 2012-02-26
Hi
I was working with partitions on an Ubuntu LiveCD using GParted Partition Editor (because I wanted to separate my home folder). a message appeared, saying this operation could cause SEVERE data loss. So my question is - how safe is it to work with partitions, and how safe is the data on the partitions when changing them (apart from the fairly obvious reformatting/deleting ;))?

Side question - what is the difference between a primary, logical or extended partition?

---

### Post by grahammechanical on 2012-02-26
Have you ever heard the expression - You can't say we didn't warn you?

It is that kind of message. Back up your data. Be prepared for things to go wrong. Sometimes the worse does happen but I have never experienced it.

I have gone from having a / partition and a /home partition to adding another partition to install a different version of Ubuntu in, then a second extra partition and a third extra partition and recently I moved and resized the partitions because the partition I am using now was getting full and I am about to resize it again because I did not make it big enough before.

Each time I re-boot into my four versions of Ubuntu without any problems. But I am prepared for things to go wrong.

As regards creating a separate home partition. I did that. I followed directions from a Linux magazine and Ubuntu would not boot! It did not know where the new home folder was. And I did not have a back up of my data. So, after rescuing my data I finally worked out a simple fix. 

Re-install Ubuntu and in the process give the new /home partition the mount point of /home without a format. The Ubuntu knew where to look for my user configuration files that are in the home folder. Then I copied my data into the relevant folders.

What method are you using to set up this /home partition?

Regards.

---

### Post by Gone fishing on 2012-02-26
Playing with partitions is inherently risky and if you resize a partition etc and it goes wrong you can use all your data. Having said that I’ve only lost my data once (I’ve done it many times) and got almost all back with testdisk. So you should back up you important data first.

The MBR partition system only allows you to have 4 primary partitions to get around this you can create an extended partition, which can contain several logical partitions.

---

### Post by sudodus on 2012-02-26
> **Dandyman10 said:**
> Hi
I was working with partitions on an Ubuntu LiveCD using GParted Partition Editor (because I wanted to separate my home folder). a message appeared, saying this operation could cause SEVERE data loss. So my question is - how safe is it to work with partitions, and how safe is the data on the partitions when changing them (apart from the fairly obvious reformatting/deleting ;))?

Side question - what is the difference between a primary, logical or extended partition?
It works most of the time to edit partitions. But you never know when it will fail. So you should ***always backup*** your system or at least your personal data (pictures, documents, video-clips etc) before starting to edit partitions.

The master boot record (MBR) partitioning scheme can have maximum 4 primary partitions or 3 primary and 1 extended partition.
- A primary partition contains a file system or a swap area.
- An extended partition contains one or more logical partitions.
- A logical partition is inside an extended partition and contains  a file system or a swap area.
See [[COLOR="Red"]_http://en.wikipedia.org/wiki/Disk_partitioning_[/COLOR]]("http://en.wikipedia.org/wiki/Disk_partitioning")

---

### Post by wildmanne39 on 2012-02-26
Hi, also sometimes you will have to reinstall grub when you resize partitions this always happens to me.
Thanks

---

### Post by Lisiano on 2012-02-26
The message Grub tells you (As I understand it) that if stuff goes wrong, don't blain GParted. Though as others said, (re)partitioning is risky.

[LIST]
[*]Primary - Contains a filesystem
[*]Extended - Contains logical partitions
[*]Logical - Contains a filesystem
[/LIST]
The reason for why we have extended instead of just limitless or just a high number or primary is historical. In the old times people thought they didn't need more than 4. You can have somewhere to 70 of logical partitions (That's how far GParted let me go when messing with a USB Flash drive)

@wildmanne39 Grub needs to be reinstalled only if you touch the root partition I think.

---

### Post by Dandyman10 on 2012-02-28
Thanks for your help :)

---

