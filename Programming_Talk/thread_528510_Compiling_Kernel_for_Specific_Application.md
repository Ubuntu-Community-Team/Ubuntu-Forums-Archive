---
title: "Compiling Kernel for Specific Application"
date: 2007-08-18
forum: Programming Talk
---

### Post by Paris Heng on 2007-08-18
Dear,

Do anybody know how to compile the  Kernel for specific application from the main Kernel, so i get minimal kernel from it. And then, I am able to run it automatically when i power-up my motherboard and this done without using login.

The concept is same like this:~

"It is like a Auto Run concept when we put the CD/DVD in to the drive. It will pop up the windows."

My aim is to let the application (the compiled Kernel) to run at itself automatically when i power-up without invoke any setting.


Please assist if any ideas on HoW-to. 

Thanx~

---

### Post by slavik on 2007-08-18
umm, at startup (after disks are mounted and such), the kernel runs th scripts in the /etc/rc*.d/ directories depending on the runlevel being entered. start diggin there. :)

---

