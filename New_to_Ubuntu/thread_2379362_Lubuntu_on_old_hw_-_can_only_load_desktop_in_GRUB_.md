---
title: "Lubuntu on old hw - can only load desktop in GRUB - Recovery Mode"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by jman0war on 2017-12-04
I formatted my IBM Thinkpad X60s  (2007) and loaded Lubuntu 17 via a USB drive.

I find now that I can only get the laptop to load desktop in Lubunto when i hold Shift, get into GNU GRUB and choose the Advanced Options ->  Ubuntu, with Linus 4.13.0-16-generic (recovery mode)
Once in Recovery mode i can run all the things there, like **fsck **etc just fine.
WHen i choose "Resume" the OS will load to desktop ok.

But if i shut down and try and power up again, the laptop boots to   [I]/dev/sda1: clean, 127005/4890624 files, 1713657/19537408 blocks
[/I]There is a rainbow like bar across the top of screen, almost like a slow progress bar.
Mouse cursor available and working.

I don't know.
There was nothing wrong with this laptop before in hardware, it just had WindowsXP on it and it was slow to load.
I had no reason to keep XP so was happy enough to format everything, including the old Thinkpad recovery partition.


But it seems to me like Lubuntu has some problems with maybe the boot partition or something?

Sometimes i also boot to a white or gray screen that fades in, that has that rainbow effect across it.

Advanced -> Recovery Mode -> Resume pretty much works each time.

Any suggestions?
Total Ubuntu newbie here.

---

### Post by mörgæs on 2017-12-05
Hi, welcome to the fora.
Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt here in CODE tags. It will show us the hardware details.

---

### Post by jman0war on 2017-12-05
```
computer
    description: Notebook
    product: 17046DG
    vendor: LENOVO
    version: ThinkPad X60s
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 family=ThinkPad X60s frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 17046DG
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7BETD7WW (2.18 )
          date: 11/20/2008
          size: 144KiB
          capacity: 1984KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           L2400  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.14.8
          serial: [REMOVED]
          slot: None
          size: 1006MHz
          capacity: 1667MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts cpuid aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
             configuration: level=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: [REMOVED]
          size: 997MHz
          capacity: 1667MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller cap_list
             configuration: latency=0
             resources: memory:ee100000-ee17ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:ee200000-ee23ffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:ee180000-ee1fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:ee240000-ee243fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:ee000000-ee0fffff ioport:80000000(size=2097152)
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: ens2
                version: 00
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:ee000000-ee01ffff ioport:2000(size=32)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=8192) memory:ec000000-edffffff ioport:e4000000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wls3
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=4.13.0-16-generic firmware=15.32.2.9 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:31 memory:edf00000-edf00fff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=8192) memory:e8000000-e9ffffff ioport:e4100000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:7000(size=8192) memory:ea000000-ebffffff ioport:e4200000(size=1048576)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Generic USB device
                   product: Mini Card
                   vendor: Sierra Wireless, Incorporated
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=sierra speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: BCM2045B
                   vendor: Broadcom Corp
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb speed=12Mbit/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Biometric Coprocessor
                   vendor: STMicroelectronics
                   physical id: 2
                   bus info: usb@5:2
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:ee444000-ee4443ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:9000(size=16384) memory:e4300000-e7ffffff ioport:e0000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: b4
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:e4300000-e4300fff ioport:9000(size=256) ioport:9400(size=256) memory:e0000000-e3ffffff memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 09
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:e4301000-e43017ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 18
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:e4301800-e43018ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:18d0(size=8) ioport:18c4(size=4) ioport:18c8(size=8) ioport:18c0(size=4) ioport:18b0(size=16) memory:ee444400-ee4447ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
     *-scsi
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK8034GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1E
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e740bf31
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-12-03 16:46:50 filesystem=ext4 lastmountpoint=/ modified=2017-12-05 16:58:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-12-05 16:56:42 state=mounted


```

---

### Post by mörgæs on 2017-12-06
I suggest that you click the old hardware link in my signature and search the text for *UXA*. Try the recommendations there.

---

### Post by jman0war on 2017-12-08
Brought laptop into a linux guy at my work.
He noticed that the screen is basically not centered and there are 2 lines on the bottom that are off screen.

He resolved the issue with this:

Edit (as root) /etc/default/grub and change following line:
 
FROM:
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8221;
 
TO:
 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Save changes

Then from command line run following to regenerate boot image and restart system
sudo update-grub

---

