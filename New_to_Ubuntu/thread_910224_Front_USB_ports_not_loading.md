---
title: "Front USB ports not loading"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by sum1cross on 2008-09-04
I am having trouble with the front USB ports on my computer.

Over a period of time it has got to the point where no devices are recognised when plugged into the front ports.  The same device plugged into a rear port is recognised immediately.

I have attached part of one of my log files which shows an eror 71, which translates as a protocol error.

Does anyone have any ideas?

System is Ubuntu 8.04 (64 bit), kernel 2.6.24-19 Generic, Gigabyte motherboard, AMD Athlon 4400+ dual core processor.

Thanks

Jim

---

### Post by Pro-reason on 2008-09-05
Does the same thing happen if you boot into something else (Windows, your Ubuntu live CD, etc...)?

If so, it is a hardware problem.  Have you checked the wires that connect the front of the box to the motherboard?

---

### Post by Rocket2DMn on 2008-09-05
It could be a problem with your hardware, but you can try disabling the ehci_hcd module
```
sudo rmmod ehci_hcd
```
Then try to plug in the device again.

---

### Post by sum1cross on 2008-09-05
Thanks Pro-reason and Rocket2DMn.

I tried booting from a Live CD, and had the same result (2gb JetFlash drive would not load in front USB, but would come up straight away through rear USB).

I also tried rmmod ehci_hcd.  JetFlash came up straight away when I plugged it in.  Didn't try writing to it, but was able to read and open files.

It would seem this could be a hardware problem with the front ports.  Not sure if it's the ports, or the mother board.  I haven't checked the cables to the motherboard, however as the 2 front ports are cabled individually to different USB pinss on the motherboard, it would seem unlikely both would be affected by a cable issue.

As the rear USB's are not affected, I am going to assume the fault is with the front ports only (the MB is around 2 yrs old but the case and front USB is around 8yrs old), unless someone can come up with another diagnosis.

Thanks again
Jim

---

