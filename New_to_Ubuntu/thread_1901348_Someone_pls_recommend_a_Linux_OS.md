---
title: "Someone pls recommend a Linux OS"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by vignezh on 2011-12-28
I have an old pc that I would like to install linux on. I have so far tried Ubuntu 11.10, Xubuntu 11.10 and Ubuntu 10.04 LTS. My comp has been really slow with both 11.10s. On the other hand, Ubuntu 10.04 LTS worked perfectly, and fast. Problem is my USB wifi adaptor will only get detected in 11.10 and not 10.04. Despite having the installation CD, I couldn't get it working in 10.04 LTS. Could someone please recommend a quicker linux that will detect my USB wifi card. It is a realtek corporation mini USB card. No product number imprinted on the USB. 

See below my pc specs.
```

PCI (sysfs)  
my-linux                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 496MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:dc000000-ddffffff memory:d0000000-d7ffffff
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:dc000000-dcffffff memory:d0000000-d7ffffff memory:dd000000-dd01ffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:de000000-dfffffff memory:20000000-200fffff
           *-network
                description: Ethernet interface
                product: 3c905B 100BaseTX [Cyclone]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 30
                serial: 00:50:04:f9:3f:48
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
                resources: irq:16 ioport:c000(size=128) memory:df000000-df00007f memory:20000000-2001ffff
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:17 memory:df001000-df001fff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:18 memory:df002000-df002fff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16
                resources: irq:19 memory:df003000-df0030ff
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d800(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:dc00(size=256) ioport:e000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@4:1
       logical name: wlan0
       serial: 00:e0:4d:81:81:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.82 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as
```

---

### Post by The Cog on 2011-12-28
I think the problem is the amount of memory - 496M of RAM is not a lot these days. Perhaps Lubuntu would do better - I gather that's the one with lowest memory requirements.

---

### Post by nothingspecial on 2011-12-28
> **The Cog said:**
> I think the problem is the amount of memory - 496M of RAM is not a lot these days. Perhaps Lubuntu would do better - I gather that's the one with lowest memory requirements.

Lubuntu should work well with that amount of ram.

---

### Post by Lars Noodén on 2011-12-28
A third vote for Lubuntu here.  If you want to try a non-Ubuntu distro, then Puppy Linux is small and fast.

---

### Post by flemur13013 on 2011-12-28
AFAIK, Linux mint 9 w/fluxbox is basically ubuntu 10.04, but lighter then (k,l,x)ubuntu. (FWIW, my 10.04 is using 435M with a fancy window mgr and FF w/6 tabs open). You'll probably have the same driver problems, though.

Puppy is easy to try on a CD - I've got it booting from a 256M CD card, and a big chunk of that is the nVidia driver, and it has all the basics.

---

### Post by Lars Noodén on 2011-12-28
Speaking of window managers like Fluxbox, there is also FVWM.  The modded FVWM-crystal package is not only fast, but also very nice.

---

### Post by bluexrider on 2011-12-28
> **The Cog said:**
> I think the problem is the amount of memory - 496M of RAM is not a lot these days. Perhaps Lubuntu would do better - I gather that's the one with lowest memory requirements.
Once you decide on a distro then install zRam and give your PC a boost, works well on low pro PC's

---

### Post by Johnny3 on 2011-12-28
From and old man. I would get some more memory it is so cheap these days. It would pep up your PC a lot.
Happy New Year and God Bless Johnny3 65++

---

### Post by mastablasta on 2011-12-28
perhaps there is something wrong with the graphics card drivers. Xubuntu 11.10 should work well with that amount of ram.

---

