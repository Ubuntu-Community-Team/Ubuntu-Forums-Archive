---
title: "Unknown syslog message"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-08-15
Aug 15 14:39:15 PJ kernel: [22731.471080] Uhhuh. NMI received for unknown reason b0 on CPU 0.
Aug 15 14:39:15 PJ kernel: [22731.471091] You have some hardware problem, likely on the PCI bus.
Aug 15 14:39:15 PJ kernel: [22731.471096] Dazed and confused, but trying to continue

This appeared today out of nowhere...any ideas on what it might mean?

---

### Post by Cypher on 2008-08-16
A NMI is a Non-Maskable Interrupt. An interrupt is a hardware mechnism available to peripherlas and devices in a system to tell the CPU that they are looking for some service.

However, any given interrupt should be masakable to allow it to be ignored. Having one that is non-maskable means that it could potentially interrupt constantly and wreak havoc on the system.

So, bottom line, the Kernel is basically warning you know that it received such an interrupt on CPU 0..

If this is only a infrequent thing, you can safely ignore it but should the machine start to crash or misbehave for no reason, then you have something to look at as a likely culprit..

---

### Post by dunbrokin on 2008-08-16
> **Cypher said:**
> A NMI is a Non-Maskable Interrupt. An interrupt is a hardware mechnism available to peripherlas and devices in a system to tell the CPU that they are looking for some service.

However, any given interrupt should be masakable to allow it to be ignored. Having one that is non-maskable means that it could potentially interrupt constantly and wreak havoc on the system.

So, bottom line, the Kernel is basically warning you know that it received such an interrupt on CPU 0..

If this is only a infrequent thing, you can safely ignore it but should the machine start to crash or misbehave for no reason, then you have something to look at as a likely culprit..


Ok, thanks for that...I will watch out for repeated errors and come back if I find them....

---

