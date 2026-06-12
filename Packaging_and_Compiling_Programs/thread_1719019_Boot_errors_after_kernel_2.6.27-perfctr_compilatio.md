---
title: "Boot errors after kernel 2.6.27-perfctr compilation"
date: 2011-04-01
forum: Packaging and Compiling Programs
---

### Post by FuzZy2006 on 2011-04-01
I have patched a 2.6.27 kernel with perfctr ( for processor counters ) and packaged the deb. I have copied the .config file in the latest ubuntu kernel. 

When i reboot I get the following errors:
i8042.c: no controller found
IO APIC resources could not be allocated
no init found. Try passing init=bootarg

And after that i get the initramfs prompt. 
What's wrong?

---

