---
title: "C++: different CPU compiling"
date: 2011-07-05
forum: Programming Talk
---

### Post by erotavlas on 2011-07-05
Hi all,
I have a question about compiling process. I have my system where I'm developing C++ code under Ubuntu x64, the my CPU has not much computing power. So I would like to run my program in a server where the CPU is different from the my. Can I compile the code in my system and execute it onto the server system without loss of performances? i.e. How can I tell to GCC compiler to use all the features of the CPU server?

Thank you

---

### Post by Zugzwang on 2011-07-05
Step 1: Find out which CPU your server has and whether it also runs an x64-version of Linux.

Step 2: Compile your executable accordingly. Use the "-static" flag for the linker to avoid having to copy all kinds of libraries to the server. Use the [mtune]("http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html") flag for the compiler to let gcc/g++ optimize towards the specific architecture. If your server runs a 32-bit version of Linux, add the "-m32" flag when compiling and linking to produce 32-bit code. Install the "g++-multilib" package in this case.

---

### Post by erotavlas on 2011-07-05
> **Zugzwang said:**
> Step 1: Find out which CPU your server has and whether it also runs an x64-version of Linux.

Step 2: Compile your executable accordingly. Use the "-static" flag for the linker to avoid having to copy all kinds of libraries to the server. Use the [mtune]("http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html") flag for the compiler to let gcc/g++ optimize towards the specific architecture. If your server runs a 32-bit version of Linux, add the "-m32" flag when compiling and linking to produce 32-bit code. Install the "g++-multilib" package in this case.


My server has the following CPU and runs Ubuntu 11.04 x64 server edition.

```

cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 9
model name    : AMD Opteron(tm) Processor 6168
stepping    : 1
cpu MHz        : 1900.000
cache size    : 512 KB
physical id    : 0
siblings    : 12
core id        : 0
cpu cores    : 12
apicid        : 16
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save pausefilter
bogomips    : 3800.25
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

I'm using Netbeans 7 as IDE. It uses a makefile to compile the project, so can I use it? If yes, where can I set the parameters?

Thank you

---

