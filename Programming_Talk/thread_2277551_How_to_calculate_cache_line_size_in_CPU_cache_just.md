---
title: "How to calculate cache line size in CPU cache just using the total cache size and set"
date: 2015-05-09
forum: Programming Talk
---

### Post by pavelexpertov on 2015-05-09
Hello, I was looking through processor specifications and I could not find a cache line size (for CPU, not RAM) that's being used in cache. However, I have managed to obtain a total size of a cache and a type of set-associative design.
Is it possible to use two details to calculate the cache line size.

---

### Post by xb12x2 on 2015-05-12
First let me say that I'm not an expert in processor design. 

For common commercial processors I don't think the cacheline size can be calculated based on the information you have. 

As I understand it, the cacheline size is arbitrarily set. A very simple explanation is: The larger the size the more likey to have more cache hits (locality) but the longer it takes to fill from memory. So the compromise is between more cache hits (good) versus more time to fill (bad). 

However, if the processor in which you' are interested is running on Linux or Windows you should be able to get the cacheline size.

Linux makes available a lot of information for you.
Depending on your particular hardware and kernel version you should be able to find a file such as 
"/sys/devices/system/cpu/cpu0/cache/index0/coherency_line_size".

Example from my machine: 
$ cat /sys/devices/system/cpu/cpu0/cache/index0/coherency_line_size
64


Windows 7: 
The function GetLogicalProcessorInformationEx() returns a buffer. You have to dig down in that buffer to find the cacheline size. 
    buffer
           -- structure SYSTEM_LOGICAL_PROCESSOR_INFORMATION_EX
                  ---- structure CACHE_RELATIONSHIP
                          ------ word LineSize


-

---

### Post by pavelexpertov on 2015-05-15
Hi, cheers for a reply, I have to remind myself that UNIX has all files for everything. Furthermore, I already figured out that I can't calculate the line sizes from the info, but I misread the section in a spec.
Thanks anyway.

---

