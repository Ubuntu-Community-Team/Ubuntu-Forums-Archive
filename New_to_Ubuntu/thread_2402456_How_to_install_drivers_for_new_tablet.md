---
title: "How to install drivers for new tablet ?"
date: 2018-09-30
forum: New to Ubuntu
---

### Post by menido on 2018-09-30
Hello 

I have tablet tbook11 
-> [https://www.gearbest.com/tablet-pcs/pp_328162.html](https://www.gearbest.com/tablet-pcs/pp_328162.html)

I dont how to install drivers for:

1. Bluetooth
2. Touch screen 
3. Sound (with antegros distro work but under ubuntu dont ;/ )

Can u help me guys ?

---

### Post by TheFu on 2018-09-30
You'll need to determine the chips providing those capabilities, then search for linux drivers for those chips.

---

### Post by menido on 2018-09-30
Chipset Inter Cherry Trail

---

### Post by TheFu on 2018-09-30
> **menido said:**
> Chipset Inter Cherry Trail

It will need to be much more detailed than that.  Think model numbers and versions.  lspci, lsusb, lshw are the tools to gather the information.

---

### Post by menido on 2018-10-18
lshw

```
  description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3868MiB
     *-cpu
          product: Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1591MHz
          capacity: 1840MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb pti tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
     *-pci
          description: Host bridge
          product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 22
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:118 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:91000000-913fffff
        *-generic:0
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: irq:20 memory:9183c000-9183cfff
        *-generic:1
             description: Signal processing controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:120 memory:9183b000-9183bfff
        *-usb
             description: USB controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:116 memory:91800000-9180ffff
        *-generic:2
             description: Encryption controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:121 memory:91700000-917fffff memory:91600000-916fffff
        *-isa
             description: ISA bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0

       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bs ip=192.168.123.123 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


```

lspci

```
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 22)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 22)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 22)
00:0a.0 Non-VGA unclassified device: Intel Corporation Device 22d8 (rev 22)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 22)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 22)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 22)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 22)


```

lsusb

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 258a:0001  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by Claus7 on 2018-10-19
Hello,

just a clarification: have you installed ubuntu in that tablet and you are seeking those drivers in order to make it work?

Regards!

---

### Post by menido on 2018-10-19
> **Claus7 said:**
> Hello,

just a clarification: have you installed ubuntu in that tablet and you are seeking those drivers in order to make it work?

Regards!

Yes, I installed


Everything works except**bluetooth**** and touchscreen ..**

---

### Post by Claus7 on 2018-10-19
Hello,

concerning the touchscreen, the lsusb output does not seem to detect it. How about the steps provided here: [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen) under the Serial connection? If you try these commands can you make your touchscreen work?

Regards!

---

