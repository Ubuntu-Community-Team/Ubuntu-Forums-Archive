---
title: "Read from/write to physical memory from user space"
date: 2011-12-14
forum: Programming Talk
---

### Post by niom on 2011-12-14
I'm currently developing on a Beagle board (OMAP3) and I have a problem. I need to read an write data/code to the DSPs internal memory from user space.

I have been able to read/write code/data to SDRAM and read from/write to registers by doing mmap with /dev/mem as file descriptor, but as soon as I try to write to the DSPs internal memory I see a kernel crash, even though the mapping was successful.

I suspect that the internal memory area is not included in /dev/mem's memory range somehow. So an idea I had  was to use ioctl to extend the memory range of /dev/mem, but I hit a wall there as well, because I can't figure out what kind of request I should sent as an argument. Is this even possible? Or is there an easier way?

I'm quite new to Linux and have very limited knowledge of it, any ideas, anyone?

---

### Post by jwbrase on 2011-12-14
The default kernel for Ubuntu only maps the first MB (I think) of physical memory into /dev/mem. Certain userspace system programs like X need access to the first MB, but the general view is that for most users, extending /dev/mem beyond the 1MB mark just creates potential security issues for little or no benefit. If you need further access to /dev/mem, you have to compile a custom kernel with the "Kernel Hacking ---> Filter access to /dev/mem" option (STRICT_DEVMEM) turned off.

---

### Post by niom on 2011-12-15
Ok, thanks for your reply. Currently I don't have the sources for the kerenel I'm using, I also suspected that some changes needed to be done there. But for a quick solution, just so I can continue developing, it is possible to extend the memory range for /dev/mem from userspace? Then how?

---

