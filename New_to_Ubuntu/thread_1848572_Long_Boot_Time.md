---
title: "Long Boot Time"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by therundleman on 2011-09-22
[SIZE=4]Hello,

I am experiencing long boot times of 45 - 60 minutes under a native 11.04 environment. During a reboot today (after a recommended OS upgrade) I got a message saying my HW was insufficient to run Unity. This message went away, the boot completed, and the system is now running fine. [/SIZE][SIZE=4] 

Is their a way to monitor the boot process real time and see what may be taking so much time? Any ideas about the Unity message?  [/SIZE]

[SIZE=4]Thanks. [/SIZE]

---

### Post by LowSky on 2011-09-22
Hi Welcome to the forums. Nice Font, but please keep it the standard if you can. If you have trouble reading it yourself, try using the CTRL++ command to increase the font size locally. CTRL+- to shrink.

A 45-60 minute boot sounds rather nuts please tell me thats an exaggeration. I can only bet a hard drive failure or a install that went south quicker than an escaped prisoner. A system should boot well under 2 minutes using a standard 5400RPM hard drive, 1Ghz processor, and one gigabyte of RAM.

---

### Post by therundleman on 2011-09-22
Low Sky,

Thanks for the welcome and the quick response. No exaggeration on the boot time. Wouldn't a bad drive prevent any kind of boot? Do you know if I can copy my current OS environment to a USB drive and see if booting from that is faster? That may help isolate the problem to the existing internal drive I boot from. 

Thanks again.

---

### Post by Mark Phelps on 2011-09-23
No, a bad drive wouldn't necessarily prevent a boot -- but a failing drive will cause sectors to be read over and over -- and this will seriously add to the boot time.

---

### Post by P05TMAN on 2011-09-23
> **Mark Phelps said:**
> No, a bad drive wouldn't necessarily prevent a boot -- but a failing drive will cause sectors to be read over and over -- and this will seriously add to the boot time.
Agreed, & to answer your question about the message regarding the running of Unity, it means that your graphics card is not capable of handling the Unity interface.

---

### Post by fractalman on 2011-09-23
There's a package in the repos called 'BootChart',  it gives you a log of the boot up sequence as a png so you can see exactly what is doing what.  you should be able to install it through synaptic package manager, once installed  the png files will be in /var/log/bootchart

---

### Post by aura7 on 2011-09-23
Install BootUp-Manager and remove those programs from boot which takes more time

---

### Post by therundleman on 2011-10-02
Replacing the drive has fixed the problem. Thanks everyone.

---

