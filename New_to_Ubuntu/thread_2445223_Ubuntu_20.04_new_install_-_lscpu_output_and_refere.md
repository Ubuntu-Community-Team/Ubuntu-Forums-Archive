---
title: "Ubuntu 20.04 new install - lscpu output and references to Vulnerabilities"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by cryptokevin on 2020-06-10
I just changed OS from Windows 10 to Ubuntu 20.04.  

I ran lscpu and noticed the reference to vulnerabilities in output.  

To follow is output i am referencing:

```
root@cyrptokevin:/home/cyrptokevin# lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          8
On-line CPU(s) list:             0-7
Thread(s) per core:              2
Core(s) per socket:              4
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           142
Model name:                      Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz
Stepping:                        11
CPU MHz:                         2500.013
CPU max MHz:                     4600.0000
CPU min MHz:                     400.0000
BogoMIPS:                        3999.93
Virtualization:                  VT-x
L1d cache:                       128 KiB
L1i cache:                       128 KiB
L2 cache:                        1 MiB
L3 cache:                        8 MiB
NUMA node0 CPU(s):               0-7
Vulnerability Itlb multihit:     KVM: Mitigation: Split huge pages
Vulnerability L1tf:              Not affected
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Meltdown:          Not affected
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB conditional, IBRS_FW, STIBP conditional, RSB filling
Vulnerability Srbds:             Mitigation; Microcode
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch
                                 _perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2
                                 apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority 
                                 ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hw
                                 p_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities

```
Is there any reason for concern based on this output?

I found info regarding this issue at [https://askubuntu.com/questions/1248273/lscpu-vulnerabilities](https://askubuntu.com/questions/1248273/lscpu-vulnerabilities), but the link does not specify how to address these issues.

Thanks in advance for your response.

Kevin

---

### Post by wildmanne39 on 2020-06-10
Hello and welcome to the forum cryptokevin.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by cryptokevin on 2020-06-10
thanks for the help.  i am going to read about code tags now

---

### Post by Holger_Gehrke on 2020-06-10
It's a list of known mis-features of various processors (like for example spectre and meltdown) that can be used by programs to either access information to which they should not have access or to gain enhanced privileges. Three of the listed problems don't affect your processor, for all the others there are mitigations included in the kernel which make it hard or even impossible to use them to do anything with them.

Holger

---

