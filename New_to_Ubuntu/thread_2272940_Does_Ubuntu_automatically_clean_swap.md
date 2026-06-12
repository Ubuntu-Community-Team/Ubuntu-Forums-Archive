---
title: "Does Ubuntu automatically clean swap?"
date: 2015-04-09
forum: New to Ubuntu
---

### Post by muhh on 2015-04-09
HI All,

There are tons of sources on the internet for how to clean swap on Ubuntu, but I cannot find any information about what the system itself does about that.

For example I have:

Mem:       5217160    3838692    1378468      25672      37416     391896
-/+ buffers/cache:    3409380    1807780
Swap:      5206012     767728    4438284

Is Ubuntu going to do something with those 750 MB of swap at some point? Or they will stay there until a restart? What is the general policy for that?

Thanks!
Dmitry

---

### Post by Keith_Helms on 2015-04-09
The NSA code in the Ubuntu kernel clears the cache after it uploads it to their servers.

---

### Post by muhh on 2015-04-09
> **Keith_Helms said:**
> The NSA code in the Ubuntu kernel clears the cache after it uploads it to their servers.

LMAO, even a fifth grader knows there is no NSA code in the kernel, CIA takes care of that actually.

---

### Post by matt_symes on 2015-04-09
Hi

> Is Ubuntu going to do something with those 750 MB of swap at some point?  Or they will stay there until a restart? What is the general policy for  that?

I'm pretty sure the pages get written to swap and stay there until they get overwritten by other pages being swapped out although i would have to research this to be 100% sure. I don't think it gets erased with a restart. It's still on the swap partition. I am open to being corrected if this is old information.

Encrypting swap is the way forward if you want swap security.

Kind regards

---

### Post by buzzingrobot on 2015-04-09
Also, note that the swap partition is not formatted.  There's no filesystem on it.

Data swapped out to the partition remains there until a process requests it.  Then it's read back, with something else written out to make space, if necessary. Since the processes don't survive a restart, the entire partition is available again.

It would take a long time to really zero out a swap partition, particularly the multiple-gigabyte partitions many of us use, in search of security or privacy.

---

