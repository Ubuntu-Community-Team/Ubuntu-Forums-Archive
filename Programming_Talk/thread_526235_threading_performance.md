---
title: "threading performance"
date: 2007-08-15
forum: Programming Talk
---

### Post by agb32 on 2007-08-15
Hi,

I have a dual quad core xeon machine, with Ubuntu on it.

I'm trying to use pthreads to create a multi-threaded program, but find that it doesn't scale well.

There is performance improvement between 1-2 threads, but then not much after this.  

I've tried compiling different kernels, but nothing seems to help.

Any suggestions?

I know the code isn't at fault, because the same code runs fine under OS X (ie using 8 threads is almost 8 times faster than using 1 thread).  

Many thanks...

---

### Post by aks44 on 2007-08-15
Looks like the kernel doesn't correctly recognize your CPUs.

What is the result of
```
cat /proc/cpuinfo
```?

---

### Post by agb32 on 2007-08-15
All 8 processors seem to be there...

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5989.15
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.02
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.12
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 1
siblings        : 4
core id         : 0
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.13
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.09
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 1
siblings        : 4
core id         : 1
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.13
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 1
siblings        : 4
core id         : 3
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.21
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU           X5365  @ 3.00GHz
stepping        : 7
cpu MHz         : 2992.497
cache size      : 4096 KB
physical id     : 1
siblings        : 4
core id         : 2
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 5985.14
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by shad0w_walker on 2007-08-15
Are you sure the task your trying to do will scale decently? It could be that the problem is just some that won't be threaded due to its nature.

---

### Post by agb32 on 2007-08-15
It scales fine on OS X.

All it is doing is taking the cos() of a large number of doubles...

Thanks...

---

### Post by thk on 2007-08-15
> **agb32 said:**
> It scales fine on OS X.

All it is doing is taking the cos() of a large number of doubles...

Thanks...

OS X on the same hardware or different hardware?

Could it be a problem with the math library? One thing to try is to omit any external functions and only use built-in operators for testing. At least then you can localize the problem within your code.

Intel compilers and math libraries should scale properly if the code is not a problem.

---

### Post by psusi on 2007-08-15
I think the four cores share a single FPU.  Try doing integer math instead.

---

### Post by agb32 on 2007-08-16
OS X tests are using the same hardware (Mac Pro).

If there is only 1 FPU, then I wouldn't expect the OS X version to scale well.

Have done tests using integer operations, and still doesn't scale well.  Infact, hardly scales at all...

---

### Post by aks44 on 2007-08-16
> **agb32 said:**
> Have done tests using integer operations, and still doesn't scale well.  Infact, hardly scales at all...

Damn.


From the top of my head I have those suggestions:

- The bottleneck may be a system call that would be serialized under the hood. (wild guess though)

- Can you saturate your 8 CPUs (all running at 100%) with some other application(s)?

- I guess it would be worth it to write a sample application using fork() instead of pthreads, to test the previous suggestion, and see if it scales.


Sorry I can't think of anything more right now.

---

### Post by psusi on 2007-08-16
Are you making any syscalls or is it just a tight infinite math loop in each thread?  What is the cpu utilization while this is running?

---

### Post by slavik on 2007-08-16
forking is not very different than pthreads in linux, threads can migrate through CPUs ... each process/thread is a task and tasks are more like processes than threads.

---

### Post by aks44 on 2007-08-17
> **slavik said:**
> forking is not very different than pthreads in linux, threads can migrate through CPUs ... each process/thread is a task and tasks are more like processes than threads.

Theorically, yes. I don't know how pthreads are actually implemented under the hood on Linux, but from the little I know it seems to be an additional layer over the kernel rather than being fully part of it (please correct me if I'm wrong).

Clearly the OP's hardware is not at fault. Apparently his(her) code isn't at fault either since (s)he mentionned that the same code scales well on OSX.

As far as I can think of, this leaves us with two options:
- either the kernel itself has problems using the OP's hardware to its full extent (although it correctly detects it),
- or the problem lies at the pthreads layer.

So I made the fork() suggestion in order to (in)validate the second option.

Granted, the OP's problem could be caused by a system call which is serialized on Linux and executed concurrently on OSX, but this seems rather unlikely when you think of it.


Do you think it makes sense or am I too uninformed yet about Linux's internals? (I only started Linux development 3 months ago, so I may well be wrong)

---

