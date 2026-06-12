---
title: "Ubuntu takes up alot of ram."
date: 2014-05-29
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-29
Hi,

My laptop uses Ubuntu 14.04 LTS and with only having my terminal open to check my cpu status it already takes up 2500 memory and i only have 3724 max.
How come it uses so much of my cpu?

---

### Post by sandyd on 2014-05-29
> **gijs2 said:**
> Hi,

My laptop uses Ubuntu 14.04 LTS and with only having my terminal open to check my cpu status it already takes up 2500 memory and i only have 3724 max.
How come it uses so much of my cpu?

Hi, what terminal command are you using to check the cpu status? From what it looks like, it is the memory being used, not the cpu.

---

### Post by gijs2 on 2014-05-29
> **sandyd said:**
> Hi, what terminal command are you using to check the cpu status? From what it looks like, it is the memory being used, not the cpu.

Yeah i'm sorry that's what i meant the memory.

And i use free -m or top

---

### Post by sandyd on 2014-05-29
Ubuntu (in fact all linux systems) uses the memory for caching to improve performance of the system.

That being said, here is the output of free -m
```

             total       used       free     shared    buffers     cached
Mem:          7838       3419       4418        386        121       1669
-/+ buffers/cache:       1629       6209
Swap:            0          0          0

```

What is relavent here is the line that starts with -/+ buffers/cache

That line shows the actual usage (with the memory used for caching excluded). When the system needs, it will remove the cached ram and use it for programs/etc

Oh, and apparently, it seems I have no swap... :-k

---

### Post by LastDino on 2014-05-29
You can also clear that cache if you feel *exclusive need* to by this command:

```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```

Note: Like sandyd pointed out, there is no real need to get worried over it, so you are in no real need to actually do anything about it.

---

### Post by gijs2 on 2014-05-29
> **sandyd said:**
> Ubuntu (in fact all linux systems) uses the memory for caching to improve performance of the system.

That being said, here is the output of free -m
```

             total       used       free     shared    buffers     cached
Mem:          7838       3419       4418        386        121       1669
-/+ buffers/cache:       1629       6209
Swap:            0          0          0

```

What is relavent here is the line that starts with -/+ buffers/cache

That line shows the actual usage (with the memory used for caching excluded). When the system needs, it will remove the cached ram and use it for programs/etc

Still it's a bit high for not having open that much.

```
             total       used       free     shared    buffers     cachedMem:         
                         3724       2938        786        361         71       1023
-/+ buffers/cache:       1844       1880
Swap:              3864        174       3690



```

---

### Post by fkkroundabout on 2014-05-29
if you had programs open before, then close them, they stay in the RAM in case you open them again [likely]

---

### Post by gijs2 on 2014-05-29
> **fkkroundabout said:**
> if you had programs open before, then close them, they stay in the RAM in case you open them again [likely]

How can i easily see/close programs if they are not on my sidebar?

---

### Post by sandyd on 2014-05-29
A useful tool to see whats using the memory is System Monitor

Just go to the dash, search for "System Monitor"

Click on the "Memory" heading to sort by memory usage.

You can then see what is using the most memory (in this case, FF gobbled up a total of 818M :eek: followed by compiz gobbling up a measly 150M )

---

### Post by gijs2 on 2014-05-29
> **sandyd said:**
> A useful tool to see whats using the memory is System Monitor

Just go to the dash, search for "System Monitor"

Click on the "Memory" heading to sort by memory usage.

You can then see what is using the most memory (in this case, FF gobbled up a total of 818M :eek: followed by compiz gobbling up a measly 150M )

Thanks but the problem now is that i dont know wich procces to end :P

---

### Post by gijs2 on 2014-05-29
Is it normal that Compiz takes up like 170 mb of memory?

---

### Post by LastDino on 2014-05-29
> **gijs2 said:**
> Is it normal that Compiz takes up like 170 mb of memory?

Yes, it can take more too if you've too much of everything enabled.

---

### Post by gijs2 on 2014-05-29
> **LastDino said:**
> Yes, it can take more too if you've too much of everything enabled.

Too much of what? ^^

---

### Post by LastDino on 2014-05-29
> **gijs2 said:**
> Too much of what? ^^

All the Eye-candy compiz can offer. For example, wobbly windows & 3D desktop etc etc.

---

### Post by philinux on 2014-05-29
Title of thread amended.

---

### Post by monkeybrain20122 on 2014-06-02
> **LastDino said:**
> All the Eye-candy compiz can offer. For example, wobbly windows & 3D desktop etc etc.

It is not normal, i have all the eye candies and a bunch of open windows, it uses <30mb (unless with transparent cube then it is possible)

BTW, OP's system is a mess and I doubt that anything is 'normal' there and there is really no point to try to fix anything without a clean re-install first.
[http://ubuntuforums.org/showthread.php?t=2226493](http://ubuntuforums.org/showthread.php?t=2226493)

---

### Post by grahammechanical on 2014-06-02
A computer operating system will use as much RAM as it needs. That is why we have the stuff in the first place. I only have 1GB RAM and 14.04 works fine. Mind you, it uses about 50% of RAM just running this browser. But I do not mind. I would worry if the OS failed to use all the resources (CPU and RAM) when I needed it to use all those resources. From my point of view, you have paid for more RAM than you use.

Regards.

---

