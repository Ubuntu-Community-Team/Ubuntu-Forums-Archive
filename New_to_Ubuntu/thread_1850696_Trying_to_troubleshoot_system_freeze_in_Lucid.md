---
title: "Trying to troubleshoot system freeze in Lucid"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Monona on 2011-09-27
So, my system has been freezing up regularly lately, as in no response to keyboard, mouse frozen, and I have to hard power off.

As far as I can tell, there's no pattern of programs running.  I've got my system monitor running, and don't notice anything hogging the system prior to the crashes.

How do I troubleshoot this?

Here's my system specs:

Lucid 10.04
Kernel 2.6.33-29-realtime
Gnome 2.30.2
2G memory
Dual core Pentium D 3GHz

Thanks!

---

### Post by dFlyer on 2011-09-27
Before you do any thing check your hard drive for bad sectors. If your drive is failing it can cause a lot of problem.

---

### Post by dwasifar on 2011-09-27
Do you have another system on the same network?  If so, try to ssh in to the frozen machine and see if you can get connected.  If you can, it's just X that's frozen, not the whole system, and your troubleshooting should start by looking for video driver issues.

---

### Post by Monona on 2011-09-28
dFlyer: How do I check for bad sectors?  My SMART test under Disk Utilities looks ok, as far as I can tell.  What do you suggest I run?

dwasifar: I have my laptop on the same wireless network.  I have no idea how to ssh in.  How should I start?

Thanks!

---

