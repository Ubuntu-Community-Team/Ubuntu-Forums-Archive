---
title: "how to check for how much memory on system c/c++"
date: 2009-07-10
forum: Programming Talk
---

### Post by monkeyking on 2009-07-10
Hi, is there a system independent way of getting the amount of memory on a system using c/c++?

thanks

---

### Post by dwhitney67 on 2009-07-10
You can use sysconf() on both Linux and Unix systems.  I doubt it will work under an M$ OS.

The API is sysconf(name), where the 'name' I believe you would need are _SC_PHYS_PAGES to get the number of pages of physical memory, and then _SC_AVPHYS_PAGES to get the number of pages of physical memory currently available.

Then a ratio of available memory can be computed...
```

double percentAvail = double(totalPages - freePages) / double(totalPages) * 100.0;
```

For Linux, you can also read/parse /proc/meminfo, but sysconf() seems a bit easier.  Merely my opinion.


P.S.  My 3000th post!  :-)

---

### Post by Mirge on 2009-07-10
> **dwhitney67 said:**
> You can use sysconf() on both Linux and Unix systems.  I doubt it will work under an M$ OS.

The API is sysconf(name), where the 'name' I believe you would need are _SC_PHYS_PAGES to get the number of pages of physical memory, and then _SC_AVPHYS_PAGES to get the number of pages of physical memory currently available.

Then a ratio of available memory can be computed...
```

double percentAvail = double(totalPages - freePages) / double(totalPages) * 100.0;
```For Linux, you can also read/parse /proc/meminfo, but sysconf() seems a bit easier.  Merely my opinion.


** P.S.  My 3000th post!**  :-)

Post hoar! :lolflag:

---

### Post by monkeyking on 2009-07-10
> **dwhitney67 said:**
> You can use sysconf() on both Linux and Unix systems.  I doubt it will work under an M$ OS.

The API is sysconf(name), where the 'name' I believe you would need are _SC_PHYS_PAGES to get the number of pages of physical memory, and then _SC_AVPHYS_PAGES to get the number of pages of physical memory currently available.

Then a ratio of available memory can be computed...
```

double percentAvail = double(totalPages - freePages) / double(totalPages) * 100.0;
```

For Linux, you can also read/parse /proc/meminfo, but sysconf() seems a bit easier.  Merely my opinion.


P.S.  My 3000th post!  :-)

CONGRATS dwhitney!

I think atleast 100 of these posts must be related to you helping me.
Thanks for you help and advices.

---

### Post by dwhitney67 on 2009-07-10
> **monkeyking said:**
> CONGRATS dwhitney!

I think atleast 100 of these posts must be related to you helping me.
Thanks for you help and advices.

You're welcome.  By the way, my posts aren't always spot on; I meant to indicate that I was computing the percent of used memory, not the available.  #-o

Now that my post has been quoted, I can't change my error.

---

### Post by supirman on 2009-07-10
On linux systems, you can try sysinfo(2).

A quick example to find total RAM:
[PHP]#include <stdio.h>
#include <sys/sysinfo.h>

int main(void)
{
  struct sysinfo myinfo;
  unsigned long total_bytes;

  sysinfo(&myinfo);

  total_bytes = myinfo.mem_unit * myinfo.totalram;


  printf("total usable main memory is %lu B, %lu MB\n",
         total_bytes, total_bytes/1024/1024);

  return 0;

}
[/PHP]

See *man sysinfo* for the rest of the items provided by sysinfo (items such as used ram, # processes, swap size, etc).

---

