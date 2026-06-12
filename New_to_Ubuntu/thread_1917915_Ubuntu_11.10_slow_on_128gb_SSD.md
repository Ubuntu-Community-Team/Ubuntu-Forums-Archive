---
title: "Ubuntu 11.10 slow on 128gb SSD"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by kmir on 2012-01-30
Dear All,

I installed 11.10 on an m4 128GB Crucial SSD, which I placed in a dual core Dell Dimension E521. I did this hoping that things would be even faster than they are already.

Unfortunately, they are much slower. Ubuntu is quite choppy in that when I click on a program or type something, it will take several seconds to a minute until anything happens. Sometimes nothing happens at all. 

I have searched around in the forum, but it does not seem that someone else has experienced this problem.

Any suggestions? Please!

---

### Post by robgraves on 2012-01-30
What are the other specs on that PC? RAM? CPU? Graphics?

---

### Post by kmir on 2012-01-30
RAM: 2GB,  
CPU: AMd Athlon 64 X2
Graphics: It says "unknown", but I believe it's some NVidia on chip thing. Could that be the problem?

---

### Post by robgraves on 2012-01-30
maybe, are you using the open source or proprietary drivers for the video?

---

### Post by kmir on 2012-01-30
It does say I am using the proprietary driver (NVIDIA acceleerated graphics driver (version 173)

---

### Post by robgraves on 2012-01-30
open up a terminal and type in:
```
lshw
```

then paste the results here

---

### Post by kmir on 2012-01-30
I just had to reboot, and I saw there is an Ubuntu 2D button, and things are a lot faster now!!!

Here is the output from lshw:


miriam-dimension-e521     
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1991MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 6
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:8000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:b000(size=4096) memory:fdc00000-fdcfffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff memory:fb000000-fbffffff memory:80000000-8001ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: ioport:9000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff
        *-network
             description: Ethernet interface
             product: BCM4401-B0 100Base-TX
             vendor: Broadcom Corporation
             physical id: 7
             bus info: pci@0000:04:07.0
             logical name: eth0
             version: 02
             serial: 00:18:8b:5d:cd:ca
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.1.4 latency=64 multicast=yes port=twisted pair speed=10Mbit/s
             resources: irq:19 memory:fdbfe000-fdbfffff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fe024000-fe027fff
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

---

### Post by robgraves on 2012-01-31
i'm personally at a loss as far as what you should do.  Did you have ubuntu functioning well prior to adding the solid state drive? I have no experience with solid states...yet.  But i discovered this: [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/), perhaps you should check this out, otherwise maybe someone else has some insight to your issue.

---

### Post by kmir on 2012-01-31
Before this, I was running the last LT release (10.04 or 10.10) on the same PC, but with a convential HD.

I saw that forum as well, thanks. 
I felt that the issue was so massive, it couldn't just be a tweaking thing - and choosing the 2D Ubuntu, it is working fine. I'm not really into fancy graphics anyways, so the problem has now lost some of its urgency.

Thank you a lot for your help and have a good night!!!

---

### Post by LowSky on 2012-01-31
> **kmir said:**
> RAM: 2GB,  
CPU: AMd Athlon 64 X2
Graphics: It says "unknown", but I believe it's some NVidia on chip thing. Could that be the problem?

> **kmir said:**
> It does say I am using the proprietary driver (NVIDIA acceleerated graphics driver (version 173)

Are you using ACHI mode for your SATA drives? Please say yes. SSD performance can suffer if you do not. 

Also SSD performance relies heavily on aligning the drive correctly when you formatted it.

Open up Disk Utility and  do a read only benchmark. My Mushkin SSD (sandforce SATA2) reads at 285MB/s for example.

---

### Post by mastablasta on 2012-01-31
> **kmir said:**
> I felt that the issue was so massive, it couldn't just be a tweaking thing - and choosing the 2D Ubuntu, it is working fine. 
 
 
this suggest it's a graphics card issue or graphics card drivers issue/bug.

---

