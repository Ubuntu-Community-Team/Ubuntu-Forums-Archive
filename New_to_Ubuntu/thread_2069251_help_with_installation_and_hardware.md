---
title: "help with installation and hardware"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by timobis on 2012-10-10
I have a new work computer and have been given the option to use Ubuntu, I have used it a small amount before so know my way around however I am having some issues trying to run it with the hardware that I currently have.

When I boot the PC I just get a black screen and nothing changes....

I installed Ubuntu via my laptop at home as I don't have much time whilst at work...

Does anyone know of any issues that may occur... I read up online somewhere and it said that if I run lshw that I would be able to view the installed hardware. The only way I am able to do this is by booting Ubuntu via the OS disk.

Is there any chance someone can have a look at my hardware and see if they can give me any pointers or if anyone knows of any issues that have arisen with any of the hardware that I currently utilize.

Below is the output from the terminal:

ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3427MiB
     *-cpu
          product: AMD A6-3650 APU with Radeon(tm) HD Graphics
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter cpufreq
     *-pci:0
          description: Host bridge
          product: Family 12h Processor Root Complex
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: BeaverCreek [Radeon HD 6530D]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:60 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:62 memory:feb44000-feb47fff
        *-usb:0
             description: USB controller
             product: Hudson USB XHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:feb4a000-feb4bfff
        *-usb:1
             description: USB controller
             product: Hudson USB XHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:feb48000-feb49fff
        *-storage
             description: SATA controller
             product: Hudson SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f190(size=8) ioport:f180(size=4) ioport:f170(size=8) ioport:f160(size=4) ioport:f150(size=16) memory:feb51000-feb517ff
        *-usb:2
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb50000-feb50fff
        *-usb:3
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb4f000-feb4f0ff
        *-usb:4
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb4e000-feb4efff
        *-usb:5
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb4d000-feb4d0ff
        *-serial
             description: SMBus
             product: Hudson SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: Hudson IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f100(size=16)
        *-multimedia:1
             description: Audio device
             product: Hudson Azalia Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb40000-feb43fff
        *-isa
             description: ISA bridge
             product: Hudson LPC Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Hudson PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:6
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb4c000-feb4cfff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: c8:60:00:4f:86:9e
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.25.148 latency=0 multicast=yes port=MII speed=100Mbit/s
                resources: irq:61 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:fea00000-feafffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fea00000-fea07fff
        *-pci:4
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:44 ioport:d050(size=8) ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4) ioport:d000(size=32) memory:fe900000-fe9001ff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage



Thanks in advance for any replies and much appreciated to anyone who can offer even the smallest amount of help :)

---

### Post by 2F4U on 2012-10-10
I would suggest that you try to boot with the nomodeset option:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

This should enable you to boot into the liveCD and perform the installation. Just remember that this option won't be carried over to the installed system, so you would have to apply it again when you boot from the installed system.

I am wondering to what machine the hardware specs belong that you have posted. I thought that you would be unable to boot into Ubuntu.

---

