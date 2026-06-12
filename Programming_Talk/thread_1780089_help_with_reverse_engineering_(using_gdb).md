---
title: "help with reverse engineering (using gdb)"
date: 2011-06-11
forum: Programming Talk
---

### Post by boast on 2011-06-11
My goal is to set a breakpoint where a string is accessed in memory.

I did ```
strings -ao -t x bin_file
``` and I found the string I was looking for, and it was at (I assume it is a relative address offset) 0x2ae59.

But when I run the application in gdb, the addresses seem to be direct, like 0x7fff84fcd2a4. 

How do I go about setting an awatch for that ASCII string? I could not find how to search for strings within gdb. 

thanks.

---

### Post by BkkBonanza on 2011-06-11
This may help.
[http://www.linuxsa.org.au/meetings/reveng-0.2.pdf](http://www.linuxsa.org.au/meetings/reveng-0.2.pdf)

You can find details of where segments load with cat /proc/<pid>/maps

I don't know enough about this to say much more.

---

