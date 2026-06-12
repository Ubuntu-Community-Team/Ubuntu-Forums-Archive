---
title: "Drive explanation please"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by hardik2 on 2013-09-26
Hey all Ubuntu lover's!!...I'm new to it.. so i just googled some stuff and found this software Gpartion... When i opened it .. i got this. Well i couldnt understand anythin ... So can anyone explain me in detail what is this... I'm sending you a pic

---

### Post by deadflowr on 2013-09-26
What exactly do you want to know?

You have 2 primary partitions mark ntfs marked 1 and 2)(those are windows partitions)
An extended partition(marked 3)
And then two logical partitions inside the extended partition.
The ext4 partition is the one for the Ubuntu system
The linux-swap is for swap.

And then the normal megabyte of unallocated space.
I forget the reason for the megabytew of unallocated space, but there is one.

---

### Post by grahammechanical on 2013-09-26
It is quite simple really. :)  In Linux everything is viewed as a device. So dev = device. Hard drives are usually SATA drives. So, sd = sata drive and sda = sata drive a. The first, often the only hard drive. A second drive would be sdb, and so on.

Each partition on a hard drive is given a number, sda1, sda2, sda3, and so on. Like I said, simple. 

A machine that uses a BIOS can only have 4 primary partitions on each drive. Why? Don't ask. I am trying to keep this simple. :)  The way around this limitation is to use one of the primary partitions as an Extended partition and inside that Extended we can create any number of Logical partitions.

So, to read your hard disk partitions: 
sda1; sda2 and sda3 are Primary partitions
sda1 and sda2 are set aside for Windows.
sda3 is an Extended partition which has inside it 2 logical partitions sda5 and sda6.
sda5 is for the Ubuntu operating system.
sda6 is a swap partition that Ubuntu uses.

ntfs is a Microsoft disk format, whereas Ext4 is a Linux disk format. The mount point is a Linux thing where / = the root file system. We can set Linux partitions to have other mount points but there must always be / mount point which is where we install Ubuntu if we were making the partitioning selection ourselves instead of letting the Installer make the decisions.

The most important thing that you need to know, is to be careful using Gparted. You can break the OS. In fact we can break every OS on the disk. This is why Gparted is not installed by default in Ubuntu. In fact I would not install it at all. I have used Gparted but I always run it from a Ubuntu live session. That makes me think very carefully about what I am using it for.

One more thing. What happened to sda4? Now that is one of the mysteries of the universe. :) I guess that sda3 and sda4 are the same.

Regards.

---

### Post by DuckHook on 2013-09-26
> **deadflowr said:**
> ...I forget the reason for the megabytew of unallocated space, but there is one.

To make sure that the file system starts precisely on the beginning of a page boundary for SSDs and other solid state memory devices like USB sticks. It *must* be present and must *never* be allocated.

---

### Post by hardik2 on 2013-09-26
@[COLOR=#000000]deadflowr ... Hey!.. Thank's for giving me info.. Basically i'm new to this, so i had no idea.. 
 
 I want to know.. 

1) Now if i want to install windows so i could just do it in 1st and 2nd marked partion .. as it is ntfs ,rite ?? 
 
                   and

 2) if i want to make new partitions in ubuntu, then how should i proceed ?

 Thank you.  
  
   " A beginner " :) [/COLOR]

---

### Post by DuckHook on 2013-09-26
> **grahammechanical said:**
> ...The most important thing that you need to know, is to be careful using Gparted. You can break the OS. In fact we can break every OS on the disk. This is why Gparted is not installed by default in Ubuntu. In fact I would not install it at all. I have used Gparted but I always run it from a Ubuntu live session. That makes me think very carefully about what I am using it for.

+1

Good advice from grahammechanical. While I do have it installed (it is useful for reconfiguring external HDDs, USB sticks, etc.), I sweat every time I launch it. It is a good thing to be nervous whenever you use it. It can hose your system like nothing else, especially in the hands of new users who don't know what they are doing. Use with extreme care. Same goes for CLI commands like *parted* and the various versions of *fdisk*.

---

### Post by deadflowr on 2013-09-26
> **hardik2 said:**
> @[COLOR=#000000]deadflowr ... Hey!.. Thank's for giving me info.. Basically i'm new to this, so i had no idea.. 
 
 I want to know.. 

1) Now if i want to install windows so i could just do it in 1st and 2nd marked partion .. as it is ntfs ,rite ?? 
 
                   and

 2) if i want to make new partitions in ubuntu, then how should i proceed ?

 Thank you.  
  
   " A beginner " :) [/COLOR]

This might help explain things better than my brain.
[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

But for question 1, partitions are malleable, so even though your system is marked with 1, and 2 as ntfs partitions, it can be designed differently from drive to drive.
If I remember right Windows boot files, or system files(can't rememeber which) need to be in a primary partition, (partitions 1-4 are typically designated primary with an extended partition taking one if used) but the rest of Windows can be in a logical partition.

Anyway, do you have Windows installed or is that a leftover partitioning scheme from earlier times?
If you still have Windows, then those 2 partitions are where it is, and if not you have 2 ready made partitions that you can install to.

---

### Post by mansonfan78 on 2013-09-27
> **grahammechanical said:**
> It is quite simple really. :)  In Linux everything is viewed as a device. So dev = device. Hard drives are usually SATA drives. So, sd = sata drive and sda = sata drive a. The first, often the only hard drive. A second drive would be sdb, and so on.

Each partition on a hard drive is given a number, sda1, sda2, sda3, and so on. Like I said, simple. 

A machine that uses a BIOS can only have 4 primary partitions on each drive. Why? Don't ask. I am trying to keep this simple. :)  The way around this limitation is to use one of the primary partitions as an Extended partition and inside that Extended we can create any number of Logical partitions.

So, to read your hard disk partitions: 
sda1; sda2 and sda3 are Primary partitions
sda1 and sda2 are set aside for Windows.
sda3 is an Extended partition which has inside it 2 logical partitions sda5 and sda6.
sda5 is for the Ubuntu operating system.
sda6 is a swap partition that Ubuntu uses.

ntfs is a Microsoft disk format, whereas Ext4 is a Linux disk format. The mount point is a Linux thing where / = the root file system. We can set Linux partitions to have other mount points but there must always be / mount point which is where we install Ubuntu if we were making the partitioning selection ourselves instead of letting the Installer make the decisions.

The most important thing that you need to know, is to be careful using Gparted. You can break the OS. In fact we can break every OS on the disk. This is why Gparted is not installed by default in Ubuntu. In fact I would not install it at all. I have used Gparted but I always run it from a Ubuntu live session. That makes me think very carefully about what I am using it for.

One more thing. What happened to sda4? Now that is one of the mysteries of the universe. :) I guess that sda3 and sda4 are the same.

Regards.

sda 1-4 are reserved for primary partitions, all logical partitions start with sda5.  If you create another primary partition it would be numbered sda4.

---

