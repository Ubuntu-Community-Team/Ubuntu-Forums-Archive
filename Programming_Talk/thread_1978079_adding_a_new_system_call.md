---
title: "adding a new system call"
date: 2012-05-11
forum: Programming Talk
---

### Post by glugT on 2012-05-11
hi,

I am trying to add a new custom system call to my kernel.
kernel version 3.4.0.
can anyone give a detailed step by step instruction on how to do it.

---

### Post by lisati on 2012-05-11
Not exactly a task for an absolute beginner?

*Thread moved to **Programming Talk**.*

---

### Post by codemaniac on 2012-05-11
You can find the below links useful , however it assumes you are familiar with bulding kernel .
[http://www.cs.brynmawr.edu/cs355/howto_add_systemcall.html](http://www.cs.brynmawr.edu/cs355/howto_add_systemcall.html)
[http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/](http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/)

---

### Post by glugT on 2012-05-11
hi,
sorry for posting it in the absolute beginner.I am not a beginner.And i got how to do it.thanks

---

### Post by lisati on 2012-05-11
> **glugT said:**
> hi,
sorry for posting it in the absolute beginner.I am not a beginner.And i got how to do it.thanks

Were the links provided by codemaniac any help?

---

### Post by PeterP24 on 2012-05-11
sorry for stepping by - You do realise that this thread will step over in searches for "how to add a new custom system call to Linux kernel"?

So if you found an immediate and nice solution: it is too much to ask you to share it with us?

Thanks!

---

### Post by glugT on 2012-05-14
hi,

I would love to share it.

let the place where you downloaded the kernel be called linux-3.4

First add the system call code to linux-3.4/fs/open.c

and then add your system call number and name in the file syscall_32.tbl which will be in linux-3.4/arch/x86/syscalls/syscall_32.tbl

then build your kernel and boot into it.

---

### Post by glugT on 2012-05-14
> **lisati said:**
> Were the links provided by codemaniac any help?


I guess they were for older kernels.I had tried them before.I may have made errors too but they did not seem to work for me.

---

### Post by codemaniac on 2012-05-14
> **glugT said:**
> I guess they were for older kernels.I had tried them before.I may have made errors too but they did not seem to work for me.
 
It was there just to get you started with the basics .
Can you share the errors you are getting while you compile ?

---

### Post by glugT on 2012-05-15
> **codemaniac said:**
> It was there just to get you started with the basics .
Can you share the errors you are getting while you compile ?


The directories and files mentioned were not present in my kernel.the paths were different and in some files were not present.

So the method i had mentioned worked.To add systems call in older kernels like 2.6 leads to many make errors.gcc 4.6 compilers are not compatible with older kernels

---

