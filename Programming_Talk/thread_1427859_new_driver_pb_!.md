---
title: "new driver pb !"
date: 2010-03-12
forum: Programming Talk
---

### Post by soro on 2010-03-12
Hello,:p
I'm new in this forum, and I'm not sure if "Programming talk" is exactly the forum in which I should ask my question ? 
my question is:
I'm now developing a serial driver for COM port. the Pb is : I guess that serial port in ubuntu is compiled in the kernel (not a module); I verfy in /proc/interrupts no module for IRQ number 4. I precise that I Work on PC not a laptop. Hence, I use interrupt handling for transmiting characters. I desable IRQ 4 and I do rmmod for parports modules to use IRQ 7 instead of 4 but my handler dont work with IRQ 7 (no Kern message). sorry to be brief. ?
thanks in advance

---

