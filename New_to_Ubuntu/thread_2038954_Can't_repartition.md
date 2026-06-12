---
title: "Can't repartition"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by whoknewbuntu on 2012-08-07
I've walked into a mess, and I can't find a post like mine.  My server tried to update itself to 12.04, but crashed.  On boot, it hangs, with either a black screen with a blinking cursor, or a purple screen with black borders on the side.

I suspect that the problem is a lack of disk space for the boot partition; it's only 240 MB.  I didn't set this up.

So I thought I would just resize the boot partition.  The server has two 240 GB hard drives, set up in a RAID 1 configuration.  (I think it's using fakeRAID, but again, I didn't set it up.)  So I figured 20 GB for the boot partition, 1 GB for a swap partition, and the rest in one big partition.

 I read up on how to do this, and thought I'd try gparted.  I booted to a Live CD and ran it.  However, gparted shows the partitions with an Unknown file system (with an exclamation point in a red circle), so it won't let me resize.

I've attached gparted images showing what I see when I look at the 2 drives in the RAID array (/dev/sda and /dev/sdc; /dev/sdb was assigned to an external USB drive).  I've also attached the results of fdisk -l.

Does anyone know if I can rescue the partitions?  I'm trying to avoid a reinstall.

Thanks in advance.

---

### Post by oldfred on 2012-08-07
Welcome to the forums.

I do not know nor use RAID. Someone else may be able to give better details:

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Also /boot does not have to be large if it is a separate partition. If you want 20GB that would be for / (root) not a separate  /boot partition. You may just need to houseclean out older kernels.

---

### Post by whoknewbuntu on 2012-08-08
OldFred,

Thanks for the suggestions.  I tried cleaning out old kernels, but it appears that 240 MB is just not enough space.  So I'm hoping to find some way to resize.  

Thanks again.

---

### Post by oldfred on 2012-08-08
Did you empty trash also? Space is not freed up until trash is emptied.

---

### Post by whoknewbuntu on 2012-08-08
Yes, I emptied the trash, but the necessary kernels seem to be too big to fit into a 0.24 GB partition.

---

### Post by oldfred on 2012-08-08
I have not housecleaned /boot recently and have 4 kernels in 96MB. mine is part of / as it is a desktop. But the kernels are the same.

---

