---
title: "Virtual Machine - SGI IRIX"
date: 2010-11-14
forum: Programming Talk
---

### Post by DIFTOW on 2010-11-14
Are there any virtual machine setups that can emulate the hardware requirements to run SGI IRIX 4.1 or higher? The CPU has to be MIPS.

---

### Post by scu-ba-de-buntu on 2011-06-24
Did you ever figure this out? I too want to know. Thanks.

also, please move this thread to the Virtualization topics folder please.

---

### Post by eeperson on 2011-06-24
I recommend looking at the software on this page:

[http://www.linux-mips.org/wiki/Emulators]("http://www.linux-mips.org/wiki/Emulators")

---

### Post by scu-ba-de-buntu on 2011-06-25
> **eeperson said:**
> I recommend looking at the software on this page:

[http://www.linux-mips.org/wiki/Emulators]("http://www.linux-mips.org/wiki/Emulators")

Thanks. Would you recommend any of those in particular? My research peer uses one binary which has long lost the source that runs on an O2 Silicon Graphics computer. I have no interest in maintaining SGI machines.

---

### Post by tgalati4 on 2011-06-25
O2's were fast machines in their day.  I would normally recommend Xen, but I don't think they have a MIPs port.  But the source is available and you could try to cross-compile.  [http://xen.org/products/xen_source.html](http://xen.org/products/xen_source.html)

FreeBSD has a MIPs port, so a little googling:

Behive--BSD hypervisor, [http://wiki.freebsd.org/201105DevSummit?action=AttachFile&do=get&target=BHyVe.pdf](http://wiki.freebsd.org/201105DevSummit?action=AttachFile&do=get&target=BHyVe.pdf)

What was the code that you are trying to run?  Perhaps there is a newer replacement?

---

### Post by scu-ba-de-buntu on 2011-06-27
> **tgalati4 said:**
> What was the code that you are trying to run?  Perhaps there is a newer replacement?

The program is a very simple chemistry program called AtomTV. It was written by some guy in Toronto in the 90s, and our lab's visiting professor wants to use THAT program - not a clone, not a copy. (We already wrote a clone for him) He writes his own quantum simulation code in FORTRAN and then likes to check if it is working correctly using AtomTV. Which is all fine, except it requires us to maintain hardware which consistently fails while at the same time we have near unlimited x86 IBM compatible (STANDARD) hardware that is not only functional but newer, better, faster,stronger,etc.

---

