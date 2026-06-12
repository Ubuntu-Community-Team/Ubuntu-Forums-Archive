---
title: "Linux kernel information"
date: 2011-11-07
forum: Programming Talk
---

### Post by erotavlas on 2011-11-07
Hi,

I'm not expert about the kernel and the linux kernel. I would like to know how the kernel manages the threads. In details, how does it distribute the threads among several processor on SMP machine? What are the limits of linux kernel in terms of number of processor that one single process can use? Where can I find information about it?

Thank you

---

### Post by gnometorule on 2011-11-07
This question would need pages to answer. A book on the kernel I like is

Covet/Cesati: understanding the Linux kernel

To give you some ideas though...the core of thread/process distribution is the schedule() function. Each process has a process descriptor structure with many entries. Some will identify its state (running, stopped with interrupts enabled etc), when stopped a flag TIF_NEED_RESCHEDULE (indicating to schedule() "pick me!"), and a wait_queue (for each processor; each process only in one such queue) in which processes currently not running wait to be picked for execution again. Processes get sorted into queues by attached priorities. Their priority depends on a somewhat complex, partly heuristic algorithm which also factors in how long the process has been asleep. I am not aware of any limit imposed, or even imposable, on the number of processor each process could run on - it would make little sense as one process could start on CPU1, sleep, work a bit on CPU2, sleep, and then go to any of the others. By allowing the scheduler() to freely pick among processor with functions such as load_balance(), you achieve workload balancing. There are other limits attached to each process, the only one usually biting related to their jiffies stamp - their time run after having been woken up, which is limited before being put back to sleep so not one process hogs all resources. Other, usually not-biting limits include max RAM and such.

---

