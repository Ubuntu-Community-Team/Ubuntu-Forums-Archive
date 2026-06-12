---
title: "Bash command for 32bit or 64bit of cpu and OS"
date: 2009-03-05
forum: Programming Talk
---

### Post by flylehe on 2009-03-05
Hi,
I was wondering what are Bash commands for checking if my cpu and OS is 32bit or 64bit?
Thanks!

---

### Post by unutbu on 2009-03-05
```
uname -m
```
i686 means 32-bit
x86_64 means 64-bit

---

### Post by flylehe on 2009-03-05
Thanks!
I man uname, and it's for hardware, so for CPU?
How to check for operating system?

---

### Post by mpsii on 2009-03-05
```
$ uname -m
``` shows the current kernel in use.

```
$ cat /proc/cpuinfo|grep "model name"
```
will tell you the CPU you have.

If you have an AMD64, Phenom, Intel Core 2, or something within the last year (other than a Celeron), you more than likely have a CPU that can do 64bit. Some Pentium D processors also do 64bit, from (IIRC) 925 and up.

Intel Pentiums prior to Core 2 Duo/Quad were not 64bit capable, with the exception of some of the Pentium 4 Extreme Editions that were produced right before the Core 2 Duo released. I have heard mixed stories on the Core Duo processors -- they seem to have the capability, but were physically disabled by Intel.

AMD Athlons, Athlon XPs and almost all Sempron processors are 32bit.

VIA has nothing but 32bit.

---

### Post by flylehe on 2009-03-05
Thanks for the detail!
So by kernel, do you mean operating system?

My laptop's CPU is  AMD Turion(tm) 64 Mobile Technology ML-30. Is that 32 or 64-bit? It was bought in 2005

---

### Post by madverb on 2009-03-05
> My laptop's CPU is AMD Turion(tm) **64** Mobile Technology ML-30. Is that 32 or 64-bit? It was bought in 2005

Peace

---

### Post by mpsii on 2009-03-05
The kernel IS Linux at the core. The rest of the packaging is Ubuntu's distribution of Linux.

A Turion 64 does 64bit.

---

### Post by jespdj on 2009-03-06
> **flylehe said:**
> Thanks!
I man uname, and it's for hardware, so for CPU?
How to check for operating system?
No, the opposite. uname -m tells you if the operating system is 32-bit or 64-bit. It does not tell you if the processor is actually 64-bit or not.

---

### Post by Krupski on 2009-03-06
> **flylehe said:**
> Hi,
I was wondering what are Bash commands for checking if my cpu and OS is 32bit or 64bit?
Thanks!

Type "uname -a"

My server box yields this:

"Linux storage 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 [COLOR="Red"]**x86_64**[/COLOR] GNU/Linux".

Note the red highlight. If the machine were not 64 bit capable, the x86_64 kernel would not have been installed (nor would it work if it WERE somehow installed).

By the way, for all intents and purposes, "OS" and "Kernel" mean the same thing.

Actually, the "kernel" is the engine under the hood and Ubuntu (or whichever Linux you use) is the whole car (which is worthless without the engine).

Make sense?

-- Roger

---

### Post by Reiger on 2009-03-06
For simply seeing what n-bit software you need...
```

getconf LONG_BIT
```

I read that here: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

