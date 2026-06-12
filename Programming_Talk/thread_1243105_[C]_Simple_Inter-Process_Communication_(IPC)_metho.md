---
title: "[C] Simple Inter-Process Communication (IPC) method?"
date: 2009-08-17
forum: Programming Talk
---

### Post by OutOfReach on 2009-08-17
Hey guys,
I want two or more processes to share data with eachother, but they need to be in sync with eachother. So all the processes need to have the same data.
All the work will be handled by a shared library that will do all the syncing.

I've created a small diagram (attached) to demonstrate my situation (excuse my horrible drawing :) ).

I've looked at pipes, FIFO's and nothing really seemed to solve my problem, since pipes are only 2 way and FIFO's can't have multiple reader/writers.

System V Message Queue's caught my attention...for a moment. The problem was that multiple readers cause for alternate reading, they would not get the same data.

Do you guys have any suggestions?

---

### Post by PmDematagoda on 2009-08-18
Did you have a look at shared memory and condition variables/read-write locks? They seem to fit your use case.

---

### Post by soltanis on 2009-08-18
Shared memory with semaphores seems to be the solution to the problem you are describing, like the above poster said. Look into the mmap (2) function for mapping shared memory; remember that you have to synchronize the memory between co-operating processes in order for them to "see" what's going on.

FIFOs/named pipes aren't really the solution to your problem (they're really for one-to-one communication); sockets could be, but you'd have to implement some sort of client-server model where the clients carry out tasks and the server hands them out, or something of that nature, then synchronizes data across the processes.

---

### Post by OutOfReach on 2009-08-18
Ahhh, nice. I've done a bit reading and shared memory segments with semaphores sounds like exactly what I need. I'll do a bit more in-depth reading. Thanks to both :)

---

### Post by SledgeHammer_999 on 2009-08-18
I don't know if this really suits you but you could use D-bus for IPC...

---

