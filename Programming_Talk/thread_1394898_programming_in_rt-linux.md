---
title: "programming in rt-linux"
date: 2010-01-31
forum: Programming Talk
---

### Post by drifterlom on 2010-01-31
Hi,
First of all, sorry if my English isn't so well, I'll try to write carefully.
I've installed the linux-rt kernel. I've red that kernel allow to work rt-processes while the ordinary linux-kernel is waiting with low priority.
If I'm writing a code in C, should I mention somewhere in code that it will be  a real-time process and that process should work with rt-kernel, not with ordinary linux-kernel.
Could you give me some examples of code of real-time processes?
Thanks in advance.

---

### Post by Maz_ on 2010-01-31
It has been long since I last encountered RTLinux. Back then the realtime threads (which sat on top of rt kernel, not on top of linux kernel) had to be inserted in kernel as modules. So yes, there's quite a huge bunch of differencies. 

The RT threads shared the kernel memory space, and had straight access to HW, and they did not use virtual memory. So basically with an invalid pointer you had the power to crash the kernel, or even write to some peripherial memory. I only messed up one soundcard though, but I've read cases where a network card has been tampered into unusable state. It's amazing how much information the modern devices store on memory :/ 

With improper priorities, you end up halting everything but your RT thread, and end up pressing the power button way too often :D (Been there, done that)

And naturally, you do have a limited set of functions to use, compared to full POSIX standard.

But my information is not really recent, things may have moved forward. Everyone who has been hassling with standard linux kenel knows, that things change faster than you can keep up :D

---

### Post by shantanuspathak on 2010-02-05
i am first time trying to even start RTLinux on ubuntu by using command 
sudo apt-get install linux-image-rt linux-headers-rt linux-restricted-modules-rtIn ubuntu. 
Can you please guide me more regarding how the screen of rtlinux should look like and how will be the interface ?

---

