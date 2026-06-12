---
title: "Repartitioning with Unallocated Space"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by chismend01 on 2014-04-19
I have ran out of space recently, several months after I installed Ubuntu. I now use it for my Operating System, although I still have my old Windows 8 partion. When I installed, I had not given sufficient space, only testing it out. While on TryMe Mode, I used GParted to dedicate more space to the Ubuntu partition. The unallocated space was left of the current partition, and I was not able to transfer more space. I could add more space to the Windows 8 partition, but I didn't want to do so. Is there any way to add more space now, or should I back everything up and re-install Ubuntu? 
Any help would be appreciated. Sorry if this is a repost, I couldn't find a similar thread.
Ubuntu 13.10

---

### Post by Vladlenin5000 on 2014-04-19
If the new unallocated space is before the beginning of the partition you want to extend, your only option is to first 'move' that partition to the left thus resulting in the free space to exist at the end of the drive. Then you'll be able to resize it easily. Both operations can be done with GParted (in a live session).

---

### Post by monkeybrain20122 on 2014-04-19
Install gparted (or boot into a live usb) take a screenshot of what the partition layout looks like and what you want to do.

---

### Post by monkeybrain20122 on 2014-04-19
> **Vladlenin5000 said:**
> If the new unallocated space is before the beginning of the partition you want to extend, your only option is to first 'move' that partition to the left thus resulting in the free space to exist at the end of the drive. Then you'll be able to resize it easily. Both operations can be done with GParted (in a live session).

Not necessarily, it may be faster and safer to clone the partition, then delete all partitions and re-partition the drive and restore (sounds like a small partition to clone from OP)

---

### Post by chismend01 on 2014-04-19
The partiton is 128 gigabytes, although cloning seems to be a nice option.

---

### Post by monkeybrain20122 on 2014-04-20
All 128G used?

---

### Post by chismend01 on 2014-04-20
Thanks for the quick responses. I think most of the 128GBs are used, I should have 500 megabytes left.

---

