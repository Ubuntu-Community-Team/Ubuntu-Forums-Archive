---
title: "System calls in Ubuntu"
date: 2006-10-13
forum: Programming Talk
---

### Post by jivesoul on 2006-10-13
Hey everyone.

I am trying to work with system calls in Ubuntu 6.06.  Kernel is 2.6.15-27-386.  

I have found a few guides around the internet that discuss intercepting system calls in a kernel, but I cannot get any of them to work.  Most discuss editing entry.S, but I cannot find this file anywhere.  Others discuss using sys_call_table, but it seems like it is no longer exported by the kernel.

Does anyone know how to use system calls in Ubuntu?  I need to be able to pass data to a kernel module, and a system call would really help.

Thanks.

---

### Post by JonahRowley on 2006-10-13
If you need to exchange data with a kernel module, an entry in /dev would probably be a better bet.  System call numbers can change, but it's not likely that **/dev/my_module** would ever be claimed by the kernel developers.

---

