---
title: "Fail to implement system call in Ubuntu distribution."
date: 2009-03-31
forum: Programming Talk
---

### Post by kunsheng on 2009-03-31
Hello everyone,

I am trying to implement a system call in ubuntu:

I installed ubuntu upon VMFusion on Macbook.

'uname -a' return the following results:

2.6.24.1ccustom2 #1 SMP Thu Nov 20 10:43:18 EST 2008 i686 GNU/Linux

I was trying to find syscall_table.S in /usr/src/linux/arch/i386 but only a 'boot' folder is there.

Then I modified something in /usr/src/linux/arch/avr32/syscall_table.S (I found this there), recompile the kernel and reboot, but failed to trigger the system call through user program.


I am pretty sure I didn't modified the correct place but don't know where it is . Couple quesitons on system call on ubuntu could be found online but no concrete answer was posted yet.

I am wondering if anyone did this could give me some idea,



Thanks in advance,

-Kunsheng

---

### Post by slavik on 2009-03-31
did you compile the kernel with your modifications in the code?

---

