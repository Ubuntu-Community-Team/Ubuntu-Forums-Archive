---
title: "kernel panic"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by IYII3r41n on 2013-03-26
I ran an update this morning on Ubuntu 13.04. It updated to kernel version 
```
linux-image-3.8.0-14-generic - Linux kernel image for version 3.8.0 on 64 bit x86 SMP
```

When I started my machine it went to the Kernel panic freeze...
[FONT=arial]```
[/FONT][COLOR=#000000][FONT=verdana]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0[/FONT][/COLOR][COLOR=#000000][FONT=verdana])[/FONT][/COLOR][FONT=arial]
```

I restarted into 3.8.0-13-generic and all is fine. 

How do I fix the error? 

here is some info about my machine
[/FONT]Dell Latitude E6510
[FONT=arial]intel i5[/FONT][FONT=arial]

[/FONT]```
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Release:	13.04

```

```
free -m
             total       used       free     shared    buffers     cached
Mem:          3876       2883        993          0        505        877
-/+ buffers/cache:       1500       2376
Swap:         4016          0       4016



```


```
cat /proc/cpuinfoprocessor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
stepping	: 2
microcode	: 0xc
cpu MHz		: 1199.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4787.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
stepping	: 2
microcode	: 0xc
cpu MHz		: 1199.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4787.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
stepping	: 2
microcode	: 0xc
cpu MHz		: 1199.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4787.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
stepping	: 2
microcode	: 0xc
cpu MHz		: 1199.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4787.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:



```


From image 3.8.0-13 I tried apt-get update, upgrade, dist-upgrade, dpkg --configure -a. I thought about trying this ```
sudo apt-get install linux-image -3.8.0-14
``` but I thought I would ask around first. 
anyone have any suggestions?

Thanks

---

