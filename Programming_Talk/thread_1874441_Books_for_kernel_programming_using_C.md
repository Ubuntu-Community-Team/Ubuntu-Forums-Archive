---
title: "Books for kernel programming using C"
date: 2011-11-03
forum: Programming Talk
---

### Post by ps_arunkumar on 2011-11-03
Hi all,

I read **[B]Sticky:**[/B] 			                          			 			[Programming Guides and Basics - Read Me First]("http://ubuntuforums.org/showthread.php?t=1766253"). Most of them are giving links to C and C++ books. I studying C in "The C Programming Language by Dennis Ritchie' and Kernel architecture in "Professional Kernel architecture by Wolfgang". But when I look for the kernel programs, it was different from the C which I learn in C books. 

Could anyone please tell me which book should I refer, to learn kernel programming using C.


thanks,
Arun

---

### Post by ofnuts on 2011-11-03
> **ps_arunkumar said:**
> Hi all,

I read **[B]Sticky:**[/B]                                                                [Programming Guides and Basics - Read Me First]("http://ubuntuforums.org/showthread.php?t=1766253"). Most of them are giving links to C and C++ books. I studying C in "The C Programming Language by Dennis Ritchie' and Kernel architecture in "Professional Kernel architecture by Wolfgang". But when I look for the kernel programs, it was different from the C which I learn in C books. 

Could anyone please tell me which book should I refer, to learn kernel programming using C.


thanks,
ArunC is C, whether it's for an image processing program, an accounts payable application or kernel programming. There may be different writing styles and conventions and emphasis put on different functionalities, but it's still the same language. 

But if you are still confused about C, start by being really proficient with C and programming in general before you take kernel programming, because it's significantly more difficult and complex and harder to debug.

---

### Post by karlson on 2011-11-03
> **ps_arunkumar said:**
> Hi all,

I read **[B]Sticky:**[/B] 			                          			 			[Programming Guides and Basics - Read Me First]("http://ubuntuforums.org/showthread.php?t=1766253"). Most of them are giving links to C and C++ books. I studying C in "The C Programming Language by Dennis Ritchie' and Kernel architecture in "Professional Kernel architecture by Wolfgang". But when I look for the kernel programs, it was different from the C which I learn in C books. 

Could anyone please tell me which book should I refer, to learn kernel programming using C.


thanks,
Arun

This book is pretty decent.

[http://www.amazon.com/Linux-Kernel-Development-Robert-Love/dp/0672329468/ref=sr_1_1?ie=UTF8&qid=1320323059&sr=8-1](http://www.amazon.com/Linux-Kernel-Development-Robert-Love/dp/0672329468/ref=sr_1_1?ie=UTF8&qid=1320323059&sr=8-1)

But before you get there I would suggest to get proficient with C for Applications because unless you are writing a device driver or something like a network stack it doesn't belong in the kernel.

---

### Post by 11jmb on 2011-11-03
This online resource is not bad (and free:D)

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)

It is designed for version 2.6, though, and 11.10 uses version 3.0, so I am not sure what will be affected (if you have an older release, it does not matter though)

---

### Post by matt_symes on 2011-11-03
Hi

Download the kernel sources and have a look through them. They are a great way to see how things have been implemented in the past.

Learn the major subsystems of the kernel such as scheduling and memory management. Understanding the theory of them will help when it comes to deciphering the code.

Lean C inside out, and i mean inside out! Get yourself a copy of 'The C Programming Language' by k&n and read it. Then read it again. And once more.

Learn how hardware works cpu, buses (etc) and read the RFCs and the technical spec's. Take a look at some of the embedded C websites around.

Understand the differences between user and kernel mode programming in C. Learn how to debug kernel mode code.

Start off easy with a kernel module you can load with modprobe and print something to kernel ring buffer. Then extend it.

Kind regards

---

### Post by 11jmb on 2011-11-03
> **matt_symes said:**
> Hi

Download the kernel sources and have a look through them. They are a great way to see how things have been implemented in the past.

Learn the major subsystems of the kernel such as scheduling and memory management. Understanding the theory of them will help when it comes to deciphering the code.

Lean C inside out, and i mean inside out! Get yourself a copy of 'The C Programming Language' by k&n and read it. Then read it again. And once more.

Learn how hardware works cpu, buses (etc) and read the RFCs and the technical spec's. Take a look at some of the embedded C websites around.

Understand the differences between user and kernel mode programming in C. Learn how to debug kernel mode code.

Start off easy with a kernel module you can load with modprobe and print something to kernel ring buffer. Then extend it.

Kind regards

That's quite a bit to bite off at once. If you are starting out, I recommend getting very good at writing user space C applications and peppering in some knowledge of architectures and assembly language. 

I don't think that downloading and reading kernel source is going to do you much good before you are good with C.

---

### Post by matt_symes on 2011-11-03
Hi

> **11jmb said:**
> That's quite a bit to bite off at once.

Yeah. This is true :D

The realities are though, if you want to be a proficient kernel  developer you do have to understand these concepts. There is no escaping  this fact. The Linux kernel may be layered and abstracted in places but  to understand the whole process you need to know these concepts.

That's why i suggested a kernel module as a start though. 

I would start off with a loadable kernel modules that creates and exposes a dummy interface in sysfs where one can read and write values.

This book 'Linux device drivers 3' by Jonathan Corbet and Alessandro Rubini may be a good place to start.

Although i have never read it, 'Linux kernel development' by Robert Love may also help.

The reason i suggested the kernel source is because the kernel is in a constant state of flux. You can always go straight to the horses mouth with the source code.

I would suggest becoming proficient in user space programming first though.

Create a daemon that forks and does something.

As 11jmb said though and i tried to make clear in my last post, become proficient in C first.

Kind regards.

---

### Post by ofnuts on 2011-11-03
> **matt_symes said:**
>  Get yourself a copy of 'The C Programming Language' by k&n 
K&N makes performance parts for engines. Performance software for computers is by K&R :-)

---

### Post by matt_symes on 2011-11-03
Hi

> **ofnuts said:**
> K&N makes performance parts for engines. Performance software for computers is by K&R :-)

Dagnamit! Typo :D

Thanks for correcting me there. 'tis a good book.

Kind regards

---

### Post by ps_arunkumar on 2011-11-03
Thanks all for the wonderful guiding!

I will start with C again and learn slowly look for kernel modules.

thanks again for the help.

---

