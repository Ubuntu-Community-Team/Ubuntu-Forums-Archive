---
title: "what is paniclog"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-03
I have a directory called 'paniclog.'  I used the command 'file paniclog' to find out it consists of ascii text.  This is all I know.  Whats it for and how do I use it?  I only panicked a few times on Ubuntu.

---

### Post by germanix on 2008-10-03
What is a kernel panic?
As the name implies, the Linux kernel gets into a situation where it doesn&#8217;t know what to do next. When this happens, the kernel gives as much information as it can about what caused the problem, depending on what caused the panic. This info is stored in the paniclog.
There are two main kinds of kernel panics: 
1.Hard Panic &#8211; also known as Aieee! 
2.Soft Panic &#8211; also known as Oops 
What can cause a kernel panic?
Only modules that are located within kernel space can directly cause the kernel to panic. To see what modules are dynamically loaded, do lsmod &#8211; this shows all dynamically loaded modules (Dialogic drivers, LiS, SCSI driver, filesystem, etc.). In addition to these dynamically loaded modules, components that are built into the kernel (memory map, etc.) can cause a panic.

---

