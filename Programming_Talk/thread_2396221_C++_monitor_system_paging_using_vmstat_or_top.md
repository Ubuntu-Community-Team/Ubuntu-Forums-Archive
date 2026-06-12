---
title: "C++ monitor system paging using vmstat or top"
date: 2018-07-12
forum: Programming Talk
---

### Post by softengstu115 on 2018-07-12
Hi all, I'm new to Linux but have some experience with C++ and I'm stuck on this problem.

 I'm trying to write a simple C++ program that will monitor the system page in and page outs in real time and alert the user if/when a process reaches a set threshold. How can I get the values from page in and page out columns (in vmstat output) for each process and for each row compare the values to the threshold (set by the user)? I feel like this should be as simple as running a for loop where I get the value of the page out column from a system command for each process and compare it, then move on to the next process. But, how would I isolate the value in page out column so I can just compare that value? Also, how would I make sure each iteration of the loop only reads one process from the vmstat output?

Thank you

---

### Post by steeldriver on 2018-07-12
I'm not a fan of shelling out from C programs for this kind of thing - wouldn't it me better to examine how vmstat gets this information and writing the equivalent functionality directly?

FWIW I suspect it just reads /proc/vmstat

```

$ strace -e trace=open vmstat 1 1 2>&1 | grep '/proc/'
open("/proc/filesystems", O_RDONLY)     = 3
open("/proc/meminfo", O_RDONLY)         = 3
open("/proc/stat", O_RDONLY)            = 4
open("/proc/vmstat", O_RDONLY)          = 5

```

---

### Post by softengstu115 on 2018-07-12
It seems more efficient to get this information from /proc/vmstat or /proc/meminfo, but I'm supposed to use the vmstat or top commands. Perhaps it would be best to just write a shell script instead of a C program or is there a simple way to write this as a C program using the vmstat command?

---

