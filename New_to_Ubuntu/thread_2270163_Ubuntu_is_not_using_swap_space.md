---
title: "Ubuntu is not using swap space"
date: 2015-03-20
forum: New to Ubuntu
---

### Post by Novitk on 2015-03-20
Instead of using a swap partition, I've always used a swap file (Debian, OpenSUSE, Slackware, Ubuntu) and I've never had problems. But I've just installed Ubuntu 14.04 LTS, I created a swap file as usual ([using this procedure]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/")), and it seems Ubuntu is not using my swap space available:

```
free -m             total       used       free     shared    buffers     cached
Mem:          7882       7722        159        321        748       2178
-/+ buffers/cache:       4795       3086
Swap:        10239          0      10239
```

This is my /etc/fstab in the part concerning my swap file:
```

/root/swapfile none swap sw 0 0

```

It's currently almost out of memory, but not a single byte of the swap space is being used. The system is slow and it feels clumsy to use. What's wrong? Why isnt' Ubuntu using the swap space availabe and how do I fix it?

---

### Post by nerdtron on 2015-03-20
Not using swap is a good thing since swap is way slower than RAM.
And your computer is not running low on memory. The second line show the real memory usage and the first line show memory usage with cache.

I think you should "load" you computer more, maybe open more programs, open firefox with 20 tabs and leave for half a day and you're sure to use some swap space.

---

### Post by buzzingrobot on 2015-03-21
Swap is used when something makes a memory allocation request that cannot be met from free, unallocated, RAM.  In that case, a chunk of allocated RAM is written to swap.

I've never used a swap *file*, but, perhaps, your system seems slow because using a file for swap *is* slower than using a partition.

---

### Post by grahammechanical on 2015-03-21
You have as twice as much cache memory as i have RAM and it seems that I am getting a better user experience than you. Could the problem be the video driver?

An OS will take as much memory as is available. And that is as it should be. The important part is the way it uses memory. What we see as "used" memory is actually memory claimed by the OS for allocation for any task that the user instructs the OS to do. I think that we will find that "used" memory also includes "cached" memory. Add "used" to "cache" and the sum is greater than "total."  

Regards.

---

### Post by buzzingrobot on 2015-03-21
If you open a terminal, leave it open,  and run ```
vmstat 3 100
``` you'll see something like this: 
```
vmstat 3 100
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 29593708  68932 1064880    0    0    72    65   52  193  1  0 98  1  0
 0  0      0 29593192  68932 1064896    0    0     0     0   93  148  0  0 100  0  0
 0  1      0 29598064  68940 1060016    0    0     0    29  103  127  0  0 100  0  0

```

This displays a running look at how swap is being used.  The 'so' column shows the amount of memory written out to swap and the 'si' column shows the amount being read into memory from swap. (Both zero here; the columns are a bit askew.) 

Dunno if this works when a swap file is used rather than the expected partition.

---

### Post by Novitk on 2015-03-22
Swap is not being used and I think it's I misunderstood the output. I had indeed a lot of free memory. I was with VirtualBox running Windows XP and I thought the problem was a lack of memory, but I guess I was wrong. My swap file is not being used and it probably shouldn't be used anyway, since I have so much free memory. Thanks to clarify things for me, guys!

---

