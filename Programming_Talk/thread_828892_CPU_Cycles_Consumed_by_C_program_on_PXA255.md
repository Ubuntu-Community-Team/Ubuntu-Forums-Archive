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

### Post by NathanB on 2008-06-14
Because Linux is multi-tasking, you will want *only* your process's time and ignore the rest.  Thankfully, the Linux API contains useful functions to this end.  IBM has an enlightening introduction to the SysCall interface here:

[http://www.ibm.com/developerworks/linux/library/l-system-calls/](http://www.ibm.com/developerworks/linux/library/l-system-calls/)

Reference material can be found here:

[http://linux.about.com/od/commands/l/blcmdl_2a.htm](http://linux.about.com/od/commands/l/blcmdl_2a.htm)
[http://linux.die.net/man/2/syscalls](http://linux.die.net/man/2/syscalls)

You will want the 'tms_utime' member of the structure which is filled by the 'times(2)' syscall.

[http://linux.die.net/man/2/times](http://linux.die.net/man/2/times)
[http://linux.about.com/library/cmd/blcmdl2_times.htm](http://linux.about.com/library/cmd/blcmdl2_times.htm)

Nathan.

---

### Post by junaidfcs on 2008-06-15
Thanks for your reply.

First of all I need to know exact CPU clocks not execution time. The second thing is I want to run it on ARM (PXA255) not on x86. Currently, I can get the CPU cycles used by my program using RTDSC assembly command available on x86 architecture. I am looking for something equivalent to it for ARM. 

I have come to know about clock() of time.h for this purpose. But problem with clock() is that it uses an internal CLOCKS_PER_SEC constant that is fixed to 1M not to frequency of machines CPU clock. Also I read about it it is not very precise.

I hope it will be more clear to you what I actually aims to achieve.

Thanks
Junaid

---

### Post by NathanB on 2008-06-15
> **junaidfcs said:**
> First of all I need to know exact CPU clocks not execution time.

CPU clocks are meaningless on a pre-emptively multi-tasking operating system like Linux.

> The second thing is I want to run it on ARM (PXA255) not on x86.

For portability reasons, the Linux API is virtually the same on all architectures.  Likewise, the standard C library contains the same functionality across a variety of hardware.  You should take a look at the 'gettimeofday' function:

[http://rabbit.eng.miami.edu/info/functions/time.html](http://rabbit.eng.miami.edu/info/functions/time.html)

> Currently, I can get the CPU cycles used by my program using RTDSC assembly command available on x86 architecture. I am looking for something equivalent to it for ARM.

References *are* freely available for you to use:

[http://www.arm.com/documentation/Instruction_Set/](http://www.arm.com/documentation/Instruction_Set/)

Nathan.

---

### Post by 23meg on 2008-06-19
Moved to Programming Talk.

---

