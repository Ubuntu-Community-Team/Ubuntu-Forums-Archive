---
title: "[SOLVED] I/O per Proc"
date: 2008-04-01
forum: Programming Talk
---

### Post by FlashOmega on 2008-04-01
I am developing a system monitor terminal process that combines the functionality of top and iostat ... plus a little more... kinda like an all in one system monitor.

I hit a snag as someone asked me to include a listing of IO hogs (processes)

so there are a couple of different ways I am ok with doing this.

If I could find out when a process is performing io

or

if I could find out a list of io hogs (if I could find out how much they have written I could divide it by their uptime to see if they are a hog)

or

anything else I suppose

Any ideas on how to get io info per process?

Writting it in C incase that is important

Thanks:D

---

### Post by stroyan on 2008-04-01
You really want the taskstats interface.  It is quite new.
Along with task delay statistics it can also report IO statistics per task or process.
It is an optional kernel feature selected by the CONFIG_TASKSTATS and
CONFIG_TASK_IO_ACCOUNTING kbuild options.
It is not enabled in the default ubuntu kernels up to the gutsy release.
It is enabled in the hardy heron kernels, as noted by
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/157191](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/157191)

There is a nice iotop.py utility written in python available at
[http://guichaz.free.fr/misc/](http://guichaz.free.fr/misc/)

There is a not quite so nice usage example written in C at
[http://www.kernel.org/doc/Documentation/accounting/getdelays.c](http://www.kernel.org/doc/Documentation/accounting/getdelays.c)

---

### Post by FlashOmega on 2008-04-02
Awesome, I wonder why it is disabled by default... it is a really crucial tool for admins.  

Anyway thank you

---

### Post by FlashOmega on 2008-04-14
I know it wont matter come the new ubuntu anyway... but how would I add that to my kernel so that I can use this feature?

the end result will be in a make file as an option when installing ... so a command line option would be sweet

---

### Post by nanotube on 2008-04-14
> **FlashOmega said:**
> I know it wont matter come the new ubuntu anyway... but how would I add that to my kernel so that I can use this feature?

the end result will be in a make file as an option when installing ... so a command line option would be sweet

i think it's a compile-time option, so you'd have to recompile the kernel to enable this...

---

