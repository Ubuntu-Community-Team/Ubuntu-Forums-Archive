---
title: "High Speed Multiple Interrupt for different devices are not working"
date: 2019-06-22
forum: New to Ubuntu
---

### Post by dsrking2006 on 2019-06-22
Hello All,

a) I am using a high speed interrupt for two boards. Both boards are having separate drivers. One is a SBC (single board computer) and another one PC104+ card. Both are connected together. Both are using different base address and IRQ. There are no sharing IRQ. OS is Ubuntu 16.04. Processor is bay trail.
b) SBC is having LPC interface and running interrupt in 5KHz speed.
c) PC104+ card driver is having PCI interface and running interrupt in 5KHz speed. 
d) If we run both boards driver simultaneously, one board interrupt is stopped or missed. I am just clearing the interrupt inside ISR and monitoring the interrupt in /proc/interrupts.
e) If we run both boards driver individually, both are working fine.

Question:

a) Will the high speed interrupt of LPC bus affects PCI device interrupt?
b) Is there any way to find the maximum supported frequency for interrupt?
c) I checked /proc/interrupts and it shows that both interrupts are running under same CPU eventhough it has 4 CPUs.
d) I tried with irqbalance command in Ubuntu but it is not sharing.

It would be helpful if you provide any ideas on this issue.

---

