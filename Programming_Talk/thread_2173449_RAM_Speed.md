---
title: "RAM Speed"
date: 2013-09-09
forum: Programming Talk
---

### Post by skyglow on 2013-09-09
I tried to make a (really simple) ram speed benchmark code in C.
I noticed that the speed calculated by my code differs from the one of tmpfs and the one in memtest.
The difference between the 3 is really huge,

The system is a Phenom X4 9950 with 4GB DDR2 800Mhz (2x2GB) running on Ubuntu 12.04.3 (updated so kernel 3.8.0-30-generic)

to check tmpfs write speed i used:
dd if=/dev/zero of=test count=2048 bs=1M

memtest speed is just the speed of ram displayed

my program is just a malloc of 2gb and 10 times a sequential write with blocks of 16k of zeros ( i tryed out 1k , 2k, 4k, 8k too but i have no idea why this size is the one that gives the best performance)

I tested ganged and unganged mode for all three benchmarks
Unganged mode is  the fasest
memtest: 3099MB/S
dd: 1.5GB/S
mycode: 1157.06 MB/s

Ganged mode
memtest: 3023MB/S
dd: 1.4GB/S
mycode: 1164.63 MB/s

There are nearly no performance differences between the two modes. I checked multiple times and i always had these values.
I expect to be some overhead on tmpfs related to my benchmark but it's actually faster.
I expected memtest to be faster than the other 2 benchmarks but not over the double of their speed. 

I was now wondering if someone could explain my results, because i have the feeling they show some interesting feature of linux/Ubuntu architecture.

---

### Post by lukeiamyourfather on 2013-09-11
Even though tmpfs is in memory it still has the performance overhead of a filesystem which will reduce the bandwidth compared to directly accessing the memory.

---

### Post by tgalati4 on 2013-09-11
Try some benchmarks in *phoronix-test-suite*.  I like to use memtest to tweak CAS timing and bus speed when building a machine, but phoronix for real performance in use.  Sometimes the tests that you create just for RAM will create unusual workloads for the CPU that get optimized in different ways, so you get unexpected results.  Try doing some real-world benchmarks to determine goodness.

---

### Post by skyglow on 2013-09-11
They even behave strange with concurrency.

> t1 = clock();
fork();
fork();
fork();
for(j =0; j < 10; j++){
	for (i = 0; i < count; i++, ramposition+=ramblock){
	  memcpy(&(ram[i]), block, ramblock);
	}
}
t2 = clock();


At the end it display 8 results all over 1180MB/s
It looks like every process can use almost the same speed.
It starts to lower with 4xfork() to 1170MB/s.
Maybe i explained myself wrong in the first post. I'm more interested on the reason i get these results than how good they are.
I'm wondering why i obtain these values to produce better code on useful programs.

---

### Post by ofnuts on 2013-09-12
Given that there are three levels of memory cache in modern processors, with processor-wide ones and core-specific ones, I wonder how you can expect to get meaningful measurements...

---

### Post by skyglow on 2013-09-12
I don't expect them to be right. I just don't expect them to be totally off. I forced the ram variable to be allocated outside caching with _mm_prefetch(). That variable size i used for tests was always 2GB so the wrong value was off of around 0.293% theorically.
Is there a function i can use to give me higher access speed to the ram, let's say the same kernel has?
And is the so much higher value given by memtest all due to only 1 process running in realtime mode?

---

### Post by MadCow108 on 2013-09-13
_mm_prefetch will explicitly pull an adress range into the cache, _mm_stream will bypass caches.
also note that memcpy needs cpu cycles, depending on the implementation single threaded copying can be slower than the memory bandwidth.
memory speed is dependent on many factors. e.g. you must also consider page faults (so using hugepages or prefaulting might improve the bandwidth)

---

### Post by skyglow on 2013-09-13
thanks for these answers.
Maybe i have some concept wrong.
If i want to access ram directly without caching it, why should i have page faults?

---

