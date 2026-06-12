---
title: "Ubuntu 16.04 lagging"
date: 2017-05-15
forum: New to Ubuntu
---

### Post by iqzibal on 2017-05-15
Hello Ubuntu Community,

I am new to Ubuntu and I have just installed it into my Lenovo however, it is currently lagging and I don't think I want and can work with a lagging OS. I have listed my specs below to give a context. I would like to start programming on Ubuntu as soon as possible as a friend recommended me. So may I know what I can do to have a smooth experience on Ubuntu?

**Computer Specs:**
**Processor:** Intel Core i5 1.70GHz 2.40GHz
**RAM: **4.00 GB
**System Type:** 64-bit OS, x64-based processor

[B]Ubuntu Specs:
[/B]**Base Memory:** 1024MB
**Video Memory:** 128MB

If it helps, whenever I run Ubuntu the performance of my computer is as the following (taken from Task Manager):
**CPU: **rough average of 15%
**Memory: **>90%
**Disk 0 (C: D:): **constantly 100%, mostly due to "System", "Service Host: Local System"

Hope that helps...

---

### Post by Bucky Ball on 2017-05-16
Welcome. You should make it crystal clear that you are running this as a virtual machine if you are, and by the info you've given, it seems you might be. Are you? Ubuntu should run fine with an i5 and 4Gb of memory, but you add these details.

> Ubuntu Specs:
Base Memory: 1024MB
Video Memory: 128MB

Try allocating 2Gb RAM to the Ubuntu virtual machine, if that's what you're doing. You don't mention anything about your video card, but you could also try backing off the vid memory to 64. With your machine specs you need to do a bit of a balancing act and see what works, if anything. 

You certainly don't need Ubuntu to start programming. An alternative would be to go with one of the lighter flavours like Xubuntu or Lubuntu. The ultimate solution is run a dual-boot and install Ubuntu or one of the flavours directly to the hard drive. I have Xubuntu-core running like lightning on an i3 with 4Gb RAM (and Kubuntu also runs fine as a virtual machine in that).

---

