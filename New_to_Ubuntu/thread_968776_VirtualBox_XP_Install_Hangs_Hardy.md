---
title: "VirtualBox XP Install Hangs Hardy"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jmwjer on 2008-11-02
I'm trying to install XP or Vista on my Hardy system through Sun VirtualBox.  It keeps hanging.  Mouse starts moving really slow then just stops responding.  The disk thrashes around for 8 hours or more before I give up.  I've tried every combination of settings for ACPI and VT.  I'm running Hardy Heron 8.04 on a Dell Inspiron 1525 (shipped with Ubuntu).

I tried updating the BIOS from A11 thinking it might not support Windows.  Nothing more current available.  I also tried to stop KVM (Synaptic knows of nothing named KVM installed, not is there anything in the BIOS settings).  I also tried all combinations of HD size and RAM settings.  No luck.  Dell won't help me with even the BIOS since I bought it with Ubuntu.  I really need Windows for an application that Wine won't support.  Anyone have any thoughts?  I'd really appreciate ANY help you can offer!

---

### Post by jbrown96 on 2008-11-03
Could you give us some info on your system? post the output of these commands ```
lspci
``` ```
cat /proc/meminfo
``` ```
cat /proc/cpuinfo
``` Do these in a terminal (apps-->accessories-->terminal)

---

### Post by jmwjer on 2008-11-03
Hey thanks for the help!

jer@dars-pushcar:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
jer@dars-pushcar:~$ cat /proc/meminfo
MemTotal:      1019448 kB
MemFree:         72348 kB
Buffers:         65324 kB
Cached:         399928 kB
SwapCached:          0 kB
Active:         544184 kB
Inactive:       263460 kB
SwapTotal:     2980016 kB
SwapFree:      2980016 kB
Dirty:              12 kB
Writeback:           0 kB
AnonPages:      342420 kB
Mapped:          63352 kB
Slab:            36628 kB
SReclaimable:    21504 kB
SUnreclaim:      15124 kB
PageTables:      15628 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   3489740 kB
Committed_AS:   834912 kB
VmallocTotal: 34359738367 kB
VmallocUsed:      9032 kB
VmallocChunk: 34359728763 kB
jer@dars-pushcar:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3195.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3191.87
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

jer@dars-pushcar:~$

---

### Post by jbrown96 on 2008-11-03
Looks to me that you're light on RAM. Do you only have 1GB? That's probably not enough to run Vista at all and XP would be iffy. How much RAM and VRAM are you giving to Windows? I'd seriously look at getting at least another GB. You can pick up 2GB sticks on Newegg for around $25 [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010260381%201309121116&name=2GB]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010260381%201309121116&name=2GB"). Drop in a couple of those and switch to 64-bit and you won't have any problems with VMs

---

### Post by jmwjer on 2008-11-06
Wow.  Total bone head move on my part.  Thanks!  I didn't even check the memory available.  VBox allowed me to partition 4 GB so I just went with it.  Thanks for catching this and helping me out.  I got the RAM at Frys for 1.5x the New Egg price (I'm too impatient to wait for shipping) and it works great.  Thanks again JBrown!!!

---

