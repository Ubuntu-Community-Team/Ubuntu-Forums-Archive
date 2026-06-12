---
title: "swap not being used"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-18
i just noticed that my swap is not being used at all (after i installed some monitoring tools)

it should be set up correctly
swapon -a  works with out errors

 sudo blkid
/dev/sda1: UUID="A8C0F02FC0F004FA" TYPE="ntfs" 
/dev/sda5: UUID="A3C15431865880F1" LABEL="data" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="dd289307-9296-4a96-9881-5baacabaa674" 
/dev/sda7: UUID="fd678ae6-8cec-4cc8-bd00-5a74ef51805a" TYPE="ext3" 
/dev/sda8: UUID="59e27148-7aa9-42c7-8803-b0923a6e5d52" TYPE="ext3" 

and my fstab is set right (as far as i can tell)

but i still have 0% of swap used
 free -m 
             total       used       free     shared    buffers     cached
Mem:          2025        718       1306          0         31        396
-/+ buffers/cache:        290       1734
Swap:          823          0        823


is this right?

btw its a laptop xps 1210 w 2gig of ram

nutz

---

### Post by bilbo.san on 2008-05-18
Hey
Perhaps I am not the best one to answer this... but I had the same question when first installed Ubuntu and created the swap partition for installation. 
I can tell you that Ubuntu indeed needs the Swap partition as a memory resorce. You should not erase it or get rid of it... this is the advise I got from the experts.

b.

---

### Post by nutpants on 2008-05-18
thats what i thought... but it is never in use.. which would should mean that it will slow down my system with out it..

so how can i get it working the way it should.  unless it is and i just dont need it.

nutz

---

### Post by Mhurst1 on 2008-05-18
You dont want to be using your swap partition as it is slower then using RAM.

---

### Post by sdennie on 2008-05-18
Linux won't use swap unless it needs to.  There is actually a setting called swappiness that allows you to configure the point at which linux starts moving stuff from RAM to swap but, if you aren't using any swap to begin with, it's probably not worth messing with it.

---

### Post by Ocxic on 2008-05-18
Swap will only be used if needed.
My swap never gets used, and I have 4 GB of RAM. but even when I only had 1GB swap was rarely used. basically if you have anything over 1GB of RAM swap will prolly never be used, but it's always good to have around just in case.

---

### Post by bilbo.san on 2008-05-18
> **nutpants said:**
> thats what i thought... but it is never in use.. which would should mean that it will slow down my system with out it..

so how can i get it working the way it should.  unless it is and i just dont need it.

nutz

No... it should not be in use... it is just a temp memory resource. I donnot think that your system will slow down without it. Think about it as a 'spear tire', it is sitting there until it is needed. It is working the way it should. I woud not touch it really.

---

### Post by PinkFloyd102489 on 2008-05-18
Im on 512MB RAM with swappiness set to 0. It rarely gets used so I played around with the partitions and shrank the swap space from nearly 500MB to 32MB. 20 some is the highest Ive ever seen it, under heavy load.

---

### Post by sam_delta on 2008-05-18
as far as i know swap is also used when you hibernate/suspend

sam

---

### Post by SunnyRabbiera on 2008-05-18
> **nutpants said:**
> thats what i thought... but it is never in use.. which would should mean that it will slow down my system with out it..

so how can i get it working the way it should.  unless it is and i just dont need it.

nutz

well to understand swap is to understand how linux allocates memory.
Linux has great memory management because of SWAP, SWAP is sort of like back up memory and is usually used for hibernation modes and such.
As opposed to totalling out your main RAM like windows does, linux tends to be more efficient and only uses the memory when it is needed...

---

### Post by PinkFloyd102489 on 2008-05-19
Swap can be compared to the pagefile in Windows.

---

### Post by SunnyRabbiera on 2008-05-19
> **PinkFloyd102489 said:**
> Swap can be compared to the pagefile in Windows.

it can, but SWAP in linux is far better at its job.

---

