---
title: "Erratic slowdowns in Ubuntu 15.04"
date: 2015-06-09
forum: New to Ubuntu
---

### Post by Cleaver on 2015-06-09
Hi,

Ubuntu was fine until today, but a few hours ago it started behaving incredibly slowly until I rebooted it. I can't think of what happened, given I installed it about a week or two ago and changed the swappiness from 60 to 10 right after doing so. After a few reboots for various reasons, I've had this happen 2 or 3 times already today and it wasn't an issue at all yesterday or any time before.

Anyone else have similar problems and know a solution? Thanks.

---

### Post by buzzingrobot on 2015-06-09
> **Cleaver said:**
> Hi,

Ubuntu was fine until today, but a few hours ago it started behaving incredibly slowly until I rebooted it. I can't think of what happened, given I installed it about a week or two ago and changed the swappiness from 60 to 10 right after doing so. After a few reboots for various reasons, I've had this happen 2 or 3 times already today and it wasn't an issue at all yesterday or any time before.

Anyone else have similar problems and know a solution? Thanks.

You might open the System Monitor and keep it open, hoping to get a look at any processes that go haywire when things get slow.

Also, you might set swappiness back to its default and see what happens.  I've never, ever, changed it and never, ever, had any issues with swap. Machines won't start the continual swapping of data from RAM to the swap partition, which is, of course, very slow, until RAM fills up and stays full. If you have enough RAM left to allot it to a process requesting RAM, then you won't swap.

On the other hand, if the machine needs to swap but can't, for one reason or another, the process requesting the allocation of RAM won't get it. What happens next is unpredictable, but simply stopping wouldn't be a surprise.

---

### Post by cariboo on 2015-06-09
I have to agree, set the swapiness back to the default, as I've never had a problem with it.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          3839       3156        682        238        176       1753
-/+ buffers/cache:       1227       2612
Swap:         3814          0       3814
```

```
uptime
 19:41:11 up 3 days,  3:02,  2 users,  load average: 0.27, 0.29, 0.30
```

Even after being up for over three days, my system isn't using swap.

---

### Post by Cleaver on 2015-06-13
> **cariboo said:**
> I have to agree, set the swapiness back to the default, as I've never had a problem with it.

Why does anyone suggest lowering the swappiness? Is this maybe an outdated way of speeding up Ubuntu that no longer works? In the past few days I haven't noticed any slowdowns(and I forgot to even try resetting it to the default) but I'm really curious as to where this idea originated and what validity it has/had.

---

### Post by mörgæs on 2015-06-13
Good that you got it working though we don't know what happened.
Swappiness can have a great impact on old computers. I use it often when dealing with gear from the Pentium 4-ages and the like.

As with many pieces of advice in Ubuntuforums: Try it and see how it works for you particular computer.

---

