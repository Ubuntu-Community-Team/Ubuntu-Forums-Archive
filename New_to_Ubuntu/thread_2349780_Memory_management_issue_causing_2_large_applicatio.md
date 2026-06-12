---
title: "Memory management issue causing 2 large applications for go unresponsive"
date: 2017-01-18
forum: New to Ubuntu
---

### Post by Datamac on 2017-01-18
After setting up a new installation on Ubuntu 16.10 on my Acer Aspire 5335 laptop in a dual boot configuration between Win7 (both OS's in separate 400 gb partitions) I am experiencing 2 applications that do not always run correctly.  As a matter of fact, there has only been once instance where the machine was performing perfectly and both applications were open at the same time along with a few other applications.  

The 2 applications that are not performing as expected are Firefox's latest version and Bible Analyzer 5.0  --  I am wondering if there is a specific tweak configuration element that I have to make or is the problem just a matter of adjusting memory usage or swap file size?  

The following is a listing of the machine hardware specs (the system board is new, the memory is new and the hard drive is new though the machine was first released and sold in 2009:   

```

Kernel version: 4.8.0-34-generic
MemTotal:        3007776 kB
free -m
              total        used        free      shared  buff/cache   available
Mem:           2937        1736          93         275        1106         746
Swap:         19071          10       19061

cat /sys/block/sda/size
3907029168
dmesg | grep blocks
[    2.520082] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    2.520084] sd 0:0:0:0: [sda] 4096-byte physical blocks

description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2937MiB
     *-cpu
          product: Genuine Intel(R) CPU             585  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
```

---

### Post by Impavidus on 2017-01-18
3GiB memory is not huge, but should be sufficient. When you ran **free -m**, you still had 746MiB memory available, but maybe that was not just before things turned unresponsive.

Programs can turn unresponsive when the system decides to use swap. You have a lot of swap space (19GiB), but when you ran free it was practically unused. Firefox, like all (graphical) web browsers, consumes a ridiculous amount of memory. Don't open too many tabs simultaneously, I usually stick to 3-6 tabs. I don't know about Bible Analyzer, never installed it.

Try monitoring your system for a while with top:```
top -o %MEM
```This will show the running processes ordered by current memory usage as a percentage of available memory.

If necessary, you can decide to switch to a lighter desktop environment.

---

### Post by Datamac on 2017-01-18
Okay, sounds like a good idea to start trouble-shooting with Thanks.

---

### Post by Datamac on 2017-01-18
Also, ,I was opening 20 tabs on Firefox.  I had been for years on other instances and versions of Ubuntu and Firefox.  I thought Firefox was having problems when I was at the 15 tab opening level with 2 tabs being 2 different sections for the L.A. Times.  LATimes seem to have memory intensive scripts running that when eliminated allowed Firefox to function.

---

