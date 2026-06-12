---
title: "reclaiming leaked memory"
date: 2009-07-20
forum: Programming Talk
---

### Post by Elisei on 2009-07-20
Hi there,

Is there a way to recover used up memory after running a process that (very likely) has a memory leak? 
More specifically, the process is a PHP script that uses fgets() to read in a text file line  by line. It seams that the buffer used by fgets() is never released after the process finishes or if the process is killed. 

Maybe there is some sort of utility like  'free' that would actually perform the garbage collection to free up the ram ?

Thanks!

---

### Post by tht00 on 2009-07-20
> **Elisei said:**
> Hi there,

Is there a way to recover used up memory after running a process that (very likely) has a memory leak? 
More specifically, the process is a PHP script that uses fgets() to read in a text file line  by line. It seams that the buffer used by fgets() is never released after the process finishes or if the process is killed. 

Maybe there is some sort of utility like  'free' that would actually perform the garbage collection to free up the ram ?

Thanks!

Killing the process should free up any memory used by that process.

---

### Post by stroyan on 2009-07-20
Almost all memory used by a program is allocated by stack, heap, or mmap calls.  It is only accessible to the program that allocates it and direct descendants that fork or clone without any exec.  That memory is always released back to the system when the last process that can access it exits.

Some programs allocate shared memory that can be accessed by other processes.  Such memory may outlive the process that creates it.  It may be used by other processes that know the id for the memory.
See [http://www.kernel.org/doc/man-pages/online/pages/man7/shm_overview.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/shm_overview.7.html) for a discussion of the posix shared memory and System V shared memory mechanisms.  Removing posix shared memory segments can be done on linux using file system operations on /dev/shm.  Removing System V shared memory segments can be done with ipcs and ipcrm commands.  But it is difficult to know whether a remaining shared memory segment is leaked or is left behind intentionally for other programs to read information from later.  A programmer that uses such shared memory should provide some tools to manage the shared memory in case of an abnormal termination.  (But almost no one does that.)

---

