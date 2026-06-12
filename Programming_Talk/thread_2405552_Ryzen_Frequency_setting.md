---
title: "Ryzen Frequency setting"
date: 2018-11-07
forum: Programming Talk
---

### Post by kkanungo17 on 2018-11-07
[FONT=trebuchet ms]Hi,

I'm trying to set the frequencies for an AMD EPYC 7551 processor for an experiment. The lscpu result is:
[/FONT][SIZE=2]
[FONT=trebuchet ms]Architecture:        x86_64[/FONT][/SIZE]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU op-mode(s):      32-bit, 64-bit[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Byte Order:          Little Endian[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU(s):              64[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]On-line CPU(s) list: 0-63[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Thread(s) per core:  2[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Core(s) per socket:  32[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Socket(s):           1[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]NUMA node(s):        4[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Vendor ID:           AuthenticAMD[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU family:          23[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Model:               1[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Model name:          AMD EPYC 7551 32-Core Processor[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Stepping:            2[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU MHz:             2396.913[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU max MHz:         2000.0000[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]CPU min MHz:         1200.0000[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]BogoMIPS:            3999.32[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Virtualization:      AMD-V[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]L1d cache:           32K[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]L1i cache:           64K[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]L2 cache:            512K[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]L3 cache:            8192K[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]NUMA node0 CPU(s):   0-7,32-39[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]NUMA node1 CPU(s):   8-15,40-47[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]NUMA node2 CPU(s):   16-23,48-55[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]NUMA node3 CPU(s):   24-31,56-63[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2] [/SIZE][/FONT][FONT=trebuchet ms][SIZE=2]Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid amd_dcm aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca[/SIZE][/FONT]
[FONT=trebuchet ms][SIZE=2]
As you can see the current frequency reported is above the max possible frequency, and even if the [/SIZE][/FONT][SIZE=2][FONT=trebuchet ms]powersave[/FONT][/SIZE][FONT=trebuchet ms][SIZE=2] governor is set, the frequency then is none of the frequencies mentioned in scaling_available_frequencies. It doesn't seem to respond to scaling_setspeed either, when using userspace governor. Any ideas as to how to manually manipulate frequencies?
[/SIZE][/FONT]

---

