---
title: "sharing clock's interrupt"
date: 2005-08-21
forum: Programming Talk
---

### Post by Scalion on 2005-08-21
hi there

I'm trying to do a kernel module (for academical pourpose), which shows the students how interrupts are handled in linux. My idea is to register a handler at irq 0, using request_irq. This handler's job would be so simple, it will use a counter (named tik), that would be incremented at each clock interrupt. Thanks to this counter, I'll be able to know how many seconds have passed since the module was loaded, and I'll use this info to show some data from screen. Every 2 seconds, the current time will be shown, and after 60 seconds, the moudule will finish.

But after trying to program it, I want to know if the system's clock handler is a shared one. If it isn't, is there any form to put 2 different handlers working together at irq 0???

---

