---
title: "syscall in a kernel module"
date: 2009-06-11
forum: Programming Talk
---

### Post by ranthal on 2009-06-11
Hey all,

I am writing a loadable kernel module that will be interacting with a daemon in user space and it will be doing so via kernel sockets and system calls.

I've read up on a few different online sources on how to accomplish this and I haven't fully moved implemented it yet, but when I tried to compile my code just to test insmod and rmmod, no actual syscall table manipulation, I got an error about sys/syscall.h not existing.

For now I've commented it out and it compiled fine but looking ahead do I need to include this file?  I want to declare the index to the system call table within my module so I don't have to patch the kernel since it's part of a much bigger build system.

Currently developing on kernel 2.6.26.2 but the module will eventually be used on 2.6.19.1.  This may seem somewhat backwards and I can explain if you really want but its kind of long...

---

### Post by ranthal on 2009-06-11
Just found linux/syscalls.h which seems to ahve a numebr of the kernel supported syscall function declarations but no syscall table.

Am I warm?

---

### Post by lensman3 on 2009-06-11
Mine is:
 
/usr/include/asm/unistd_64.h

or if you are 32

/usr/include/asm/unistd_32.h

---

### Post by ranthal on 2009-06-11
> **lensman3 said:**
> Mine is:
 
/usr/include/asm/unistd_64.h

or if you are 32

/usr/include/asm/unistd_32.h

thanks, checked it out and it all looked good.

after banging my head against the wall for a while i ended up going with netlink sockets so i don't have to deal with the messiness of the syscall table for anyone who might be dealing with similar frustration and looking for another solution.

---

