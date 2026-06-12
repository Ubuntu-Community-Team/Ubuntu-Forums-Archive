---
title: "Copying files from HDD over network"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by markotitel on 2008-05-17
Hi,

Ill first paste output from DSTAT .

```

-dsk/total- --net/eth0-
 read  writ| recv  send
   0    14M|8283k  265k
   0    23M|8124k  263k
   0     0 |7809k  255k
   0     0 |7546k  247k
   0     0 |8160k  263k
4096B   12M|8061k  260k
  12k   25M|8039k  260k
   0     0 |7823k  253k
4096B   64k|7338k  237k
   0     0 |7871k  255k
   0    11M|8321k  268k
   0    26M|8439k  273k
  32k    0 |7828k  254k
   0     0 |8073k  260k
   0    40k|7965k  259k
   0    64k| 467k   15k
```

Why disk writes are not at constant speed of network transfer speed, but every ~35MB is written and then nothing. I dont think it is bad beahaviour just asking to learn more :) .

---

### Post by lemming465 on 2008-05-17
Typically linux kernels will buffer stuff for a while in memory, in hopes of merging adjacent writes and avoiding extraneous seeks.  About every 30 seconds pending dirty blocks get flushed to disk by one of the kernel threads.  However, programs can specify if they want immediate I/O (e.g. fsync()), and the flush interval can be adjusted by writing (echo) a different value into /proc/sys/vm/dirty_write_centiseconds.

---

### Post by markotitel on 2008-05-19
ah thx :)

---

