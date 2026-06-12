---
title: "What does the Kernel do ?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by roffemuffe on 2008-07-03
The kernel seems to be the essence of Linux. The heart that makes everything work.

As I understand, a Ubuntu installation has a standard allround kernel.
What happens when I recompile a kernel ?

Can I expect performance increase ? more stability? what are the upsides? Will it pay off to recompile my own kernel? Will my new recompiled kernel only hold information about my current hardware and not load anything else ?

What's inside a kernel ?

---

### Post by fatality_uk on 2008-07-03
There can be benfits to "rolling" your own kernel, such as taking out specific modules that will never be used, lets say on a server box. However, it's tricky, you *have* to understand what you are doing.

I like this article for explaining the Linux kernel.

[http://www.ibm.com/developerworks/linux/library/l-linux-kernel/](http://www.ibm.com/developerworks/linux/library/l-linux-kernel/)

---

### Post by ET! on 2008-07-03
kernel is the main code for any operating system. it contains pieces of code for scheduling operations,power management,device driver codes etc.....when you are recompiling a code you can make the kernel to contain only that options you need...for example if you are using a desktop you can safely disable the power saving options provided for laptop in that kernel. by stripping your kernel you can minimize the booting time. time and again kernel patches with added features are released. you can patch and recompile your kernel if you find the features useful.try downloading a kernel from the net and compile it

---

### Post by roffemuffe on 2008-07-03
Thanks. I have no imminent plan of doing a kernel recompilation :)
Just needed to know what it did before I wanted to venture on.

---

