---
title: "sda2 = sda5 in Gparted"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-14
Does this look right? From Gparted:

/dev/sda1  ext4  27.46 GiB
/dev/sda2  extended 493 MiB
/dev/sda5  unknown 493 MiB

---

### Post by Elfy on 2012-09-14
In relation to what?

You have an ext4 partition in sda1 and a logical partition in sda5 that gparted does not recognise - sda2 is the extended.

---

### Post by deadflowr on 2012-09-14
Think of extended partitions as containers for logical partitions.
Hard drives can have a maximum of four primary partitions, but to expand beyond this, you can set one of them as an extended which in turn can house many more logical partitions.

---

### Post by Rallg on 2012-09-14
The result from gparted is possibly right.

It is not the case that sda2 = sda5, however.

My guess is that in the past, you did the following: sda1 is your Ubuntu partition. sda2 is the remainder of the hard drive, created as an exended partition.

EDIT: Per subsequent posts, this line is incorrect: You may have created partitions sda3, sda4, and sda5, then deleted sda3 and sda4. If so, gparted won't re-count; the former sda5 is still sda5 even though 3 and 4 are gone.

If sda2 is an extended partition, and sda5 is the only sub-partition within it (occupying all of sda2) then indeed you can see the result that you see. But even though sda5 occupies all of sda2, it is not the case that they are "equal" logically. In fact, they are not equal in exact byte count, because sda2 has some information specific to its partition system, which is not included in sda5. You don't need to know this, as it is invisible to most users.

If the partitions are the way I suggested, there is another difference: sda2, the extended partition, is not formatted and cannot be formatted to (say) ext4 or ntfs or whatever, whether or not it has any sub-partition. But sda5 can be formatted and used for storing files.

That is, sda2 is just a wrapper around other things. In this case, only sda5 is inside the wrapper.

---

### Post by coffeecat on 2012-09-14
> **Rallg said:**
> 
You may have created partitions sda3, sda4, and sda5, then deleted sda3 and sda4. If so, gparted won't re-count; the former sda5 is still sda5 even though 3 and 4 are gone.

As a point of information, not necessarily. Logical partitions are always numbered 5 and upwards, so it is entirely possible to create a partition table with sda1, sda2 and sda5 in one go. In fact I wouldn't be surprised if this layout was created by the Ubuntu installer, and sda5 was the swap partition which has subsequently become corrupted, hence the unknown from Gparted. If you choose the whole drive option in the Ubuntu installer it usually create a sda1 = primary ext4, sda2 = extended, sda5 = swap layout.

---

### Post by Sonoran Desert Rat on 2012-09-14
I used a Lubuntu live CD. Maybe I should have been less lazy. I want to know what is where, why and how to use it. I overwrote Windows XP entirely (something I DO NOT regret!). Is Gparted the best program for this?

edit: How do I figure out if it's corrupted? I'd like to know for sure.

---

### Post by deadflowr on 2012-09-14
> **Rallg said:**
> The result from gparted is possibly right.

It is not the case that sda2 = sda5, however.

My guess is that in the past, you did the following: sda1 is your Ubuntu partition. sda2 is the remainder of the hard drive, created as an exended partition.

You may have created partitions sda3, sda4, and sda5, then deleted sda3 and sda4. If so, gparted won't re-count; the former sda5 is still sda5 even though 3 and 4 are gone.

If sda2 is an extended partition, and sda5 is the only sub-partition within it (occupying all of sda2) then indeed you can see the result that you see. But even though sda5 occupies all of sda2, it is not the case that they are "equal" logically. In fact, they are not equal in exact byte count, because sda2 has some information specific to its partition system, which is not included in sda5. You don't need to know this, as it is invisible to most users.

If the partitions are the way I suggested, there is another difference: sda2, the extended partition, is not formatted and cannot be formatted to (say) ext4 or ntfs or whatever, whether or not it has any sub-partition. But sda5 can be formatted and used for storing files.

That is, sda2 is just a wrapper around other things. In this case, only sda5 is inside the wrapper.

If you delete a partition, then gparted would read it as unallocated. I know from experience.

Coffeecat has the right idea, in that the partition sda5 most likely contained the swap partition, which ended up getting corrupted. You can try to reformat it as swap, using gparted, to see if it might have been an initial error, or if it is a hard drive corruption.

---

### Post by Sonoran Desert Rat on 2012-09-14
I think this is it:

[http://ubuntuforums.org/showthread.php?t=2057849](http://ubuntuforums.org/showthread.php?t=2057849)

see the last post, I did encrypt.

---

### Post by coffeecat on 2012-09-14
> **Sonoran Desert Rat said:**
> 
see the last post, I did encrypt.

That's good - there's nothing to worry about. Gparted reports encrypted partitions as unknown, so if you opted for an encrypted swap partition when you installed, it's not corrupted.

---

