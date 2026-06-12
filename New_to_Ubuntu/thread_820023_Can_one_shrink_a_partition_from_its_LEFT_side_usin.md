---
title: "Can one shrink a partition from its LEFT side using gparted?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by swarup on 2008-06-05
I have a triple boot WinXP/Ubuntu Hardy/Puppy Linux 3.01. Looking at the partitions in gparted, they are going from left to right: WinXP/Hardy/Puppy/Swap. WinXP is a primary partition sda1, then there is an extended partition sda2 inside of which are three logical parititions: Hardy (sda5), Puppy (sda7), swap (sda6). 

My question is this: I need to expand the WinXP partition by around 2 GB. The only way to create the space is to shorten the Hardy partition from Hardy's LEFT side, so that space is created on WinXP's right side for WinXP to expand into. But of course, all of Hardy's material is on the left half of the partition, and the free space is on the right half of the Hardy partition. If I select to RESIZE (shrink) the Hardy partition from the LEFT side, will Hardy move all its folders etc safely toward the right half of the partition so as to shrink the left side? Or is shrinking from the left side problematic and one can only shrink from the right side (in which case, I am in problem).

---

### Post by srt4play on 2008-06-05
"Shrinking from the left side" will work.  Gparted will copy the data to a different area of the partition if needed.

---

### Post by swarup on 2008-06-05
I see, very interesting. So does that mean that there is no greater danger in shrinking from the left side than the right? Since the OS and files etc are on the left side, is there any increased risk in shrinking from the left? 

Or-- is "left" and "right" all just a way of making a picture for humans to look at whereas in the true picture of what is going on there isn't any "left" or "right"? Is there actually a "left" and a "right" to the partition as per the way it appears in gparted?

---

### Post by bumanie on 2008-06-05
It is possible but I'm not sure how it works as all the linux distros are in logical partitions. You will not be able to shrink the partitions as such, due to the logical/extended partition/box - you will have to shrink the logical partition box. I'm not exactly sure how well that works. Be aware, it will take considerable time as there are filesystems involved.

---

### Post by swarup on 2008-06-05
> **bumanie said:**
> It is possible but I'm not sure how it works as all the linux distros are in logical partitions. You will not be able to shrink the partitions as such, due to the logical/extended partition/box - you will have to shrink the logical partition box. I'm not exactly sure how well that works. Be aware, it will take considerable time as there are filesystems involved.

I have often shrunk logical partitions in the past, without any problem whatsoever. But I always did it from the right side-- not the left.

In the current case, I was thinking that I would first shrink sda5 (Hardy) from the left side by 2 GB, which would create an empty space of 2 GB to its left side-- outside sda5 but *inside* the extended partition sda2. I would then shrink the extended partition sda2 by 2 GB from *its* left side. That would put the 2GB just to the right of WinXP (sda1), in between WinXP and the extended partition containing all the linux distros. I would then in the last phase simply extend WindXP by 2GB to the right, thus taking over the freed 2GB for WinXP. 

You have said it will take considerable time-- does it take longer to shrink from the LEFT side than the RIGHT, as the file systems are located on the LEFT?

---

### Post by wdaniels on 2008-06-05
> **swarup said:**
> Or-- is "left" and "right" all just a way of making a picture for humans to look at whereas in the true picture of what is going on there isn't any "left" or "right"? Is there actually a "left" and a "right" to the partition as per the way it appears in gparted?

Obviously it isn't really "left" and "right" (with the disk being organised in circular tracks) but for the partition itself there is certainly a "beginning" and "end" of a continuous segment of the disk. However, it is not usually so simple for the filesystem data structure that occupies that space, and the algorithms for allocating blocks and inodes in ext filesystems try to keep blocks together for the same files and directories (to reduce fragmentation) which involves some amount of pre-allocating of adjacent blocks etc. Basically, the data is not allocated contiguously from beginning to end, so shrinking from the "right" is not just a case of truncating the end of the partition, and in this sense it carries practically the same level of risk as shrinking from the "left" - the filesystem has to be rewritten to some degree in either case.

---

### Post by swarup on 2008-06-05
I see, so is there any significance at all to the fact that in gparted all the data in any partition is always pictured as being on the left side. In other words, is there any difference *at all* between shrinking from the left versus the right side? 

Whether it is really a "left"/"right" difference or in reality another sort of difference-- is there any practical difference between what is pictured in gparted as the left side, and what is pictured in gparted as the right side?  

Or "left" and "right" here is just for viewing convenience and doesn't carry even any symbolic or representative meaning at all on any plane of the drive itself.

---

### Post by Delever on 2008-06-05
the main difference that it takes ages, i experienced that with ntfs partitions. but it worked.

sometimes, it is faster to move data somewhere else, delete partition, and move it back.

---

### Post by wdaniels on 2008-06-05
> **swarup said:**
> I see, so is there any significance at all to the fact that in gparted all the data in any partition is always pictured as being on the left side.

No, it only represents the proportion of the filesystem that is allocated/free.

> **swarup said:**
> In other words, is there any difference *at all* between shrinking from the left versus the right side? 

So far as the filesystem is concerned/aware, no - shrinking is shrinking and is the same operation. The difference is that if you're shrinking from the left, the partition also has to be moved, which doesn't involve rewriting the filesystem, but does involve moving a lot of data. The "risk" mostly lies in reorganising the filesystem for the shrinking, which is the same either way, but it will take *longer* to shrink the filesystem and then move all the data for partition.

---

### Post by swarup on 2008-06-05
Bottom line: I have done a lot of shrinking on the right side in the past, and it only takes 15 minutes for a 2-3 GB shrink. Is shrinking from the left side going to be similar, or could it take hours and hours? (And of course, if that much more time is involved, then more work is involved and attendant risk would also increase significantly.)

@wdaniels: your post just above answered my question. (We posted at virtually the same time, so I didn't see yours.)

---

### Post by Delever on 2008-06-06
for 160gb partition it took about 6 hours. it was 70 percent full. that was one big risk, even with ups.

---

### Post by swarup on 2008-06-06
> **Delever said:**
> the main difference that it takes ages, i experienced that with ntfs partitions. but it worked.

sometimes, it is faster to move data somewhere else, delete partition, and move it back.

Now I am getting the picture. 

But if the "data" we are talking about is an entire OS (Ub Hardy [sda5]), then to transfer the data to another drive, delete original partition and then recreate partition and bring back OS, would involve creating a mirror image (to a backup HD). And then restoring the mirror image. And that would take time too. But ok, I get the picture. When dealing with the left side, it is just going to take time no matter how it is done. --Whether by shrinking the partition, or by creating mirror images.

---

### Post by swarup on 2008-06-06
> **wdaniels said:**
> No, it only represents the proportion of the filesystem that is allocated/free.



So far as the filesystem is concerned/aware, no - shrinking is shrinking and is the same operation. The difference is that if you're shrinking from the left, the partition also has to be moved, which doesn't involve rewriting the filesystem, but does involve moving a lot of data. The "risk" mostly lies in reorganising the filesystem for the shrinking, which is the same either way, but it will take *longer* to shrink the filesystem and then move all the data for partition.

Thinking more about this point, I find that I am still confused: On the one hand you have said that the left/right spectrum in gparted "only represents the proportion of the filesystem that is allocated/free". i.e. that there is no geographic significance to the left/right distinction. But then further on you indicate that it is more than just an allocated/free proportion; rather, there *is* a geographic difference between shrinking from left side versus right i.e. that the data really *is* located on the left side and therefore takes longer to shrink/move from the left (than from the right, as the data is not located there).

---

### Post by wdaniels on 2008-06-06
It has more to do with the intelligence of the program really - it would be theoretically possible to shrink an ext filesystem from the left then just edit the partition table so that it starts at a later point, but I don't think anything does this.

The thing is, even though the blocks are spread out across the whole space, the boot block and block 0 hold special significance in the structure and it would be more difficult to try to move those to the right for the shrinking operation. So, yes, I suppose there is *some* significance to the data at the beginning of the partition, but not in the way that it might look.

I may be getting some of the exact details wrong (I'm not an expert on filesystems) but I think I'm right in principle. What I was trying to do was explain that the data isn't all clustered to the left as depicted in gparted, and that shrinking from the right doesn't avoid reorganising the data.

---

### Post by swarup on 2008-06-06
I see now, yes-- that makes sense. It gives a way of thinking about it.

---

