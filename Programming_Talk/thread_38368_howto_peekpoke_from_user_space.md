---
title: "howto peek/poke from user space???"
date: 2005-05-31
forum: Programming Talk
---

### Post by Ronbin on 2005-05-31
hi
I'm trying to port some code from MS-DOS to linux. This code needs to read/write some data from/to video memory, using peek and poke. Is there any command to do the same in linux, from user space????

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=Ronbin]hi
I'm trying to port some code from MS-DOS to linux. This code needs to read/write some data from/to video memory, using peek and poke. Is there any command to do the same in linux, from user space????[/QUOTE]
 Not from user-space, no.  You're goign to be completely rewritting the application, I think.  Telling us what it's supposed to do might yield better results, though.

---

### Post by Ronbin on 2005-05-31
[QUOTE=LordHunter317]Not from user-space, no.  You're goign to be completely rewritting the application, I think.  Telling us what it's supposed to do might yield better results, though.[/QUOTE]
The aplication is for student use. It does some simple actions (write some characters, scroll the pant, show a cursor.....). The goal is to show students how the hardware works. So, they will have to use system calls like inp or outp, and work with memory adresses. The abstraction must be minimall.

Sorry about my english.

---

### Post by LordHunter317 on 2005-05-31
Your better off giving them VMware and DOS then, or just DOS.  Such direct interaction isn't possible under Linux directly, and with good cause.

I do believe on x86 there is a way to allow root programs to do some I/O port access, but I don't remember all the gory details.  What you can do through it is kinda limited anyway.

---

### Post by Ronbin on 2005-06-01
yes, I know. But would it be possible to create a module which does the "dirty job", and call it from a user-space program???
I mean, a module that exports some functions for reading/writing memory (using ioremap????), and use them from user space.

I've read on "Linux device drivers" (3rd edition) that direct access memory is possible *mmap*ping /dev/mem, but is a module oriented book, and it doesn't explain how. Somebody knows any tutorial, or something which explains that???

> 
But the user-space approach to device driving has a number of drawbacks. The most important are:

-Interrupts are not available in user space. There are workarounds for this limitation on some platforms, such as the vm86 system call on the IA32 architecture.

-Direct access to memory is possible only by mmapping /dev/mem, and only a privileged user can do that.

-Access to I/O ports is available only after calling ioperm or iopl. Moreover, not all platforms support these system calls, and access to /dev/port can be too slow to be effective. Both the system calls and the device file are reserved to a privileged user.

-Response time is slower, because a context switch is required to transfer information or actions between the client and the hardware.

-Worse yet, if the driver has been swapped to disk, response time is unacceptably long. Using the mlock system call might help, but usually you'll need to lock many memory pages, because a user-space program depends on a lot of library code. mlock, too, is limited to privileged users.

-The most important devices can't be handled in user space, including, but not limited to, network interfaces and block devices.

---

