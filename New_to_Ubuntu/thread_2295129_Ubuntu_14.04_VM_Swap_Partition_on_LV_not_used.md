---
title: "Ubuntu 14.04 VM Swap Partition on LV not used?"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by Jon_Talbot-Jones on 2015-09-16
Hi,

I am trying to verify whether a swap partition on a logical volume is really being used.

I have set swapiness to 100 and have obtained the following:-

Top:

KiB Mem:  16430980 total, 15686060 used,   744920 free,  1828928 buffersKiB Swap:  2093052 total,        0 used,  2093052 free.  9334704 cached Mem

swapon -s:

Filename                                Type            Size    Used    Priority
/dev/mapper/EJ--TEMPLATE--02--vg-swap_1 partition       2093052 0       -1

free:
             total       used       free     shared    buffers     cached
Mem:      16430980   15733524     697456      80360    1844604    9344744
-/+ buffers/cache:    4544176   11886804
Swap:      2093052          0    2093052

dmeg:

[   21.083622] Adding 2093052k swap on /dev/mapper/EJ--TEMPLATE--02--vg-swap_1.  Priority:-1 extents:1 across:2093052k FS

meminfo:
SwapTotal:       2093052 kB
SwapFree:        2093052 kB


/proc/swaps/

Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       2093052 0       -1



I am concerned /proc/swaps points to dm-1 and not the logical volume.

Thanks in advance.

---

