---
title: "Merging partitions"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-05-15
Is it possible for me to merge an 80GB empty partition with my 400GB partition where in which my /home directory is mounted?  My guess would be to make the 80GB partition the same file system as the /home partition and use Gparted?

---

### Post by MaindotC on 2008-05-15
Just format the 400GB partition with ext3 and you can access it and read/write to it just like it's an individual folder in your regular file system.

---

### Post by HotShotDJ on 2008-05-15
> **baddnady23 said:**
> Is it possible for me to merge an 80GB empty partition with my 400GB partition where in which my /home directory is mounted?  My guess would be to make the 80GB partition the same file system as the /home partition and use Gparted?Just delete the 80G partition, then expand the 400G partition into it.

---

### Post by louieb on 2008-05-15
If they are physically next to each other. 
And both are the same type (either primary or logical). Then one can be deleted and the other expanded to occupy the now unused space.  

If one is a logical partition and the other a primary partition then it gets a little tricker. The extended partition will need to grow or shrink depending on if the partition you want to have the unused space is a logical or primary partition. 

 It can be done with GParted or one of its forks like VisParted.  

BTW: Not a problem for you but if both partitions have data you want to keep, the data on one will have to be copied off some place safe and coppied back to the expanded partition. Don't know of any other way to merge two partitions with data in both and  have the resulting partition contain the data that was in both partitions.

---

### Post by UnWarierMage224 on 2008-05-15
Doesn't the empty one have to be after the one you want to add to, as well?
You can't add to the beginning of a partition, can you?

---

### Post by tacutu on 2008-05-15
To merge them "virtually" you can use LVM

---

### Post by HotShotDJ on 2008-05-15
> **UnWarierMage224 said:**
> Doesn't the empty one have to be after the one you want to add to, as well?
You can't add to the beginning of a partition, can you?I don't believe this is true.  However, I just happen to have an external 160 GiB harddrive with nothing better to do than serve as a test case.  Stand by... lets see what happens...

---

### Post by baddnady23 on 2008-05-15
well they both will be ext3 so i guess then i can just delete the one and expand the other which sounds like the easiest thing to do.  Ill have to check they both are primary/logical

---

### Post by HotShotDJ on 2008-05-16
Just a quick note.  I began my test about an hour ago.  Everything is working fine (apparently).  HOWEVER, the "Applying pending operations" dialog box tells me there are 3 hours, 28 minutes remaining to complete.  While it seems that one can, in fact, grow an ext3 partition into the free space preceding it, it is a SLOW process.  In my test case, it would have been much faster to copy the files I wanted to save to another drive and then delete the existent partitions completely, create & format a new partition, and then copy back the files.  This resizing thing should be used only as a last resort, unless you LIKE spending hours in this manner.

A full report on my test will be posted in about 3 1/2 hours. :)

---

### Post by Delever on 2008-05-16
> **HotShotDJ said:**
> Just a quick note.  I began my test about an hour ago.  Everything is working fine (apparently).  HOWEVER, the "Applying pending operations" dialog box tells me there are 3 hours, 28 minutes remaining to complete.  While it seems that one can, in fact, grow an ext3 partition into the free space preceding it, it is a SLOW process.  In my test case, it would have been much faster to copy the files I wanted to save to another drive and then delete the existent partitions completely, create & format a new partition, and then copy back the files.  This resizing thing should be used only as a last resort, unless you LIKE spending hours in this manner.

A full report on my test will be posted in about 3 1/2 hours. :)

It will be ok. You just need to pray that power suddenly don't disappear. That helped me when I did it.

:lolflag:

Basically, moving STARTING POINT of partition anywhere takes ages. Otherwise it is fast enough.

---

### Post by HotShotDJ on 2008-05-16
Thats it.  I canceled the operation.  Its 2:30 in the morning and it STILL had over 2.5 hours left.  I think my aborted test shows two things... 1) it is possible and 2) it takes a VERY LONG TIME.

---

### Post by louieb on 2008-05-16
> **HotShotDJ said:**
> ...  Its 2:30 in the morning and it STILL had over 2.5 hours left.  ...

:roll:I grew a 15GB partition w 7GB of data 5GB to the left once. Took several hours. Same time waste happens if you move a partition to left. Delever has it right on this one.

---

### Post by baddnady23 on 2008-05-16
thanks for the test and resaults hotshot.  so basically, i have just my home directory mounted on the 400GB, which means i would need to somehow back up the whole director/partition and then delete the two that i want to merge and copy my home directory back, then remount it to that partition?

---

### Post by Oldsoldier2003 on 2008-05-16
> **louieb said:**
> :roll:I grew a 15GB partition w 7GB of data 5GB to the left once. Took several hours. Same time waste happens if you move a partition to left. Delever has it right on this one.

Rather than grow partitions left I usually back up the data and delete the partitions. After doing that just recreate the partitions to the appropriate size and restore the data. Much Faster!

---

### Post by Oldsoldier2003 on 2008-05-16
> **baddnady23 said:**
> thanks for the test and resaults hotshot.  so basically, i have just my home directory mounted on the 400GB, which means i would need to somehow back up the whole director/partition and then delete the two that i want to merge and copy my home directory back, then remount it to that partition?

Thats what i would do. ( make sure you preserve permissions when you backup your /home)

---

