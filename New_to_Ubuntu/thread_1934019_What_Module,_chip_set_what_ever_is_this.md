---
title: "What Module, chip set what ever is this?"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by suomalainen on 2012-03-01
Ubunteros,

I have this card in my laptop that I don't know what it is. Online research also yielded negative results.

So I took it out to learn what I could. The only identifying markings on it are those as seen in the attached picture.

Anyone have any idea what we are looking at here??????

I'm asking the question here so I know what I have and then any software the device is capable of supporting.

Thanks to all.... 

Suomalainen

---

### Post by Jeanke on 2012-03-01
Hi,

What brand and model is your laptop?

---

### Post by egalvan on 2012-03-01
how about a pix of the other side?

---

### Post by suomalainen on 2012-03-01
Ubunteros,

I have a Panasonic Toughbook Model CF-29 running Ubuntu 11.10.

It appears that this may be a GPRS modem as a GSM SIM card fits into a slot on the side of the machine. I tried it worked.

This being the case, how can I get Ubuntu to recognize this modem?

Thank you very much.

---

### Post by suomalainen on 2012-03-02
Is there a command I can run to determine the brand of gsm module this is and then the type of driver I need to make it work?

---

### Post by suomalainen on 2012-03-03
bump

---

### Post by mastablasta on 2012-03-03
lshw

lists all recognised hardware.

lspci 

lists all PCI connected devices

---

### Post by Paqman on 2012-03-03
> **suomalainen said:**
> 
This being the case, how can I get Ubuntu to recognize this modem?


It might have done so already. Stick your SIM in, open up Network Manager and see if you can create a new mobile connection.

---

### Post by suomalainen on 2012-03-03
Actually, the first thing I did do was insert my sim into the module to see if a connection could be made but no luck.....

Perhaps the info listed below from the terminal commands recently offered proves that this indeed is the case.....

```

WARNING: you should run this program as super-user.
john-cf-29ctkghgs         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1200MHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.9.5
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:9 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:9 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:30000000-37ffffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00202010-b0020200f irq:9 memory:e0202000-e0202fff ioport:3400(size=256) ioport:3800(size=256) memory:30000000-33ffffff memory:3c000000-3fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603010-b0060300f irq:9 memory:e0203000-e0203fff ioport:3c00(size=256) ioport:1400(size=256) memory:34000000-37ffffff memory:40000000-43ffffff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: eth1
                version: 04
                serial: 00:04:23:92:6f:bb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.43.209 latency=32 maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
                resources: irq:9 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:01:02.0
                logical name: eth0
                version: 10
                serial: 00:80:45:45:d4:35
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:9 ioport:3000(size=256) memory:e0201000-e02010ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:38000000-380003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1860(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:9 memory:3c000000-3c000fff
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@0000:02:00.1
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:9 memory:3c001000-3c001fff
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@0000:02:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=68 maxlatency=34 mingnt=16
          resources: irq:9 memory:3c002000-3c0020ff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
john@john-CF-29CTKGHGS:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 USB Controller: NEC Corporation USB (rev 43)
02:00.1 USB Controller: NEC Corporation USB (rev 43)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

---

### Post by suomalainen on 2012-03-04
Bump....

---

### Post by westie457 on 2012-03-04
Hello, cannot see anything obvious in 'lspci', maybe it is a rare usb device hard-wired onto the mobo.

Stick the sim card in again and run the previous commands and ```
lsusb
```

This time when you post the results could you put them in [ code] [/code] tags please.

---

### Post by suomalainen on 2012-03-05
@ westie457

Here is the data you requested.

When I ran these commands SIM card was in slot. I was connected to LAN via cable connection. 4 port USB 2.0 PCMCIA card was in slot with Logitech wireless mouse working.

Thanks for your support.


LSUSB =

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

```

LSPCI =

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 USB Controller: NEC Corporation USB (rev 43)
02:00.1 USB Controller: NEC Corporation USB (rev 43)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```

LSHW=

```
  description: Notebook
    version: 001
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=00000000-0000-1000-8000-00804545D435
  *-core
       description: Motherboard
       product: CF29-1
       vendor: Matsushita Electric Industrial Co.,Ltd.
       physical id: 0
       version: 001
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies K.K.
          physical id: 0
          version: V1.00L10
          date: 08/01/2003
          size: 124KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1200MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: IC1
          size: 600MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          capacity: 1GiB
        *-bank:0
             description: TSOP DDR Synchronous
             physical id: 0
             slot: Onboard
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: DIMM
             size: 512MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 1e
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: TSOP FLASH Non-volatile
             physical id: 0
             slot: Flash ROM
             size: 512KiB
             width: 8 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:9 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:9 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:30000000-37ffffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00202010-b0020200f irq:9 memory:e0202000-e0202fff ioport:3400(size=256) ioport:3800(size=256) memory:30000000-33ffffff memory:3c000000-3fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603010-b0060300f irq:9 memory:e0203000-e0203fff ioport:3c00(size=256) ioport:1400(size=256) memory:34000000-37ffffff memory:40000000-43ffffff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: eth1
                version: 04
                serial: 00:04:23:92:6f:bb
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
                resources: irq:9 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:01:02.0
                logical name: eth0
                version: 10
                serial: 00:80:45:45:d4:35
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.8 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:9 ioport:3000(size=256) memory:e0201000-e02010ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:38000000-380003ff
           *-disk
                description: ATA Disk
                product: HITACHI_DK23EA-4
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00K3
                serial: PP8841
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00010eff
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 8e34497b-5d39-468c-a80a-187eb1451cf4
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-02-29 14:05:02 filesystem=ext4 lastmountpoint=/ modified=2012-03-02 13:01:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-03-05 09:00:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 757MiB
                   capacity: 757MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 757MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: UJDA340
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.50
                serial: [
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1860(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 3
          bus info: pci@0000:02:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:9 memory:3c000000-3c000fff
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@0000:02:00.1
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:9 memory:3c001000-3c001fff
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@0000:02:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=68 maxlatency=34 mingnt=16
          resources: irq:9 memory:3c002000-3c0020ff
  *-battery:0
       description: Lithium Ion Battery
       product: CF-VZSU29
       vendor: Panasonic
       physical id: 1
       slot: in the front,left-hand side
       capacity: 73260mWh
       configuration: voltage=11.1V
  *-battery:1
       description: Lithium Ion Battery
       vendor: Panasonic
       physical id: 2
       slot: left-hand side

```

---

### Post by suomalainen on 2012-03-05
I just found this interesting piece of info at:

[http://forum.notebookreview.com/panasonic/214029-official-panasonic-cf-29-toughbook-thread-41.html]("http://forum.notebookreview.com/panasonic/214029-official-panasonic-cf-29-toughbook-thread-41.html")


> Thanks for the pointers. I forgot to mention that the switch on the left stopped working about a week ago!? Maybe something i've messed with. The device manager shows a Siemens AG WM USB modem but when i look in the properties it says "device cannot start (code10)", probably to do with the switch not working. Apart from a dodgy switch is there anything else which could have stopped this? Everything else is working spot on.

So it appears we are looking for a USB device?

---

### Post by westie457 on 2012-03-05
Hello 

I take it that you have been following the advice about turning the device on in the BIOS in the link you posted and checking any hardware switches on the case.

The only other piece of help I have been able to find is here [http://people.csail.mit.edu/lfgs/ict4dlab/mitsp716lab/sms.html](http://people.csail.mit.edu/lfgs/ict4dlab/mitsp716lab/sms.html)

Unfortunately it is so far beyond my knowledge and capabilities I do not know where to begin to implement it.

Sorry that I can be of no further help with this.

Hopefully someone who is more capable than me will find this thread and be able to help you.

---

### Post by suomalainen on 2012-03-05
Ubunteros,

I believe I'm getting closer to getting this GPRS modem to work but it's still one royal pain in the butt!

I found this link:

[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/]("http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/")

Easy stuff first. I installed "Ndiswrapper".

Then I wenting hunting for the drivers and found this:

[http://www.onelasttrip.net/2011/03/toughbook-cf-29-modem/]("http://www.onelasttrip.net/2011/03/toughbook-cf-29-modem/")

Man..... This guy had same experience as me ! Anyway, based on the info contained in this link and doing some searches as per MC45, MC46 & MC75 images, I confirmed that I got the MC-45 modem.

The driver for the MC45 is provided in the above link. However, you can find it here too:

[http://www.toughbookdrivers.com/drivers/cf-29/index.php?dir=CF-29%20MK1/]("http://www.toughbookdrivers.com/drivers/cf-29/index.php?dir=CF-29%20MK1/")

BUT this is for MC46 which is for North American.

I downloaded both versions because the problem I'm about to outline was same for both!

According to Ndiswrapper, after file extraction I'm suppose to see a inf file. This is not the case!

The North AMerican drive page states:

> Checknet Software for use with the Siemens MC75 modems only. Install by running Setup.exe. After installation‚ modem inf file is copied in c:\program files\panasonic\checknet\modem directory. For Windows 2000, XP. 


So, should I just install to XP and then copy the .inf file over to Ubuntu?

Or is there some other extraction tool I can use in Ubuntu to get the inf file I need?

Thanks for your support and suggestions!

---

### Post by suomalainen on 2012-03-05
Well this isn't gonna work. I just tried to install the Windows XP drivers onto another laptop where I have XP running and as you can see from the attached pic. No can do....

The Panasonic laptop is running Ubuntu and I don't have the XP disks for it.

Anyone got any ideas what I can try next?

---

### Post by westie457 on 2012-03-05
Hello again suomalainen,

purely as an experiment I have downloaded the driver from the link you posted and tried running it under 'Wine' on an Acer laptop. What a surprise, the setup.exe file ran with no errors or warnings about needing to run on a Panasonic machine only. So then I tried installing the .inf file with ndiswrapper and it failed -not surprisingly- with 'invalid driver'. It might work properly with your Toughbook.

---

### Post by suomalainen on 2012-03-06
@ westie457,

I believe that you got as far as you did because you were using the wrong zip file. The zip for MC46 is the North American version. As the first 2 pictures illustrate, I could install the software under WINE but then the inf file failed under Ndiswrapper. Not that it would work anyway, because again, it's wrong version.

The MC45 driver (European version) didn't get out of the gate and produced exactly the same error message as it did when attempted in a native windows xp environment.

WINE has been installed onto my Panasonic CF-29.So it's interesting to read the error messages.

None the less, thank you very much for your support and interest in helping me get this up and running. Much Appreciated!!!!

Suomalainen

---

### Post by westie457 on 2012-03-06
Have you tried this site [http://pc-dl.panasonic.co.jp/dl/search?dc%5B%5D=002001003](http://pc-dl.panasonic.co.jp/dl/search?dc%5B%5D=002001003) using the exact model number. Using the generic id CF-29 produces over 4000 network drivers ranging from Windows 2000 to Windows 7

---

### Post by suomalainen on 2012-03-06
Thanks again but no can do.

Keep getting the can't install because it's not a Panasonic laptop msg...

Funny too cause it is a Panasonic!!!!

---

### Post by suomalainen on 2012-03-07
I setup WVDIAL and created the .wvdialrc file. I then copied it to /home/john .wvfolder.

Because I originally created this file using sudo gedit the file became locked. After rebooting file status did not change. See attached pic. Trying wvdial produced no results as number username and pw could not be found.

I went into /john folder copied .wvdialrc file to desk top and "lock" status disappeared. Rebooted. Still same status as shown in pics.

My belief is that the WVDIAL program is not seeing the GPRS sled I have installed.

HOwever, the .wvdial file was created to my knowledge correctly.

a. I do not have a PIN request set up on my SIM card.
b. APN is internet
c. number to dial is *99#
d. MY network does not use user name
e. My network does not use password

---

### Post by suomalainen on 2012-03-08
Anyone know a good way to see if Ubuntu 11.10 is seeing my GPRS sled? It's suppose to be using a Siemens MC45 module.

Thanks.

---

### Post by lkraemer on 2012-03-08
A search of DriverGuide shows that the file "siemens_windows_driver.zip" should contain the drivers you need for the MC45.
I didn't download this file from the DriverGuide site.

Plus your wvdial setup looks suspicious!

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

So, try that to see if wvdial detects your modem that the hardware has already properly detected.

Also, if you are using ndiswrapper and the Windows Driver, you need the following:

1.  Same 32bit or 64bit Windows driver as your *NIX Version 32/64bit??
2.  The Windows SYS & INF files for your Windows MC45 Driver

Here is some good information on ndiswrapper & the Windows Drivers under the section **#1**:

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

REF:
[http://www.automation.siemens.com/WW/forum/guests/PostShow.aspx?PageIndex=1&PostID=34401&Language=en](http://www.automation.siemens.com/WW/forum/guests/PostShow.aspx?PageIndex=1&PostID=34401&Language=en)

[www.gprsmodems.co.uk/images/gprs_startup_v0400.pdf](www.gprsmodems.co.uk/images/gprs_startup_v0400.pdf)

Google for:
mc45-mc46-at-command-set.pdf


lk

---

### Post by suomalainen on 2012-03-08
@ lkraemer,

Thank you very much for responding and lending your support. It's much appreciated!

Just to clarify, The laptop I have is a Panasonic Toughbook CF-29 (Mk1).On the left side over the battery compartment is a slot into which the GPRS modem slides into. I attached a picture (Siemens MC45.png) which shows this and you can see that it is held in place by 2 philips head screws. You can also see the slot for the SIM card and an outlet for headset. Research has shown that this modem uses the Siemens MC45 module. I can also confirm this by stating I made a visual as well.

I went to DriverGuide and in the dialogue box typed "Siemens MC45". From the new page that appeared one is lead to believe that a file called "siemens_windows_driver.zip" can be downloaded. Although this indeed is the case the file is not a zip file. Rather it is a exe file named "setup_132701.exe".

In Ubuntu 11.10 this file can be extracted and a Setup.exe file is found within the extracted folder. When this file is double clicked it starts the installation process then yields a Fetal Error message. See attached pic called "Fetal Error".

However, if you look closely this error message there is a link "Please try Directly Downloading this file". When you click this link then it gives you the opportunity to download "siemens_windows_driver.zip". When this file is extracted you will find a "mdmsiewm_v2.6.inf" file and a "readme.txt" file.  There is no sys file inside!!!

So........ This is how the first part of the instructions went for me.

I ran the command "sudo wvdialconf /etc/wvdial.conf" and the result returned was:

```
john@john-CF-29CTKGHGS:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S4   S5   S6   S7   S8   S9   S10  S11  
Modem Port Scan<*1>: S12  S13  S14  S15  S16  S17  S18  S19  
Modem Port Scan<*1>: S20  S21  S22  S23  S24  S25  S26  S27  
Modem Port Scan<*1>: S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://alumnit.ca/wiki/?WvDial

```

I ran the 10 terminal commands you gave and below are the results:

```
john@john-CF-29CTKGHGS:~$ asyncmap 0
asyncmap: command not found
john@john-CF-29CTKGHGS:~$ noauth
No command 'noauth' found, did you mean:
 Command 'nuauth' from package 'nuauth' (universe)
 Command 'nwauth' from package 'ncpfs' (universe)
noauth: command not found
john@john-CF-29CTKGHGS:~$ crtscts
crtscts: command not found
john@john-CF-29CTKGHGS:~$ lock
No command 'lock' found, did you mean:
 Command 'vlock' from package 'vlock' (universe)
 Command 'clock' from package 'xview-clients' (universe)
 Command 'rlock' from package 'liblockfile-ruby' (universe)
 Command 'loch' from package 'therion-viewer' (universe)
 Command 'flock' from package 'util-linux' (main)
 Command 'mlock' from package 'mlock' (universe)
 Command 'look' from package 'bsdmainutils' (main)
 Command 'wlock' from package 'sendfile' (universe)
 Command 'slock' from package 'suckless-tools' (universe)
 Command 'xlock' from package 'xlockmore-gl' (universe)
 Command 'xlock' from package 'xlockmore' (universe)
lock: command not found
john@john-CF-29CTKGHGS:~$ hide-password
hide-password: command not found
john@john-CF-29CTKGHGS:~$ modem
No command 'modem' found, did you mean:
 Command 'mode2' from package 'lirc' (main)
 Command 'mode3' from package 'svgalib-bin' (universe)
modem: command not found
john@john-CF-29CTKGHGS:~$ proxyarp
proxyarp: command not found
john@john-CF-29CTKGHGS:~$ lcp-echo-interval 30
lcp-echo-interval: command not found
john@john-CF-29CTKGHGS:~$ lcp-echo-failure 4
lcp-echo-failure: command not found
john@john-CF-29CTKGHGS:~$ noipx
No command 'noipx' found, did you mean:
 Command 'noip2' from package 'noip2' (universe)
noipx: command not found
```



**QUESTION:**

***what are pap-secrets and/or chap-secrets files??????***


Running wvdial /etc/wvdial.conf stated:

```
john@john-CF-29CTKGHGS:~$ wvdial /etc/wvdial.conf
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```


**QUESTION:**
[I][B]
How is CNTL C entered?[/B][/I] Is this just a command I enter/type via the keyboard?

**QUESTION:**

You stated: ***"So, try that to see if wvdial detects your modem that the hardware has already properly detected."***

Did you see something that told you that my GPRS modem is being seen/working? If so, tell me as I thought it wasn't being seen.

**QUESTION:**[/B]

Any advice as to how to get around the required sys file would be good to know about. Especially the exact name of the file I'm looking for.


Thanks again for your time and support in helping me work through this. I really appreciate it!!!

Best,

Suomalainen

---

### Post by lkraemer on 2012-03-08
Well, you are correct in that I made an incorrect assumption about your modem.  I assumed that:
> 
*-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)

was your MC45 Modem.  That was likely incorrect.

When you ran the configuration for wvdial, if it didn't locate your modem, then you won't get it working.

The ten commands you tried to execute are the contents of the file
located at:

**Checking settings of: /etc/ppp/options**

```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```

pap-secret & chap-secret files are configuration files for ppp.
You can read more there.
REF:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4


CNTL C is just those keystrokes in a Terminal Window (Console)
(Hold CNTL depressed and depress C)

Since wvdial didn't find the Modem you're pretty well stuck.  
Not much left to do as far as I know. Unless someone has a better idea!
And that means it doesn't require the sys & inf files..........Sorry!



lk

---

### Post by suomalainen on 2012-03-23
I guess that this also means that if I could find Windows programs that I could run under WINE they probably won't work because Linux kernel doesn't recognise the HW in the first place? or how dependant is WINE on the linux kernel?

---

### Post by suomalainen on 2012-03-24
bump

---

