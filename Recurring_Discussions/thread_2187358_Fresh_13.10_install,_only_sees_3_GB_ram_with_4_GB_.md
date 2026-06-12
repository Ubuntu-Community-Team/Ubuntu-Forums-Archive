---
title: "Fresh 13.10 install, only sees 3 GB ram with 4 GB installed"
date: 2013-11-11
forum: Recurring Discussions
---

### Post by gowen-0 on 2013-11-11
Short version:

1) I installed Ubuntu 13.10 on a laptop with 2 GB (2x1GB) memory. 
2) Then I upgraded the laptop to have 4 GB (2x2GB) memory.
3) Ubuntu only sees 3 GB, even though all my research suggests that PAE should take effect by default.
4) I've read Ubuntu detects high RAM at install time, since I installed with 2 GB and then inserted more memory after the fact, is there anything I can or need to do to kick it in the rump and make it recognize the memory?

Any help is appreciated.  TYVM!
gowen


Long version and boring details:

The CPU is 32-bit, which means that PAE is required to support more than 3 GB of memory:

```

root@golap:~# uname -a
Linux golap 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 17:26:33 UTC 2013 i686 i686 i686 GNU/Linux
root@golap:~# egrep "model name|address" /proc/cpuinfo 
model name    : Genuine Intel(R) CPU           T2400  @ 1.83GHz
address sizes    : 32 bits physical, 32 bits virtual
model name    : Genuine Intel(R) CPU           T2400  @ 1.83GHz
address sizes    : 32 bits physical, 32 bits virtual
root@golap:~# 

```


The CPU supports PAE:

```

root@golap:~# grep -w pae /proc/cpuinfo
flags        : fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm
flags        : fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm
root@golap:~# 

```

The Kernel supports PAE:

```

root@golap:~# grep PAE /boot/config-3.11.0-13-generic 
CONFIG_X86_PAE=[B]y
[/B]root@golap:~# 

```

However, the OS only reports 3 GB of memory:

```

root@golap:~# dmesg | grep Memory:
[    0.000000] Memory: 3076192K/3135928K available (6352K kernel code, 607K rwdata, 2640K rodata, 880K init, 908K bss, 59736K reserved, 2222920K highmem)
root@golap:~# free -m
             total       used       free     shared    buffers     cached
Mem:          3021       1913       1107          0        101       1043
-/+ buffers/cache:        768       2252
Swap:         3905          0       3905
root@golap:~# 

```

---

### Post by mörgæs on 2013-11-12
Welcome to the fora. Your post has been moved to Recurring.

Regarding the root user:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zKhtdyX on 2013-11-21
Does your pc support 4gb ram according to its specs?

---

