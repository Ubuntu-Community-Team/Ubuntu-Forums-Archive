---
title: "64bit Linux with only 3GB RAM"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Malacath on 2013-03-10
I recently got fed up with windows freezing and taking ages to boot up so installed Ubuntu as a dual boot setup.

After installing I realised I had installed the 32bit version.

Are there any benefits to having the 64bit version if your computer has only 3GB RAM?

I don't want to go through the hassle of replacing the 32bit version with the 64bit version if there are no benefits.

---

### Post by Impavidus on 2013-03-10
Not much. Some programs will be faster using the 64 bit version. On the other hand, programs will use more memory. 3GB RAM is a bit of a grey area in the choice between 32 and 64 bit. But if you just installed it shouldn't be a lot of trouble to switch to 64 bit.

---

### Post by varunendra on 2013-03-10
64 bit is the size of instructions that are passed to the cpu for performing tasks. It is not just about addressable memory, but also about operand and instruction size.

The simplified version of this statement is that the execution of programs is supposed to be much faster on a 64 bit OS, provided the executing program does support 64 bit instruction set.

In practical experience so far, the performance is 'usually' better, but not in everything.

My personal advice is to try using both 32 bit and 64 bit on live cd (not installed vs. live), then decide yourself.
Also, if it is not too much hassle, 64 bit is always recommended if you have even 1 GB of RAM.

---

### Post by tartalo on 2013-03-10
In theory the 64bits version should be faster, but it's unnoticeable in most cases.

There are some little disadvantages too, for example Wine still needs to install all the 32bits libraries to work properly.

You can keep using the 32bits version and everything will work fine.

---

### Post by Malacath on 2013-03-10
Thanks for the replies. I'll stick with 32bit. It seems to be working fine and am not having any problems.

Is there an easy way to resize the partition Ubuntu uses?
When installing I only gave it 80GB. It wasn't clear which partition was for windows and which was for ubuntu when I was installing so linux ended up with the smallest partition.

---

### Post by Impavidus on 2013-03-10
Better to start a new thread for each new question, but here is a quick answer: use gparted from a live cd. If you need to shrink the windows partition you can do that using the windows tool.

---

### Post by varunendra on 2013-03-10
> **Malacath said:**
> Thanks for the replies. I'll stick with 32bit. It seems to be working fine and am not having any problems.

Is there an easy way to resize the partition Ubuntu uses?
When installing I only gave it 80GB. It wasn't clear which partition was for windows and which was for ubuntu when I was installing so linux ended up with the smallest partition.

You can use Gparted (included on the live cd) to manipulate partitions.

But be sure NOT to touch windows partition (or its boot partition) with gparted or any external tool. If required, defragment, then use windows' own disk management utility to shrink its partition(s).
Then boot with the live cd > run gparted > expand the Ubuntu partition to fill the space.

But also be aware that resizing ANY partition from it's 'Left' side will take eternity to complete (slightly exaggerated ;)). In that case, it is much-much quicker to just delete --> recreate the partition. If that happens to be Ubuntu's root partition, then you are looking for some complex operation that needs to be wisely performed.

---

### Post by ViliX64 on 2013-03-10
Just use 32bit.. it is more safe..

---

### Post by varunendra on 2013-03-10
> **ViliX64 said:**
> Just use 32bit.. it is more safe..

Safe ??

To be honest, I have never heard of, and can not think on a single reason why there would be a difference in 'safety' between the two versions.

If you are concerned about compatibility of programs/drivers, it used to be a real concern some 6-7 years ago, not anymore. In Linux, absolutely not!

But it's just my personal opinion, and I'm open for corrections :)

---

### Post by Malacath on 2013-03-10
> **varunendra said:**
> You can use Gparted (included on the live cd) to manipulate partitions.

But be sure NOT to touch windows partition (or its boot partition) with gparted or any external tool. If required, defragment, then use windows' own disk management utility to shrink its partition(s).
Then boot with the live cd > run gparted > expand the Ubuntu partition to fill the space.

But also be aware that resizing ANY partition from it's 'Left' side will take eternity to complete (slightly exaggerated ;)). In that case, it is much-much quicker to just delete --> recreate the partition. If that happens to be Ubuntu's root partition, then you are looking for some complex operation that needs to be wisely performed.


Thanks

---

### Post by varunendra on 2013-03-10
> **Malacath said:**
> Thanks

Welcome :)

And if you are indeed going to dual boot and not sure about partition plan, I'd suggest to post your question in a new thread with output of -
```
sudo fdisk -l
```
from ubuntu live session.

---

### Post by oldos2er on 2013-03-10
> **Malacath said:**
> Are there any benefits to having the 64bit version if your computer has only 3GB RAM?

I don't want to go through the hassle of replacing the 32bit version with the 64bit version if there are no benefits.

Absolutely there are benefits; why not use your hardware to its full potential? CPU-intensive tasks such as video encoding will be noticeably faster; for day-to-day tasks like web browsing and email you may not notice much difference.

---

### Post by oldos2er on 2013-03-10
> **ViliX64 said:**
> Just use 32bit.. it is more safe..

Please don't spread FUD.

---

