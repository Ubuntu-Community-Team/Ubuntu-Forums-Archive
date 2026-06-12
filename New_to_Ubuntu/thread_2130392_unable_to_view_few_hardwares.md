---
title: "unable to view few hardwares"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by 007riky on 2013-03-29
Hi,

I have recently purchased a new laptop, with AMD chip, I have installed ubantu 12.04 on a friend's recomndation, but i am unable to find certain hardwares, such as camera etc. can anyone help me in this regard.

Thanks in advance.

---

### Post by mörgæs on 2013-03-29
Hi, welcome to the fora.

Please run

```
sudo lshw > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by 007riky on 2013-03-29
Just sticked to the first one

also it is asking for password, while running the code. but not taking it

---

### Post by deadflowr on 2013-03-29
> **007riky said:**
> Just sticked to the first one

also it is asking for password, while running the code. but not taking it

The password will be invisible. Type it anyway as best you can remember it.

---

### Post by 007riky on 2013-03-29
> **deadflowr said:**
> The password will be invisible. Type it anyway as best you can remember it.

okay done now??

---

### Post by deadflowr on 2013-03-29
> **007riky said:**
> okay done now??

Did it produce a bunch of output stuff?

If so, open your home folder and look for the lshw.txt file.
Open the file and select all and copy.
Then open a reply in the thread and click on the # button in the reply box toolbar.
Then paste the copy file in between the two code]here[code boxes.

---

### Post by 007riky on 2013-03-29
```
#[rikesh-k53u    description: Notebook
    product: K53U ()
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: CCN0CJ465383507
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook uuid=34721D6E-3AE8-11E2-87F5-08606E8CD933
  *-core
       description: Motherboard
       product: K53U
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 223
          date: 04/10/2012
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: HMT325S6CFR8C-PB
             vendor: Hynix Semiconduc
             physical id: 1
             serial: 0F73936D
             slot: A1_DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cache:0
          description: L1 cache
          physical id: 2c
          slot: L1 CACHE
          size: 128KiB
          capacity: 128KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cache:1
          description: L2 cache
          physical id: 2d
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cpu
          description: CPU
          product: AMD C-60 APU with Radeon(tm) HD Graphics
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 36
          bus info: cpu@0
          version: AMD C-60 APU with Radeon(tm) HD Graphics
          slot: P0
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 14h Processor Root Complex
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: Wrestler [Radeon HD 6290]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:42 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: Wrestler HDMI Audio [Radeon HD 6250/6310]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             product: Family 14h Processor Root Port
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:7f000000-7f1fffff ioport:7f200000(size=2097152)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f190(size=8) ioport:f180(size=4) ioport:f170(size=8) ioport:f160(size=4) ioport:f150(size=16) memory:feb4f000-feb4f3ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MQ01ABD0
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AX00
                serial: 92REP7XWT
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a5135a6b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: b66e6d3a-5cfc-4341-8071-18fd52e3f314
                   size: 122GiB
                   capacity: 122GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-03-22 01:37:49 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 341GiB
                   capacity: 341GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 61GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 55GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /boot
                      capacity: 476MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,stripe=4,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home
                      capacity: 223GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW DVRTD11RS
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb4e000-feb4efff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb4d000-feb4d0ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb4c000-feb4cfff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb4b000-feb4b0ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f100(size=16)
        *-multimedia:1
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb40000-feb43fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb4a000-feb4afff
        *-pci:2
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 08:60:6e:8c:d9:33
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:3
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: dc:85:de:9b:95:49
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-39-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:fea00000-fea7ffff memory:fea80000-fea8ffff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb49000-feb49fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb48000-feb480ff
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
          bus info: usb@1:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr1
             logical name: /media/Reliance 3G
             capabilities: audio partitioned partitioned:mac
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-volume:0 UNCLAIMED
                description: Apple partition map
                physical id: 1
                bus info: scsi@8:0.0.0,1
                capacity: 17KiB
           *-volume:1 UNCLAIMED
                description: Apple HFS
                vendor: Mac OS X
                physical id: 2
                bus info: scsi@8:0.0.0,2
                version: 4
                serial: 00000000-0000-0000-0000-000000001000
                size: 26MiB
                capacity: 26MiB
                capabilities: hfsplus initialized
                configuration: checked=1904-01-01 05:53:20 created=2011-09-02 09:17:05 filesystem=hfsplus lastmountedby=10.0 modified=2011-09-02 14:47:05 state=clean
        *-disk
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdb]
```
Edited by The Cog to add code tags for readability

---

### Post by deadflowr on 2013-03-29
Let's investigate further.

Try running
```
lspci -v
```

and 

```
lsusb
```

Do the same thing as before, but remember to use the code tags.

---

### Post by 007riky on 2013-03-29
#```
rikesh@rikesh-K53U:~$ lspci -v00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Flags: bus master, 66MHz, medium devsel, latency 0


00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6290] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_12, radeon


00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 7f000000-7f1fffff
    Prefetchable memory behind bridge: 000000007f200000-000000007f3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f190 [size=8]
    I/O ports at f180 [size=4]
    I/O ports at f170 [size=8]
    I/O ports at f160 [size=4]
    I/O ports at f150 [size=16]
    Memory at feb4f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd


00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4d000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd


00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4b000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: 66MHz, medium devsel
    Kernel modules: sp5100_tco, i2c-piix4


00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp


00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64


00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd


00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb49000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd


00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb48000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel


00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel


00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp


00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel


00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel


00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel


00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel


03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at e000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
    Subsystem: AzureWave Device 2c97
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fea00000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at fea80000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k



```

#> rikesh@rikesh-K53U:~$ lsusbBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 19d2:0117 ZTE WCDMA Technologies MSM 
Bus 001 Device 003: ID 04f2:b23b Chicony Electronics Co., Ltd 
Bus 004 Device 007: ID 13d3:3362 IMC Networks 

---

### Post by deadflowr on 2013-03-29
From what I gather this

> [COLOR=#000000]*Bus 001 Device 003: ID 04f2:b23b Chicony Electronics Co., Ltd*[/COLOR]

seems to be the camera.

Unfortunately, I can't find anything about its compatiblity with linux.:(

It is listed as an unknown device in Ubuntu certified hardware listing

[http://www.ubuntu.com/certification/catalog/make/CHICONY%20Electronics%20Co%20Ltd/](http://www.ubuntu.com/certification/catalog/make/CHICONY%20Electronics%20Co%20Ltd/)

---

### Post by mörgæs on 2013-03-29
Very few people seem to be posting about this webcam in Buntu. Could be because the K53U is rare, which I doubt, or because the problem is fixed in the latest release. 

If you have 10 GB left on your hard drive you could try installing Buntu 13.04 (beta) and see if it works here. If not it would be good to create a bug report to get the developers' attention.

---

### Post by 007riky on 2013-03-30
thanks for your support.

But My di has solved the problem. :)

---

### Post by barrymmm on 2013-04-09
Hey could you share the solution with me please? I believe I've got the same web cam (Chicony) with the same symptoms.

---

