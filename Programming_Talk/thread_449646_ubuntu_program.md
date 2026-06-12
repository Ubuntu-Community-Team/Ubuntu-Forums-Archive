---
title: "ubuntu program"
date: 2007-05-20
forum: Programming Talk
---

### Post by androssofer on 2007-05-20
does anyone know if ubuntu is designed to take full of advantage of multi core processors? cus alot of programs on windows arent, only ones that r used on macs also like dreamweaver and photoshop really take advantage of it.was just wondering if ubuntu does

---

### Post by hartz on 2007-05-20
Linux supports:
Scheduling processes and threads across multiple processor cores
Multi-threaded processes

This is true if you have SMP (Symmetric Multi-processing) turned on in your kernel.  

The default in the kernel that ships with Feisty is SMP enabled.  At least I was under this impression as the SMP specific packages have been removed - this is implied by the description on the smp-specific kernel packages which says the packages are obsoleted and depends on the generic kernel package.  However I just checked my kernel config file and it indicates:

```
config-2.6.20-15-386:CONFIG_BROKEN_ON_SMP=y
config-2.6.20-15-386:# CONFIG_SMP is not set
config-2.6.20-15-386:# CONFIG_X86_BIGSMP is not set
config-2.6.20-15-386:CONFIG_X86_FIND_SMP_CONFIG=y
```

You can check whether your kernel has got SMP support enabled.  Enter this command in a terminal:

```
cat /proc/cpuinfo
```

You should see info about each of your cpus/processors/cores.

In real terms, SMP support means that:
- if you have multiple programs that want to run simultaneously, then they can and will be scheduled to run on separate CPU cores.
- if you have program which was written to be able to support multi-threaded execution, then the separate threads will run on any available cores simultaneously.  This support must be specifically programmed into the program.
- Since about 2001 some time, the Linux kernel itself was made fully multi-threaded.  This means that the kernel itself will also utilize the extra cores.  (SMP support for user-space processes/threads was provided long before that though)

---

### Post by androssofer on 2007-05-20
thanks, wasnt expecting some1 to b quite so helpful hahaha.

---

