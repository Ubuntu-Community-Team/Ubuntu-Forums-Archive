---
title: "Compiling Kernel Modules???"
date: 2006-05-16
forum: Programming Talk
---

### Post by mak90 on 2006-05-16
After upgrading my breezy to 2.6.16 kernel, I find that the sata_mv.ko module is in an uncompiled state in my linux/drivers/scsi directory (its just the c file). I am assuming I need to compile this bad boy, but performing a 
gcc -c sata_mv.c -o sata_mv.o -l /usr/src/linux/include -D__KERNEL__

produces seroiusly heavy gcc errors, and I'm thinking I'm missing something. Any help?

THanks!

---

### Post by panabar on 2006-05-18
Not sure but [KernelHowto]("https://wiki.ubuntu.com/KernelHowto") says "You will need the gcc-3.4 compiler for 2.6 series kernels" .

---

