---
title: "creating a new system call"
date: 2009-03-03
forum: Programming Talk
---

### Post by samarth.s on 2009-03-03
Hi, 
I am using ubuntu 8.04.1 LTS...

I have been reading the net for the creating a system call and I understand-
1. need to create a new function

2. Update header files - in '/usr/src' I have 4 linux folders, viz.,
   linux-headers-2.6.24-19, linux-headers-2.6.24-19-generic, 
   linux-headers-2.6.24-23, linux-headers-2.6.24-23-generic
   'unistd.h' file in which of these folders do I need to update?

3. Update the system call table for the new function - where is it??
   There is no such file - '/usr/src/linux/arch/x86/kernel/syscall_table.S'
            or    '/usr/src/linux/arch/x86/kernel/syscall_table_32'!!!!

could anyone provide more knowledge on these steps or is there a better way?

Thank You in advance

---

### Post by Roptaty on 2009-03-03
What is the purpose of creating a new system call? Why do you want to create it? Do you really need to create it?

---

### Post by samarth.s on 2009-03-03
I am working on a project related to file systems. Need to write to raw hard disk partition. So, I guess I would be requiring to use the kernel functions to carry out various functions of the file system. To make them available in the user space I'll have to create system calls.

---

### Post by cabalas on 2009-03-03
Have you looked at this, it seems to be a reasonably complete guide [http://www.tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/](http://www.tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/)

---

### Post by cabalas on 2009-03-03
> **samarth.s said:**
> I am working on a project related to file systems. Need to write to raw hard disk partition. So, I guess I would be requiring to use the kernel functions to carry out various functions of the file system. To make them available in the user space I'll have to create system calls.

Are you sure you should be looking at system calls, maybe you might be better off looking at file systems in particular I think you should have a look at [FUSE]("http://fuse.sourceforge.net/")

---

### Post by samarth.s on 2009-03-03
It seems I cannot open fuse.sourceforge.net...my college administrator seems to have blocked it...what is a better solution than creating system calls??

---

### Post by cabalas on 2009-03-03
To be honest it doesn't sound like you are wanting to write a system call by replacing various functions **of** the file system sounds like you are replacing the file system and something like fuse would probably be the easier road to go as it can work on top of already existing file systems and gives you access to all the userspace libraries.

Also for more info: [http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)

---

