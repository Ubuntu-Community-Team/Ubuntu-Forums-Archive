---
title: "Question about  Kernel Threads"
date: 2008-06-28
forum: Programming Talk
---

### Post by eldoctor on 2008-06-28
Hi everyone!

I have a doubt about Kernel threads, I have been searching but I could not come up with I clean answer on this one:
Do two Kernel Threads share the PCB (Proccess Control Block)?

Thanks in advance
Diego

---

### Post by angustia on 2008-06-28
i'm not sure completely, but in linux there are practically only threads.

each thread have a TCB (PCB for threads), and in those tcb there are entries that maps virtual to physical memory addresses. 

All threads belonging to one process share the same memory mappings, that's all. Processes are threads whose TCBs maps to diffrent physical addresses, or even same physical addresses (but mapped to diffrent virtual addresses).

well, threads share other resources too like file descriptors, file system view, etc. Take a look at [man clone]("http://linux.die.net/man/2/clone")

excuse my english

---

### Post by slavik on 2008-06-28
Linux doesn't have threads or processes, it has tasks. :P

---

### Post by eldoctor on 2008-06-28
The problem is that I need to answer this question for my Operating Systems profesor and I cant manage to get the right answer, I am very confused.
I read in my text books that tasks or proccess/thread is the same in Linux but still I need to know if Kernel Threads (threads that do not block the entire father proccess when they block) share the same PCB between them, supossing one proccess has more than one Kernel thread (besides the TCB)

---

### Post by slavik on 2008-06-28
kernel threads are scheduled separately.

---

### Post by angustia on 2008-06-28
> **eldoctor said:**
> The problem is that I need to answer this question for my Operating Systems profesor and I cant manage to get the right answer, I am very confused.
I read in my text books that tasks or proccess/thread is the same in Linux but still I need to know if Kernel Threads (threads that do not block the entire father proccess when they block) share the same PCB between them, supossing one proccess has more than one Kernel thread (besides the TCB)

well... yes

at least, all threads share  the same PID, so this info has to be in a common structure, that is the PCB (the same for other common data).

the point is that the "PCB" in linux is diffrent to other unixes.

(excuse my english)

---

