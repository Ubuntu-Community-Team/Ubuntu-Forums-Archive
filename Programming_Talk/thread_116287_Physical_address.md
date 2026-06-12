---
title: "Physical address"
date: 2006-01-12
forum: Programming Talk
---

### Post by Mordred on 2006-01-12
Hi

I'm building an embedded system running linux on a powerpc.
This system uses a coprocessor. For this I need to retrieve
the physical address of the data I stored in the RAM.

Is this possible and where do I find information about it?

Thanks

---

### Post by LordHunter317 on 2006-01-12
I don't know if it's possible on PPC, it's possible in Linux if you're root.

Otherwise, you have to be in the kernel.

---

### Post by Mordred on 2006-01-12
I am root so that's no problem, 
How can I use this in a C++ program?

---

### Post by LordHunter317 on 2006-01-12
Err, I misspoke. It's possible on IA-32 on Linux, if you're root.

I'm pretty sure you're going to have be in the kernel.

---

### Post by Mordred on 2006-01-12
I haven't done anything like that before,
where can I find information about it?

---

### Post by coredump on 2006-01-13
Maybe you could try the Kernel Newbies:

[http://www.kernelnewbies.org/]("http://www.kernelnewbies.org/")

Or perhaps the two O'Reilly books would help: Linux Device Drivers and Understanding the Linux Kernel (both now 3rd edition).

---

