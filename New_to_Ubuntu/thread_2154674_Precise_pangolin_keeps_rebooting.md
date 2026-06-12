---
title: "Precise pangolin keeps rebooting"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by opiumsmoker on 2013-06-15
Title says it all... My computer reboots ramdomly from time to time, here are some specs, if you need any other info please let me know

```
description: Desktop Computer
    product: A55MLC2 (None)
    vendor: BIOSTAR Group
    serial: None
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=None sku=None uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A55MLC2
       vendor: BIOSTAR Group
       physical id: 0
       serial: None
       slot: None
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.4
          date: 05/29/2012
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 9905471-001.A01LF
             vendor: Kingston
             physical id: 2
             serial: 6C3ADA0A
             slot: A1_DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber3
             vendor: A1_Manufacturer3
             physical id: 3
             serial: A1_SerNum3
             slot: A1_DIMM3
     *-cache:0
          description: L2 cache
          physical id: f
          slot: L2 CACHE
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cache:1
          description: L1 cache
          physical id: 10
          slot: L1 CACHE
          size: 512KiB
          capacity: 512KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cpu
          description: CPU
          product: AMD A6-3670 APU with Radeon(tm) HD Graphics
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 12
          bus info: cpu@0
          version: AMD A6-3670 APU with Radeon(tm) HD Graphics
          slot: P0
          size: 800MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=4 enabledcores=4 threads=4
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
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:44 memory:e0000000-efffffff ioport:f000(size=256) memory:fef00000-fef3ffff
        *-multimedia:0
             description: Audio device
             product: BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:fef44000-fef47fff
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
             resources: irq:19 ioport:f190(size=8) ioport:f180(size=4) ioport:f170(size=8) ioport:f160(size=4) ioport:f150(size=16) memory:fef4f000-fef4f7ff
        *-usb:0
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
             resources: irq:18 memory:fef4e000-fef4efff
        *-usb:1
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fef4d000-fef4d0ff
        *-usb:2
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
             resources: irq:18 memory:fef4c000-fef4cfff
        *-usb:3
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fef4b000-fef4b0ff
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
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fef40000-fef43fff
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
        *-usb:4
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
             resources: irq:18 memory:fef4a000-fef4afff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
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
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: b8:97:5a:17:b7:02
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:5
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fef49000-fef49fff
        *-usb:6
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fef48000-fef480ff
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
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA DT01ACA0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: MS1O
             serial: 435HLNRNS
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=95bc6bbf-2b6a-4ea5-817c-49fa3b29c6e3
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 7f76b0eb-0bcf-4d64-8a5c-35879474254c
                size: 74GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-06-06 22:59:00 filesystem=ext4 lastmountpoint=/ modified=2013-06-06 23:33:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-06-15 10:06:43 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /home
                version: 1.0
                serial: 7b1e0051-ebdd-4601-a33d-a2bbc27f4ea8
                size: 149GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-06 22:59:02 filesystem=ext4 lastmountpoint=/home modified=2013-06-15 10:14:02 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-06-15 10:14:02 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 8e5e2cf6-3286-446a-8ea2-59c18dfe7d9f
                size: 1906MiB
                capacity: 1906MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:3
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                logical name: /boot/efi
                version: FAT32
                serial: d039-f912
                size: 185MiB
                capacity: 190MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
```

---

### Post by Scallyph on 2013-06-15
I had that twice. What i would do:
-unplug all usb devices  > test system
-A visual check on the Elco;s on motherboard 
 If  the top of an elco is not flat then that could be the reason for random  system reboots. Check especially those around/near CPU and on-board  graphic chip
-If  (while on a running system) pressing/pulling/moving  sideways carefully, with not to much force, on the fan (or better  cooling-block) of the cpu makes the system reboot.
 This could indicate an incorrect placed or faulty CPU or CPU-socket.

If everything looks good/keeps running, then test system with a live DVD or pen-drive.
If problem is still there then:

-If available, plug in an graphic card and disable on-board graphic card in bios. > test system.
other reasons could be memory-module or memory-bank or power-supply
-memory bank > move module to bank 3 (read MB manual before doing so) !!!
-Power-supply > especially if you recently added/replaced hardware >remove added hardware or replace power-supply

---

### Post by sgaap on 2013-06-15
I would first try to change the memory bank if memcheck doesn't give you any errors.
If memcheck runs without issues and another bank doesn't work it might help to either change the timings on your memory and/or underclock it a bit to see if that works.

---

### Post by Scallyph on 2013-06-16
I forgot to ask you. Did random reboots started AFTER installing Pangolin? If so, it will probably be useless to follow my previous given advise. Except maybe for the DVD or pendrive option.  Sgaap suggestion, running memcheck is a good one. Even before doing anything else.  But if you decide to open up your box. Do a visual inspection first.  You should move/replace/install hardware with care and only when system is not plugged into power/wallsocket. Even if youre systems powersupply has a on/off button. On a open and running system take off any jewelry you ware on hands or wrists.

---

### Post by Scallyph on 2013-06-16
I forgot to ask you. Did random reboots started AFTER installing Pangolin? If so, it will probably be useless to follow my previous given advise. Except maybe for the DVD or pendrive option.  Sgaap suggestion, running memcheck is a good one. Even before doing anything else.  But if you decide to open up your box. Do a visual inspection first.  You should move/replace/install hardware with care and only when system is not plugged into power/wallsocket. Even if youre systems powersupply has a on/off button. On a open and running system take off any jewelry you ware on hands or wrists.

---

### Post by opiumsmoker on 2013-06-17
Sorry the delay the problem persists, everything inside seems well connected... will try sgaap memtest and post... thanks for the replies

---

### Post by opiumsmoker on 2013-06-17
> **opiumsmoker said:**
> Sorry the delay the problem persists, everything inside seems well connected... will try sgaap memtest and post... thanks for the replies

when executing memtest show Unkown error "linux16"

---

### Post by opiumsmoker on 2013-06-18
also made a boot-repair just in case, this is the output (long text)

[http://paste.ubuntu.com/5776094/](http://paste.ubuntu.com/5776094/)

---

### Post by opiumsmoker on 2013-06-20
Well I tried installing Windows 7... but the rebooting issue attacked in the middle of the installation, so a software issue is discarted... guess will have to send it to the company

---

### Post by mansonfan78 on 2013-06-20
I had something similar happen years ago (with Windows) and it turned out to be an irq conflict somewhere.  I solved it by swapping the slots for my video card and sound card.  You could try something like that, or maybe switch the memory to a different slot.  It also might not be a bad idea to get some spray air duster and blow the dust out of the connections.

---

