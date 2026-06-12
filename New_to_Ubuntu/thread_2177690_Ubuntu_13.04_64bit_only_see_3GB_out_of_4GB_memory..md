---
title: "Ubuntu 13.04 64bit only see 3GB out of 4GB memory."
date: 2013-09-29
forum: New to Ubuntu
---

### Post by dusty254 on 2013-09-29
output of uname -a
   ```
Linux linux 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
  output free -m

               ```
             total       used       free     shared    buffers     cached
Mem:          3088        944       2143          0         29        398
-/+ buffers/cache:        516       2571
Swap:         3280          0       3280
```

  Taken from hardinfo:

      ```
-Memory-
    Total Memory        : 3162692 kB
    Free Memory     : 2171192 kB
    Buffers     : 31496 kB
    Cached      : 426468 kB
    Cached Swap     : 0 kB
    Active      : 447472 kB
    Inactive        : 309820 kB
    Active(anon)        : 300092 kB
    Inactive(anon)      : 1100 kB
    Active(file)        : 147380 kB
    Inactive(file)      : 308720 kB
    Unevictable     : 0 kB
    Mlocked     : 0 kB
    Virtual Memory      : 3359740 kB
    Free Virtual Memory     : 3359740 kB
    Dirty       : 52 kB
    Writeback       : 144 kB
    AnonPages       : 299324 kB
    Mapped      : 161220 kB
    Shmem       : 1868 kB
    Slab        : 38996 kB
    SReclaimable        : 18784 kB
    SUnreclaim      : 20212 kB
    KernelStack     : 2656 kB
    PageTables      : 14680 kB
    NFS_Unstable        : 0 kB
    Bounce      : 0 kB
    WritebackTmp        : 0 kB
    CommitLimit     : 4941084 kB
    Committed_AS        : 1579588 kB
    VmallocTotal        : 34359738367 kB
    VmallocUsed     : 302256 kB
    VmallocChunk        : 34359433468 kB
    HardwareCorrupted       : 0 kB
    AnonHugePages       : 0 kB
    HugePages_Total     : 0
    HugePages_Free      : 0
    HugePages_Rsvd      : 0
    HugePages_Surp      : 0
    Hugepagesize        : 2048 kB
    DirectMap4k     : 98300 kB
    DirectMap2M     : 2236416 kB
    DirectMap1G     : 1048576 kB
```
lspci output for the intergrated GPU on my CPU
 
    ```
Subsystem: Micro-Star International Co., Ltd. Device 7721
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at fef00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
```
 
 
The CPU is an AMD A8-5600K. 
My mother board is a MSI fm2-a55m-e33 which can use up to 16GB of memory. Windows 7 64bit and my BIOS both show 4GB of memory.

---

### Post by UltimateCat on 2013-09-29
> My mother board is a MSI fm2-a55m-e33 which can use up to 16GB of memory. 


How many sticks of RAM did you install on your mobo?


When I installed Black Opal which is built on Ubuntu 12.04 I allocated 20 GB for the /journaling file system but when I view those partitions it shows as 18 GB's.
Not sure what this discrepancy is about.

Maybe another member will know more.

---

### Post by dusty254 on 2013-09-29
I currently have 2 ram modules.

---

### Post by DuckHook on 2013-09-29
Windows and Linux report RAM in different ways. I know nothing about your particular APU/MB combo, but does it reserve 1GB as VRAM for graphics? If so, on older MBs, this will be permanently carved out of your DRAM pool (it has to come from somewhere). On newer systems, I believe that VRAM allocation is dynamic and will change depending on graphics needs, but I'm not sure how the system would report DRAM in such cases. Your system documentation should tell you, or a Google query of your CPU/MB combo could as well. Your BIOS may even allow you to define how much VRAM you want allocated.

---

### Post by sanderj on 2013-09-30
Run this script, and it will tell you all:

```
wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
sudo python check-my-memory.py
```

---

### Post by mastablasta on 2013-09-30
> AMD A8-5600K

that's an APU. does the GPU chip on it perhaps take 1GB of RAM?

i have 2GB ram on notebook, yet Kubuntu is showing 1,5 GB. 512MB is taken by GPU part of APU.

---

### Post by su:bhatta on 2013-09-30
I have AMD A4 APU and it reserves 512 MB for Graphics, perhaps your A8 is reserving 1GB for graphics. 

Use Duckhook & Sanderj's ways to check out if the APU is reserving 1GB for Graphics.

---

### Post by dusty254 on 2013-09-30
> **sanderj said:**
> Run this script, and it will tell you all:

```
wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
sudo python check-my-memory.py
```



Here is what I got:

```
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3279 MB as usable
Memory seen by OS 3088 MB
BIOS version 05/02/2013
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 817 MB
Memory difference between BIOS offering and memory seen by OS 191 MB
Memory difference between DIMM hardware and memory seen by OS 1008 MB

ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: SODIMM DDR3 [empty]
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          size: 2GiB
          description: SODIMM DDR3 [empty]
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          size: 2GiB

Finished
```


I don't really understand in my BIOS it shows 4GIG being available and there isn't an optiton for 'memory hole remapping / hoisting'.

---

### Post by DuckHook on 2013-09-30
There may be nothing at all wrong with your system and 1GB has just been set aside for video memory. You must check out how much DRAM your APU reserves for VRAM before making any changes willy-nilly to your computer. Otherwise, you may risk destabilizing a perfectly normal system for the wrong reasons. Please check out previous posts from *mastablasta*, *bhattabhishek* and me, all of which point to the same conclusion.

The script you ran cannot tell you how much DRAM has been set aside for VRAM. BTW, on a separate note, did you review the python script before running it? Especially as root? Not to cast any aspersions on *sanderj* (who I'm sure is a fine fellow) but it is risky to just run any script you download unless you understand exactly what it will do.

---

### Post by dusty254 on 2013-09-30
> **DuckHook said:**
> Snip


I ran 

```
grep -i --color memory /var/log/Xorg.0.log
```

When looking through I found

```
[    23.018] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    23.018] (--) fglrx(0): Video RAM: 786432 kByte, Type: DDR3 
```

The system sees 3088MB of ram and 786MB is being used for the GPU. 3088 + 786 = 3874MB, there is suppose to be 4096MB. I don't know if the 786MB is taken out of the 3088MB or out of 3874MB. But I do know two things, it is still less than 4GB and that the GPU shares system memory since it doesn't have much of its own. Is there a command to see how much memory the kernel is keeping locked away?

---

### Post by DuckHook on 2013-09-30
Good detective work! The VRAM definitely comes out before the DRAM is reported because commands like *free* will only report what memory can actually be used. In short, you have accounted for 3874MB of your installed RAM. I'm not sure where the remaining 222MB went as I am not an expert on system or memory architecture. Hopefully, some guru reading this thread can enlighten us. However, you can take at least some comfort in knowing that you are trying to account for 5% of your installed RAM rather than 25%.

You may be able to get a finer picture of memory allocation with:```
dmesg | grep -i memory
```and```
grep -i memory /var/log/syslog
```

---

### Post by dusty254 on 2013-09-30
I can't make heads or tails of this one.

```
dmesg | grep -i memory
```
```

[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x8f7fffff]
[    0.000000] init_memory_mapping: [mem 0x100001000-0x13effffff]
[    0.000000] Early memory node ranges
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000008db29000 - 000000008db59000
[    0.000000] PM: Registered nosave memory: 000000008de19000 - 000000008deb8000
[    0.000000] PM: Registered nosave memory: 000000008deb8000 - 000000008ea28000
[    0.000000] PM: Registered nosave memory: 000000008ea29000 - 000000008ec2f000
[    0.000000] PM: Registered nosave memory: 000000008f072000 - 000000008f7f3000
[    0.000000] PM: Registered nosave memory: 000000008f800000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed40000
[    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fed45000
[    0.000000] PM: Registered nosave memory: 00000000fed45000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] PM: Registered nosave memory: 0000000078000000 - 000000007c000000
[    0.000000] Memory: 2938676k/5226496k available (7014k kernel code, 1865948k absent, 421872k reserved, 6228k data, 996k init)
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.003203] Initializing cgroup subsys memory
[    0.894749] Freeing initrd memory: 15840k freed
[    1.256260] Freeing unused kernel memory: 996k freed
[    1.261076] Freeing unused kernel memory: 1168k freed
[    1.265350] Freeing unused kernel memory: 1076k freed
[   11.578657] <6>[fglrx] Maximum main memory to use for locked dma buffers: 2941 MBytes.
```

And I noticed these two, its the first time I saw the second line.

```
grep -i memory /var/log/syslog
```

```
Sep 30 10:40:41 linux kernel: [   10.179107] [drm] radeon: 768M of VRAM memory ready
Sep 30 10:40:41 linux kernel: [   10.179108] [drm] radeon: 512M of GTT memory ready.

```

---

### Post by su:bhatta on 2013-09-30
I guess your issue is solved then. Good you got your clarifications.

Please go to the 'Thread Tools' and mark the thread as 'Solved'.

---

### Post by UltimateCat on 2013-10-01
Are they 8 gig's each?  (or) 4?

---

