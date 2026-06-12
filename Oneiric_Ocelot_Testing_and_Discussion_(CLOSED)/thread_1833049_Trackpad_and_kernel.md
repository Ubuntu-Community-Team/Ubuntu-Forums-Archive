---
title: "Trackpad and kernel"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by aeronutt on 2011-08-25
I'm trying to learn a bit about how all this development of open software really works. :)

So, for example, my trackpad currently is not recognized by the latest Ubuntu releases or kernels. I've read, that the kernels are now the primary place that these resources (like trackpads) are built in.

How would I find out if my particular trackpad is being considered to be added to a kernel build, or, how would I find out if a driver is available that I could add to my own kernel compile?

I've posted here in Oneiric because I thought this community would be familiar with how all this works, and I could ask questions about this current effort.

---

### Post by sanderd17 on 2011-08-25
Most kernel discussions happen in the mailing list I suppose:[http://www.kernel.org/pub/linux/docs/lkml/](http://www.kernel.org/pub/linux/docs/lkml/)

But as all mailing lists, it's difficult to get an overview of it.

The kernel indeed contains the drivers, but the kernel in Ubuntu contains all drivers available.

If you are interested in open source development, I would not start with such a big project as the kernel. Start hacking on something small.

I know LibreOffice has a list of "hacks for beginners", so you can familiarise yourself with their code and way of working.

---

