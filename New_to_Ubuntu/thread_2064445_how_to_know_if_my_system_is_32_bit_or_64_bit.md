---
title: "how to know if my system is 32 bit or 64 bit"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-29
1. how to know if i have installed 32bit ubuntu on my system or 64bit
2. how to know if my pc architechture is 32 bit or 64 bit.... does it depends on architecture of pc , if it is 32 bit , i have to install 32 bit operating system, and if it is 64 bit, i have to install 64 bit operating system
3. what diference does 32 bit and 64 bit architecture and operating system???

---

### Post by newb85 on 2012-09-29
[s]32- vs. 64- bit architecture is a feature of the OS, not the hardware.  However, based on what hardware you have, one will probably run better than the other.[/s]  If the machine came with Windows pre-installed, a good rule of thumb is to mimic the architecture used by Windows.

To see which architecture is being used in Ubuntu, go to the "Details" section of "System Settings".

---

### Post by mips on 2012-09-29
post the output of 1 & 2 here.

1. uname -a
2. lscpu
3.  See links below,

[http://ubuntuforums.org/showthread.php?t=2037106](http://ubuntuforums.org/showthread.php?t=2037106)
[http://ubuntuforums.org/showthread.php?t=2062435](http://ubuntuforums.org/showthread.php?t=2062435)

---

### Post by jrog on 2012-09-29
> **newb85 said:**
> 32- vs. 64- bit architecture is a feature of the OS, not the hardware.
Not sure what you mean by this... There is 64-bit hardware and there is 32-bit hardware. Some processors are 64-bit processors, for example, while some aren't.

To answer the OP, you can tell whether the processor in your machine is 64-bit by typing (at the terminal): ```
cat /proc/cpuinfo | grep flags
```

If you see 'lm' (for **l**ong **m**ode) in the list of flags, then your processor is 64-bit.

> **newb85 said:**
> However, based on what hardware you have, one will probably run better than the other.
A 32-bit processor simply cannot run a 64-bit operating system, so if you have a 32-bit processor, you must run a 32-bit (or lower, but that shouldn't really be considered an option) OS.

On the other hand, if you have 64-bit hardware, you can run either a 32-bit OS or a 64-bit OS. The 64-bit OS will probably give better performance, and it is definitely the best option if you have 4+ GB of RAM.

> **newb85 said:**
> To see which architecture is being used, go to the "Details" section of "System Settings".
If you're interested in knowing, you can also do this at the terminal by typing: ```
uname -m
```

---

### Post by syednasirraza on 2012-09-30
thnx alll and specially jrog -  for such a detailed and nice reply.... i have got it

---

### Post by jrog on 2012-09-30
> **syednasirraza said:**
> thnx alll and specially jrog -  for such a detailed and nice reply.... i have got it
Great, and no problem! If you get the chance, please mark the thread as "solved" using the Thread Tools at the top of the page.

---

