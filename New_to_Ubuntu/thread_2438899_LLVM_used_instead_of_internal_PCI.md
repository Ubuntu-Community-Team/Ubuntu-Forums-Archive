---
title: "LLVM used instead of internal PCI"
date: 2020-03-20
forum: New to Ubuntu
---

### Post by dingus-khan on 2020-03-20
Hello all,

Relative newbie here, about 3 weeks of linux experience.  Trying to set up and install a linux system on a chromebook only through the terminal so I can better understand the system, but I have hit a wall with the video driver.  For the life of me I cant get the laptop to see the "00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)" as a "Driver.  I think I've installed all the intel drivers I needed but obviously something is amiss.  I'd be happy to provide any other info, and for now to run "Civilization 4" through wine with PCI video acceleration (OpenGL) if that's possible.

I'm totally ignorant of hardware, so perhaps this is all how its supposed to be, but I'm under the impression that the PCI card can be used to handle the hardware acceleration / video duties, but has to be recognized instead of the llmvpipe.

An interesting note, ubuntu-devices drivers hangs, and then another prompt shows up.  Pretty much anything with "grep drivers does the same"
Some info:

Ubuntu 18.04
Mesa

```
$ LIBGL_DEBUG=verbose glxgears
libGL: screen 0 does not appear to be DRI2 capable
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/dingus/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/dingus/.drirc: No such file or directory.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 4930 requests (4930 known processed) with 0 events remaining.

```

```
lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:15.0 DMA controller: Intel Corporation 8 Series Low Power Sub-System DMA (rev 04)
00:15.1 Serial bus controller [0c80]: Intel Corporation 8 Series I2C Controller #0 (rev 04)
00:15.2 Serial bus controller [0c80]: Intel Corporation 8 Series I2C Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
01:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)

```

```
glxinfo | grep Device
    Device: llvmpipe (LLVM 9.0.0, 128 bits) (0xffffffff)

```

```
(xenial)dingus@localhost:~$ lscpu
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              2
On-line CPU(s) list: 0,1
Thread(s) per core:  1
Core(s) per socket:  2
Socket(s):           1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               69
Model name:          Intel(R) Celeron(R) 2955U @ 1.40GHz
Stepping:            1
CPU MHz:             1400.000
CPU max MHz:         1400.0000
CPU min MHz:         800.0000
BogoMIPS:            2793.60
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            2048K
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer xsave rdrand lahf_lm abm arat epb xsaveopt pln pts dtherm invpcid_single tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust erms invpcid

```

---

