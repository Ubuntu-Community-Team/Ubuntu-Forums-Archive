---
title: "where is source code of system calls?"
date: 2010-03-02
forum: Programming Talk
---

### Post by vksingh on 2010-03-02
Hi,

I have downloaded source code of linux kernel from [www.kernel.org](www.kernel.org). I have to some on some of the linux system calls.

Can any body tell me where is the source code of system calls in linux source is located?

Thanks,

Vivek

---

### Post by saulgoode on 2010-03-02
Top include is /usr/include/sys/syscall.h 

You would trace that to the appropriate file, which on my (32-bit) system is /usr/include/asm/unistd_32.h

---

