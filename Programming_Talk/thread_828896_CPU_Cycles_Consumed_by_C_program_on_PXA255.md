---
title: "CPU Cycles Consumed by C program on PXA255"
date: 2008-06-14
forum: Programming Talk
---

### Post by junaidfcs on 2008-06-14
Hi,
I have run my C program on a board which have Intel PXA255 ARM processor. Now I want to know how much CPU cycles it consumed during its execution. So I think I can do this by capturing the CPU clocks at start of my program and capture again at the end of my program. The difference in the cpu clocks is the total CPU cycles consumed by my program. But how can I do this using some C or inline (ARM)assembly code?

I seen some of members are discussing this on this forum that they count the CPU cycles consumed by C programs. But I want you to help me writing this code. I do not have much idea about ARM Assembly but can understand easily as I worked in Assembly for x86.

By the way, I am using arm-linux-gcc 3.3.2 toolchain to build executables that I run on my board.

Thanks
Junaid

---

