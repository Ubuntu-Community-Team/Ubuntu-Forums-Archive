---
title: "what is the ideal swap size?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by 007casper on 2012-11-24
It used to be that swap should be double the ram size.  Is it still same?

If I have 8gig ram, what should be the swap size? 16gig?

please, advise.  Thank you.

---

### Post by vuarnet on 2012-11-24
afaik it is 25% larger than your actual ram (this is what mine is)... e.g. 10GB swap for 8GB of physical RAM. but i'm not 100% sure so i'll keep an eye out on this thread and learn...

---

### Post by RoosterHam on 2012-11-24
The golden rule of double your installed ram started sounding excessive to me once I began installing on 4Gb ram systems...
But in situations where there's 500GB hard drives and bigger available I continue to use the same rule. In many situations I still have no more than 120GB of disk space, so I simply match the swap partition total to the total ram.

So far I haven't had any issues. Perhaps this is not good practice tough.

---

### Post by DuckHook on 2012-11-24
There is no rule. It depends on what you intend for your swap. At 8 GB, you really don't even need a swap unless you intend on having a dozen major apps open at once or wish to work on huge graphics files. However, the single biggest factor is whether you intend to hibernate your system. If so, then you absolutely must define a swap equal to at least the amount of your system memory in GiB (not just GB). If not and if you never have any more than half a dozen typical programs running, then you may not even want a swap. The problem with defining a swap partition is that the system will resort to it even if you don't want it to, and this slows the system down. Leaving a swap file/partition out of your install will force your system to aggressively manage cache and generally give you snappier response.

The above is an oversimplification, but for purposes of general discussion, it is pretty accurate.

---

### Post by 007casper on 2012-11-24
thanks

---

### Post by vuarnet on 2012-11-25
just re-sized mine lol thx also :)

---

