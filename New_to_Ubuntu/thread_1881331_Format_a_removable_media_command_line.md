---
title: "Format a removable media command line"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-15
Hello everyone.... :)
I want to know how to format removable media like pendrives thorugh command line...
I know there is gui options by right clicking that drive.. but i want to do this on command line...

Also there is another question...it's kind of based on generic os kernel and concepts of scheduling not spefic to linux or windows...
It's in the image...
[IMG]http://img405.imageshack.us/img405/374/kernelanduserthreads.jpg[/IMG]

---

### Post by 11jmb on 2011-11-15
you can use mkfs to format your drive

[http://manpages.ubuntu.com/manpages/hardy/man8/mkfs.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mkfs.8.html)

---

### Post by 11jmb on 2011-11-15
In response to your second question, the answer is abstraction. The kernel does a lot more than just execute threads.  For example, even though segmentation faults drive programmers nuts, they are a gift from the kernel, because otherwise the program would just access memory that is possibly allocated to another program and run into some other weird runtime error. Basically, the kernel will hide a lot of ugly things from user space programs.

---

### Post by greendragons on 2011-11-15
> **11jmb said:**
> In response to your second question, the answer is abstraction. The kernel does a lot more than just execute threads.  For example, even though segmentation faults drive programmers nuts, they are a gift from the kernel, because otherwise the program would just access memory that is possibly allocated to another program and run into some other weird runtime error. Basically, the kernel will hide a lot of ugly things from user space programs.

The segmentation faults are informed through traps(which is responsibility of hardware) which are then handled by Interrupt handler and exits the error causing program....isn't?

About kernel mode... u mean mode bit is only set to kernel mode when user makes syscalls or any trap condition is raised...otherwise user thread (actually mapped kernel thread in disguise) runs the user code wit mode bit set to user space.....?

---

### Post by greendragons on 2011-11-15
> **11jmb said:**
> you can use mkfs to format your drive

[http://manpages.ubuntu.com/manpages/hardy/man8/mkfs.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mkfs.8.html)

Kool i was able to format my drive....
:)
Thnx!!!!

---

### Post by 11jmb on 2011-11-15
> **greendragons said:**
> The segmentation faults are informed through traps(which is responsibility of hardware) which are then handled by Interrupt handler and exits the error causing program....isn't?

If the program tries to access memory that is not physically addressable, the hardware will generate an interrupt, but user mode program will also segfault if it tries to access memory that it does not own.

> **greendragons said:**
> 
About kernel mode... u mean mode bit is only set to kernel mode when user makes syscalls or any trap condition is raised...otherwise user thread (actually mapped kernel thread in disguise) runs the user code wit mode bit set to user space.....?

Yes, when implementing syscalls the process is temporarily run in kernel mode.

The big difference is access to resources. Kernel mode processes can access any physically addressable memory, while user mode processes can only access memory that they own.

---

### Post by greendragons on 2011-11-15
> **11jmb said:**
> If the program tries to access memory that is not physically addressable, the hardware will generate an interrupt, but user mode program will also segfault if it tries to access memory that it does not own.



Yes, when implementing syscalls the process is temporarily run in kernel mode.

The big difference is access to resources. Kernel mode processes can access any physically addressable memory, while user mode processes can only access memory that they own.

Thnx alot bro!!!
You solved my problem... actually there is so much abstraction tht sometimes it's hard to relate it with reality underlying...OS is very complex and more i read about it makes me feel lesser i know...until we relate everything with each other, the concepts remain shallow and useless....

---

### Post by MG&amp;TL on 2011-11-15
> **greendragons said:**
> Thnx alot bro!!!
You solved my problem... actually there is so much abstraction tht sometimes it's hard to relate it with reality underlying...OS is very complex and more i read about it makes me feel lesser i know...until we relate everything with each other, the concepts remain shallow and useless....

Agreed. Software-center was abstracted until i knew about apt, and apt was abstracted until I knew about dpkg....the bits slowly fall together.

---

