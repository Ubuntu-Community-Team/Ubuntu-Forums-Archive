---
title: "in ubuntu, my pc support virtualization technology?"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by edsh on 2012-08-10
HI!
I give the command ```
cat /proc/cpuinfo
```          to look for if my pc support virtualization technologyes...the result it is:
```
[FONT=Courier New]pc1@ubuntu:~$ cat /proc cpuinfo
cat: /proc: Is a directory
cat: cpuinfo: No such file or directory
pc1@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping    : 4
cpu MHz        : 3391.285
cache size    : 2048 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm  constant_tsc up pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr  pdcm lahf_lm
bogomips    : 6782.57
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:[/FONT]

``` I can not understand if VT is active or not ....can anyone say me if its or nor not????
thanks
best regards edsh

---

### Post by Paqman on 2012-08-10
The Intel website says not all Pentium4's do support it. What Google says is that your processor has have the flag "vmx", which it doesn't. Looks like you're out of luck.

---

