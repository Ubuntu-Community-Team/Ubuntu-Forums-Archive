---
title: "[SOLVED] Resizing of a partitioned hard-drive"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Berean on 2008-05-16
Hi,

I've installed Ubuntu on my internal HD alongside XP.  I am now weaning myself from Windows, and thus reduced the size of the partition.  I was hoping to resize the partition 8.04 is installed upon, but I've ended up with the smaller XP partition, an Ubuntu partition - which hasn't changed - and an unallocated partition.  I've been using the Live CD to do this, but would like to grow the Ubuntu partition to take in the unallocated partition as per my screen-shot.  Any ideas?  Regards,

---

### Post by bumanie on 2008-05-16
You should be able to extend the ubuntu partition to the left with the move/resize option and have it take the unallocated space. Be aware that there is a small chance of something going wrong (but I have never had it muck up). You are correct to use a live cd - ?gparted, I guess? Also be aware that extending the partition to the left will take considerable time to complete the operation. If you have tried this already, It may be that you have ubuntu and swap partitions inside an extended partition. You should be able to remove the extended partition. Hard drives can have 4 primary partitions, so you don't really need an extended partition due to the fact that xp, ubuntu and swap total three partitions. If it were me, I'd get rid of the extended partition anyway - that's just personal choice.

---

### Post by Berean on 2008-05-16
bumanie,

thanks.  That's what I thought but for some strange reason I'm not able to "activate" the partition to use the orange resize button!  Any ideas?

---

### Post by bumanie on 2008-05-16
Try deleting the extended partition first. Highlight it and choose delete - make sure you are deleting the light blue box around the ubuntu and swap aprtitions.

---

### Post by Berean on 2008-05-16
> **bumanie said:**
> Try deleting the extended partition first. Highlight it and choose delete - make sure you are deleting the light blue box around the ubuntu and swap aprtitions.

I'm not actually using the Live CD at the present (but in a few minutes) but just to be certain: I can delete the extended partition WITHOUT losing my whole ubuntu partition?  I've had a nightmare in the past, having to do away with 7.10 completely, and now I'm working my way back to where I was before.  I really don't want that to happen again!  Just give me a bit of reassurance bumanie, if you would be so kind.

---

### Post by indytim on 2008-05-16
Using GParted Live, re-size your **Extended** to partition to include the unused space to the left.  After that operation has completed, expand your ext3 with the new available space **WITHIN** your extended partition.

IndyTim

---

### Post by Crossroads on 2008-05-16
> **Berean said:**
> I'm not actually using the Live CD at the present (but in a few minutes) but just to be certain: I can delete the extended partition WITHOUT losing my whole ubuntu partition?  I've had a nightmare in the past, having to do away with 7.10 completely, and now I'm working my way back to where I was before.  I really don't want that to happen again!  Just give me a bit of reassurance bumanie, if you would be so kind.

Noooo!

Your extended partition contains your 2 Ubuntu partitons.
So if you delete the extended partition you will lose Ubuntu. :(

---

### Post by bumanie on 2008-05-16
> **Crossroads said:**
> Noooo!

Your extended partition contains your 2 Ubuntu partitons.
So if you delete the extended partition you will lose Ubuntu. :(

Crossrods seems very sure of his statement, so follow that. I have a recollection of removing an extended partition without ill effects, but it was a long time ago and may be my memory is not serving me well.

---

### Post by az on 2008-05-16
> **Berean said:**
> I can delete the extended partition WITHOUT losing my whole ubuntu partition?  

No, you can't.  That solution will only work if you don't care about your data.

> **bumanie said:**
> Crossrods seems very sure of his statement, so follow that. I have a recollection of removing an extended partition without ill effects, but it was a long time ago and may be my memory is not serving me well.

...so use caution when handing out advice.  

Don't do it.  Sure you can recover lost partitions, but you should not go about it that way.

---

### Post by Berean on 2008-05-16
Thanks to you all.  What I've actually done is resize the extended partition, and then increase the size of ext3 within it.  I have kept all of my data and increased the size of the partition that I had originally wanted.  Once again, many thanks.  Regards.

---

### Post by ipburbank on 2008-10-07
wait... how did you resize it? i thought it was un-resizeable... i'm having the same problem, but can't resize it.

---

### Post by indytim on 2008-10-07
Extended partitions are re-sizeable.  On the "upside" you have to have unallocated space adjoining the extended partition.  On the "downside" you will need to create unallocated space adjoining the extended partition wall you want to decrease to.  For example, if you want to shrink your extended partition smaller from the left side, then the left most partition **within** your extended will have to be shrunk from the left side thus creating unallocated space where the extended partition can be shrunk to. 

In this case, a picture would be easier.

IndyTim

---

### Post by handydan918 on 2008-10-08
Perhaps it would help to reiterate that this MUST be done from a live cd. gparted will not resize a mounted partition.

---

