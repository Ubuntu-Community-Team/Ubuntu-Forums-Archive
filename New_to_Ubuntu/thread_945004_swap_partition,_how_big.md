---
title: "swap partition, how big ?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-10-11
ive always wondered this, what is the point of creating a swap partition in linux ? lets say i have 3gb of ram in my system, how big of a swap partition do i realistically need for optimum performance ?

---

### Post by echo314 on 2008-10-12
There is no best answer, its much up to debate. Plus, systems have changed quite a bit in the past few years, so past estimates (like 1.5x your ram or w/e) are not so accurate. 

Just set it at 2 gigs and you will be fine lol. other options will much more impact sys performance than swap

---

### Post by epidemiks on 2008-10-12
I recently resized my swap from 10GB (don't ask) to 2GB.
So far I've not seen ubuntu use more than 50Mb of swap..

---

### Post by Steveway on 2008-10-12
> **echo314 said:**
> There is no best answer, its much up to debate. Plus, systems have changed quite a bit in the past few years, so past estimates (like 1.5x your ram or w/e) are not so accurate. 

Just set it at 2 gigs and you will be fine lol

The 1.5x times of the RAM is a pretty accurate number.
It is meant to allow enough space so you can suspend to disk without a problem.
If you don't want to suspend to disk then you most propably won't need that amount of swap-space.

---

### Post by eternalnewbee on 2008-10-12
I've read in another thread that with newer machines swap isn't necessary anymore...

---

### Post by echo314 on 2008-10-12
Alright thanks for the update, knowing about it related to the suspend function is nice.

> **Steveway said:**
> The 1.5x times of the RAM is a pretty accurate number.
It is meant to allow enough space so you can suspend to disk without a problem.
If you don't want to suspend to disk then you most propably won't need that amount of swap-space.

---

### Post by ProNux on 2008-10-12
I have a 3GB RAM.  Do you think a swap partition (not swap file) of 2GB gives a noticeable performance?

---

### Post by bodhi.zazen on 2008-10-12
LOL

In general , the more RAM you have the less swap you need. keep in mind swap is used to expand your RAM using hard drive space.

In general, you want swap = ram X 2 , max 1 Gb. Some people say may 512 Mb or even no swap if RAM is 2 Gb or more.

With 3 gb ram you may be able to go with no swap.

The only exception is laptops. On laptops, to use sleep and suspend you need swap = ram. This is because when you use these functions what is in RAM is stored on HD and then reloaded when you wake up.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) 

    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml) 

    [http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

---

### Post by fidamehran on 2008-10-12
As per the conception I got all throughout the years, SWAP should be equal to your physical memory (RAM)if you have 512MB or 1 GB RAM. it could be double th RAM, if you have less RAM, like 256 MB. As for the "it's not needed anymore" I think, if you install Ubuntu through Wubi (from within Windows), you really don't need it.
But if you install Ubuntu the original way (Boot from CD, manual/automatic partitioning and stuff like that), I think you will need to allocate SWAP space; which is ideally equal to your RAM.

---

### Post by earthpigg on 2008-10-12
> **bodhi.zazen said:**
> LOL

In general , the more RAM you have the less swap you need. keep in mind swap is used to expand your RAM using hard drive space.

In general, you want swap = ram X 2 , max 1 Gb. Some people say may 512 Mb or even no swap if RAM is 2 Gb or more.

With 3 gb ram you may be able to go with no swap.

The only exception is laptops. On laptops, to use sleep and suspend you need swap = ram. This is because when you use these functions what is in RAM is stored on HD and then reloaded when you wake up.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) 

    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml) 

    [http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

is that why my laptop sometimes does not play nice with hibernate and sleep with 4 gigs of ram, and 1.5 gig swap?

ie: if my ram usage is at 800 megs and i go into hibernate, then there is no issue, but if i have 2 gigs of RAM being used then there isn't enough swap space to sleep properly... is that what is happening?

---

### Post by bodhi.zazen on 2008-10-12
> **earthpigg said:**
> is that why my laptop sometimes does not play nice with hibernate and sleep with 4 gigs of ram, and 1.5 gig swap?

ie: if my ram usage is at 800 megs and i go into hibernate, then there is no issue, but if i have 2 gigs of RAM being used then there isn't enough swap space to sleep properly... is that what is happening?

Most likely yes, but sleep and hibernate can be finicky.

Try increasing your swap size to say 4256 Mb (just a little larger then 4 Gb) and see if your performance improves.

Outside of sleep and hibernation, the links I gave you will show you how to calculate how much swap you need. If you read through those links you will get a better sense of how it works, and thus how big to make your swap.

---

### Post by earthpigg on 2008-10-12
ok, ill try fiddling with my swap size when i get home. i gave up on using sleep/hibernate several months ago, this is a new angle to approach the problem from, so we'll see what i can do :)

---

### Post by smooth3006 on 2008-10-12
so since i have 3gb of ram in my laptop i should create a 4.5gb swap partition ? :confused:

---

### Post by bodhi.zazen on 2008-10-12
> **smooth3006 said:**
> so since i have 3gb of ram in my laptop i should create a 4.5gb swap partition ? :confused:

No, 4.5 Gb swap is way too big.

If you use sleep and hibernate, make it 3.5 Gb, otherwise you probably do not even need swap. 0.5 Gb would be fine.

Look through the links I gave you as 4.5 Gb is way off target.

---

### Post by SunnyRabbiera on 2008-10-12
Well I still value swap myself despite my decent amount of ram (1 GB, more then enough for my needs) I think the swap still comes in handy.
It makes boot times faster on my machine actually.

---

### Post by bodhi.zazen on 2008-10-12
> **SunnyRabbiera said:**
> Well I still value swap myself despite my decent amount of ram (1 GB, more then enough for my needs) I think the swap still comes in handy.
It makes boot times faster on my machine actually.

I agree. In my experience 1 Gb is on the small side to eliminate swap.

Here is what it looks like with bigger ram :

> bodhi@Entropy:~$ free -m
             total       used       free     shared    buffers     cached
Mem:____2961 ___ 1131 ___ 1829          0         75        448
-/+ buffers/cache:        607       2353
Swap: __  3098 ____  0       3098See, no swap used :twisted:

The only reason I use a large swap is this is a laptop and my wife likes to put it to sleep.

But to answer the question "how much swap do I need" you need to understand your RAM and how you use it. You needs will vary if you stat using your RAM, such as virtualization.

---

### Post by smooth3006 on 2008-11-20
im about to install 4 gigs of ram on my laptop. would i set the swap to 5.5 gigs to equal 1.5 times greater ?

---

### Post by Jesan Fafon on 2008-11-20
> **smooth3006 said:**
> im about to install 4 gigs of ram on my laptop. would i set the swap to 5.5 gigs to equal 1.5 times greater ?

no. i believe the theme of this thread has mostly been"

"If you need to sleep, slightly more than your RAM, if not then around 512mb"

5.5 gb is way overkill.

---

