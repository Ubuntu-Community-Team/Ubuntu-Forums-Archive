---
title: "How to resize partition"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by esl1885 on 2008-04-30
Hi,

Now that Ubuntu is installed on the complete hard drive, how can I resize the ext3 partition and create a new partition, or increase the size of the swap partition?

I installed gparted, but in seems that you have to unmount the ext3 partition, but it will not let you. I assume that is because you are using it. 

Any help?

Sam

---

### Post by Six_Digits on 2008-04-30
Search. 

[http://ubuntuforums.org/showthread.php?t=771028&highlight=gparted](http://ubuntuforums.org/showthread.php?t=771028&highlight=gparted)
[http://ubuntuforums.org/showthread.php?t=728205&highlight=repartition](http://ubuntuforums.org/showthread.php?t=728205&highlight=repartition)

You'll basically have to run the LiveCD and do it from there.

---

### Post by esl1885 on 2008-05-02
OK, I downloaded Gparted, burned to a cd, booted the computer with it, made the changes I wanted to the hard drive, and clicked apply.

Computer started doing its thing and after 3 hours, was still doing it. The drive was making sounds the whole time and the drive activity light was on. Finally canceled the operation, rebooted the computer, and the hard drive was still the same as before.

Anyone have a suggestion as to how I can partition this hard drive. I really don't want to start over with a fresh install.

Sam

---

### Post by tjwoosta on 2008-05-02
well thats the way its done but it sounds like you have alot of data on the harddisk you might just want to let it go over night and see if that works  i know when i shrunk mine it took about 2 hours but i only had about 20 gigs of data on it.
what it has to do is copy and move all of the data so theres room for the new partition

---

### Post by esl1885 on 2008-05-02
I only have a little over 3 gigs on the drive. It is a fresh install on a 40 gig hard drive.

Sam

---

### Post by bilbo.san on 2008-05-02
Hey,

If you still have the Windows installed on your pc, you could do merge, increase or resize partitions using DiskDirector... I have used it to do exact the same thing you need to do.

Good luck
b.

---

### Post by esl1885 on 2008-05-02
Unfortunately there is only Ubuntu on the drive. Otherwise, i would use Acronis PartitionExpert.

The drive is clean with only a new install of Ubuntu on it. That is why I thought it would take a lot less than 3 hours.

Thanks,

Sam

---

### Post by Six_Digits on 2008-05-03
> **esl1885 said:**
> OK, I downloaded Gparted, burned to a cd, booted the computer with it, made the changes I wanted to the hard drive, and clicked apply.

Computer started doing its thing and after 3 hours, was still doing it. The drive was making sounds the whole time and the drive activity light was on. Finally canceled the operation, rebooted the computer, and the hard drive was still the same as before.

Anyone have a suggestion as to how I can partition this hard drive. I really don't want to start over with a fresh install.

Sam

I don't understand why that wouldn't work... As tjwoosta stated, just try being patient. Partitioning can take a while, depending on your computers characteristics. I would personally try the LiveCD and if that doesn't work - Backup and re-install.

---

