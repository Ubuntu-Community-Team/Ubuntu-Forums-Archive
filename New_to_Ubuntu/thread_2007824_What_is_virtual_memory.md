---
title: "What is virtual memory?"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by thinkndev on 2012-06-21
I've been studying about Linux for a few days now, and I stumbled on a compelling feature of Linux, that it uses virtual memory.  

Here's the source.
>  Another great advantage of Linux is that it offers a simple memory model to the user programs - it has a uniform address space of 2^32 bytes which can be addressed by a 32 bit pointer.  Although I understand the concept of physical memory - a caching "pool" - I don't understand the concept of virtual memory. 

What is a simple memory model, an address space, and a 32 bit pointer?  Why are they related?  And what's the significance of 2^32 bytes (why the 2 and the exponent 32)? 

Thanks.

---

### Post by haqking on 2012-06-21
> **thinkndev said:**
> I've been studying about Linux for a few days now, and I stumbled on a compelling feature of Linux, that it uses virtual memory.  

Here's the source.
Although I understand the concept of physical memory - a caching "pool" - I don't understand the concept of virtual memory. 

What is a simple memory model, an address space, and a 32 bit pointer?  Why are they related?  And what's the significance of 2^32 bytes (why the 2 and the exponent 32)? 

Thanks.

It is not a compelling feature of Linux, it is inherent in all modern computer architecture and OS.

[https://en.wikipedia.org/wiki/Virtual_memory](https://en.wikipedia.org/wiki/Virtual_memory)

the 2 because everything in computers comes down to base 2 because computers understand one thing (or more correctly only 2 states) and thats on or off which is a 1 or 0, binary.  Hence the 2 and multiples thereof.

Peace

---

### Post by lisati on 2012-06-21
Virtual memory isn't a new idea. The way I look at it, it's a way of managing resources which, amongst other things, can make it appear that a program has access to more memory (RAM) than would be available when virtual memory isn't being used. The program accesses the virtual memory as if it were real memory, and the details of where the information is actually stored is taken care of behind the scenes by a combination of specialised hardware and software (usually the OS, BIOS or equivalent).

---

### Post by lenny2100 on 2012-06-21
Virtual memory vs real memory is the key.  Real memory is the memory you buy when building a computer.  If you have 2GB of memory you have 2GB of real memory.  Early operating systems (1950's) used only real memory.  Later (1960's), when OS designers wanted to let apps have "more" memory, they mapped memory to another device, such as a hard drive (today it could be a usb flash drive) and only "swapped" it into real memory when the app needed it.  This was especially handy with "larger" computers that handled multiple batch jobs and/or multiple terminals.  When an app does an IO, for example, it takes a long time in terms of machine cycles.  The OS will swap the apps real memory out to virtual memory (disk) so that other apps which are currently using the cpu(s) can have the real memory in question, when the IO completes, our apps goes into the queue for cpu time and when it is scheduled to run, the OS will swap the virtual memory back to real memory, or with larger apps, just the portion of memory currently needed.  This, btw is called paging.  This higher technology generally became available to desktop computers in the 1990's with operating systems such as Linux, OS/2, Window 95 and Windows NT.

---

### Post by thinkndev on 2012-06-21
Maybe I exaggerated there about virtual memory as a compelling feature. 

Thanks for the explanations!

---

