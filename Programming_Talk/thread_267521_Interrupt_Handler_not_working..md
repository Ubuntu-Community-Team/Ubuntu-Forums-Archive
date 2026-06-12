---
title: "Interrupt Handler not working."
date: 2006-09-28
forum: Programming Talk
---

### Post by funnyfraggle on 2006-09-28
I'm trying to write a kernel module driver for an ISA card. I have the reading from and writing to the hardware working, but my interrupt handler never gets called. ](*,) 

When I call request_irq it returns success, but when I wait for an IRQ one never occurs. I've confirmed that the card itself is signalling an interrupt by hooking it up to an oscilliscope, but the handler is never getting called.

The handler shows up correctly when I cat /proc/interrupts.

I would post code, but I'm not really sure what to post, and there is quite a lot of it. I'm hoping someone has had similar problems or can point me to a better resource than the ones I've been finding.

---

### Post by funnyfraggle on 2006-09-29
Problem solved. I had my parameters to outb backwards of all things. Two days wasted, but now I have the driver I was looking to create :).

---

