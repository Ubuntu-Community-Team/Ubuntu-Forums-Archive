---
title: "I have tried everything to get rid of this error, /sbin/modprobe abnormal exit"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Clockworkxoa on 2008-06-17
Hi, I just got a new laptop and it came with vista but was not powerful enough to run it properly, so I decided to give Ubuntu a try after using it sucessfully on several friend's computers. 

The laptop is a Toshiba Satellite A305 
250GB Hard drive (I don't know what company)
Intel Core 2 duo T5550
It has built in ATI graphics (no exact specs given) 
3 Gigs RAM 

The problem I have is that every time I run installer it gets past the loading bar with the logo and goes to the boot CD menu, I run it to install with no splash and it loads everything but root file system. I've tried almost everything but I always get to the command prompt: 

udevd-event [1524]: run_program: '/sbin/modprobe' abnormal exit

BusyBox V1.1.3 (Debian 1:1.1.3-5ubuntu12) Built in shell (ash)
Enter 'Help' for a list of built in commands 

(Initrams) 

I just did a fresh reformat of vista so my laptop has no partions, or anything else set up on the hard drive. 

Thank you for the help.

---

### Post by kerry_s on 2008-06-17
try burning a new iso, 4x for the best results.

---

### Post by Clockworkxoa on 2008-06-17
I burned the Disk at 4x but still no resolve

---

### Post by annda on 2008-06-17
are you trying to install gutsy or hardy?

it seems that the problem might have already been resolved in hardy (8.04):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591)

---

### Post by Clockworkxoa on 2008-06-17
Hardy and I will try that fix thank you

---

