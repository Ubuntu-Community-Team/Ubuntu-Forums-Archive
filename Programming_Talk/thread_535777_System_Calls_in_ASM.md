---
title: "System Calls in ASM"
date: 2007-08-26
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-08-26
Seems to me the kernel *used* to export a system call table that could be used to sort out what registers to dump syscall params into in ASM programs.

Does anyone know where that went? I can't find it anywhere, and I *really* don't want external dependencies in this project.

---

### Post by Wybiral on 2007-08-26
I've never heard of the kernel exporting the syscall registers, but you can find tables of them online.

[http://docs.cs.up.ac.za/programming/asm/derick_tut/syscalls.html](http://docs.cs.up.ac.za/programming/asm/derick_tut/syscalls.html)

---

### Post by Carl Hamlin on 2007-08-27
Thanks, Wybiral.

I've actually seen that table, but some of the data doesn't seem to correspond to the calls as implemented in Ubuntu, or at least not on the machines I'm writing for.

When the kernel exported the syscall table, I could be reasonably assured that the information was going to be accurate on the machine the export came from.

Aargh. I can build it from scratch using trial and error if I have to, but that's going to be a real pain.

---

### Post by slavik on 2007-08-27
there should be a table in a .h file from the kernel, forget which though :(

---

### Post by Modred on 2007-08-27
I can't be sure if this is exactly what you're looking for, but it appears close:

[http://tiger.la.asu.edu/Quick_Ref/Linux_Syscall_quickref.pdf](http://tiger.la.asu.edu/Quick_Ref/Linux_Syscall_quickref.pdf)

---

### Post by fct on 2007-08-27
If it's what I think you want, the sys_call_table is no longer exported in the 2.6 kernel, though it was in the 2.4 series.

Instead, look for the function "get_sys_call_table" in google, those are some implementations to get the table in 2.6.

But I don't know if that's what you want, since I never tried getting info about the registers. I only replaced some signals for a uni project.

---

### Post by Carl Hamlin on 2007-08-27
Beauty.

Thanks, gentlemen. Between all of your replies I've got exactly what I needed. Pity the table doesn't export any longer. I wonder why not?

---

### Post by fct on 2007-08-28
> **Carl Hamlin said:**
> Pity the table doesn't export any longer. I wonder why not?

There are some explanations here:
[http://www.linuxdevcenter.com/pub/a/linux/2002/12/12/vanishing.html](http://www.linuxdevcenter.com/pub/a/linux/2002/12/12/vanishing.html)

---

### Post by Carl Hamlin on 2007-08-28
Aha. That makes a little more sense, although I disagree philosophically with the stated reasoning. Thank you.

---

