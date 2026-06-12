---
title: "Slow response, I/O wait, conflicts 14.04 LTS"
date: 2014-09-19
forum: New to Ubuntu
---

### Post by agentorange2 on 2014-09-19
Hi

New to Ubuntu and recently setup dual boot with my existing Win 7 64bit. PC is soley used by me and no other users. The two are booting and available via the grub menu. However whilst Win 7 is very quick and snappy to respond Ubuntu is very slow and laggy. Command line is virtually instant but Unity UI laggy in initial startup of apps. Once app started response is perfectly acceptable but still generates a large amount of IO wait ie. Greater than 40%.

Firefox in Win7 starts instantly. Firefox in Ubuntu takes 5-10 seconds with lots of IO wait.

The dual boot setup was a little problematic and that may point to the problem.

PC has 1 x SSD (Win7), 2xHDD (160 and 500GB) drives. Ideally I wanted Ubuntu on the 160GB HDD but try as I might the partitioning on Ubuntu install just failed and errored with a dialgoue box full of ???? when it got to the timezone selection screen. Using a free partition on the 500GB worked fine with no obvious issues. Incidentally Ubuntu was unable to detect my existing Win7 OS.

Boot displays two conflicts /var/log/syslog

```
Sep 19 18:41:02 linux kernel: [    8.212139] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
Sep 19 18:41:02 linux kernel: [    8.212143] ACPI: If an  driver is available for this device, you should use it instead of the native driver
Sep 19 18:41:02 linux kernel: [    8.212145] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
Sep 19 18:41:02 linux kernel: [    8.212147] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 18:41:02 linux kernel: [    8.212148] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \LED_ 1 (20131115/utaddress-251)
Sep 19 18:41:02 linux kernel: [    8.212150] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20131115/utaddress-251)
Sep 19 18:41:02 linux kernel: [    8.212151] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 18:41:02 linux kernel: [    8.212152] lpc_ich: Resource conflict(s) found affecting gpio_ich
```

```
Sep 19 18:41:02 linux kernel: [    8.862080] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
```

The SystemIO conflict would seem the obvious issue here. 

Any advice as to what I can do to resolve?
 Also any understanding as to why the install wouldn't use the 160GB HDD? I've since carved it up for Windows.

Below is output from fdisk (which is telling but I don't understand) and lshw and if anyone is able to assist I'd be very grateful! :) 

Thanks

```
@linux:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1caee299

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   153602047    76697600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5ead544

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   629528575   314763264    7  HPFS/NTFS/exFAT
/dev/sdb2       629528576   631529471     1000448   83  Linux
/dev/sdb3       631529472   647530495     8000512   82  Linux swap / Solaris
/dev/sdb4       647532542   976771071   164619265    5  Extended
/dev/sdb5   *   647532544   976771071   164619264   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa845a590

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   312578047   156288000    7  HPFS/NTFS/exFAT

Disk /dev/mapper/nvidia_bicabiha: 160.0 GB, 160041884672 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581806 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa845a590

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bicabiha1            2048   312578047   156288000    7  HPFS/NTFS/exFAT

Disk /dev/mapper/nvidia_bicabiha1: 160.0 GB, 160038912000 bytes
255 heads, 63 sectors/track, 19456 cylinders, total 312576000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bicabiha1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
/dev/mapper/nvidia_bicabiha1p2   ?  1917848077  2462285169   272218546+  73  Unknown
/dev/mapper/nvidia_bicabiha1p3   ?  1818575915  2362751050   272087568   2b  Unknown
/dev/mapper/nvidia_bicabiha1p4   ?  2844524554  2844579527       27487   61  SpeedStor

Partition table entries are not in disk order
@linux:~$ 
```




```
@linux:~$ sudo lshw
linux                     
    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 ldt16 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=5002E503-4904-EE05-EE06-9D0700080009
  *-core
       description: Motherboard
       product: Z77-D3H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F18
          date: 08/21/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through instruction
     *-cache:2
          description: L3 cache
          physical id: 6
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-07-07 12:12+0000X-Generator: Launchpad (build 17086) [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KHX1600C9D3/4GX
             vendor: Kingston
             physical id: 1
             serial: 40192157
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-07-07 12:12+0000X-Generator: Launchpad (build 17086) [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KHX1600C9D3/4GX
             vendor: Kingston
             physical id: 3
             serial: 411AC477
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 43
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz
          slot: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:f7e00000-f7efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Curacao XT [Radeon R9 270X]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:46 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
           *-multimedia
                description: Audio device
                product: Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:47 memory:f7e60000-f7e63fff
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:42 memory:f7f00000-f7f0ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:f7f19000-f7f1900f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7f17000-f7f173ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f7f10000-f7f13fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) memory:f7d00000-f7dfffff
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c0
                serial: 50:e5:49:ee:ee:9d
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:48 memory:f7d00000-f7d3ffff ioport:d000(size=128)
        *-pci:4
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f7c00000-f7cfffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:43 memory:f7c00000-f7c07fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7f16000-f7f163ff
        *-isa
             description: ISA bridge
             product: Z77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=16) ioport:f080(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7f15000-f7f150ff ioport:f000(size=32)
        *-ide:1
             description: IDE interface
             product: 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f030(size=16) ioport:f020(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: OCZ-AGILITY3
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2.15
             serial: OCZ-J070366484I8T23D
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=1caee299
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 5206835c-87a7-5c4b-8245-e98658af9f38
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-09-07 04:04:44 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 064985b0-1af8-6242-94de-a8dd3279e5e8
                size: 73GiB
                capacity: 73GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-09-07 04:05:01 filesystem=ntfs state=clean
        *-disk:1
             description: ATA Disk
             product: SAMSUNG HD501LJ
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: CR10
             serial: S0MUJ1FPB55903
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b5ead544
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: ee98ce17-23c0-ae44-bcfc-00b60e1d0956
                size: 300GiB
                capacity: 300GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-01-01 19:03:50 filesystem=ntfs label=New Volume state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sdb2
                logical name: /boot
                version: 1.0
                serial: 32325604-b3f7-470a-af4f-01ff0bf27b95
                size: 977MiB
                capacity: 977MiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-09-14 22:28:45 filesystem=ext4 lastmountpoint=/boot modified=2014-09-19 18:41:02 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-09-19 18:41:02 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.1.0,3
                logical name: /dev/sdb3
                version: 1
                serial: 8705d005-42cb-4cdc-9f7a-254bc43682d4
                size: 7813MiB
                capacity: 7813MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.1.0,4
                logical name: /dev/sdb4
                size: 156GiB
                capacity: 156GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /
                   capacity: 156GiB
                   capabilities: bootable
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HD161HJ
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sdc
             version: GF10
             serial: S0V3J1DP901354
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=a845a590
           *-volume UNCLAIMED
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.1.0,1
                version: 3.1
                serial: 1c2e7244-6d49-a24a-bfb3-b8db387ce216
                size: 149GiB
                capacity: 149GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-09-14 22:12:41 filesystem=ntfs label=New Volume state=clean
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc
     *-scsi:3
          physical id: 8
          bus info: usb@5:1.2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdd
             configuration: sectorsize=512
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
@linux:~$ 
```

---

### Post by Michael_McKenney on 2014-09-19
ACPI driver is not loading properly and affecting your 160GB.   I would consider moving Ubuntu to a newer driver and getting rid of the 160GB.

---

### Post by agentorange2 on 2014-09-19
Thank you for responding but I'm sorry I don't completely understand your answer. Are you saying update the ACPI driver and also remove the 160GB drive from the PC? If so can you point me towards some info on how to update the driver please because Ubuntu appears up to date. Thanks.

---

### Post by Michael_McKenney on 2014-09-19
ACPI is a chipset driver.  Some chipsets are not well supported in Linux.  It can lead to NICs and hard drives not working well.  Hard drives are cheap.  SATA drives don't need ACPI like IDE drives.  Getting rid of the 160 GB and replacing it with a $50-$80 drive would probably improve your performance.  Can you install Ubuntu on the other drive and unplug the 160GB and test performance.  Without ACPI working, the 160GB drive will drag your rig down. 

 I tested my Tyan Thunder K8WE rig with a Live boot DVD to see if everything was found and working properly.  I checked the error logs for issues.  The next step is a test install on a single hard drive with the old OS hard drive unplugged.

---

### Post by agentorange2 on 2014-09-22
Thanks though that confuses me a little because I'm not running any IDE  drives in the system and the Z77 chipset appears to be well supported  with this release of Ubuntu. The 160GB drive is an old SATA 1.5 drive  but otherwise system has SATA 2 500GB and SATA 3 SSD.

However I  was looking for an excuse to purchase another SSD for the OS so I'll do  that and swap out the old 160GB drive and see how things go and report  back.

Thanks

---

### Post by kira-yamato-2008 on 2014-09-22
The issue might be because of you using all three grades of SATA at the same time, or because the controller for your SATA 1.5 is actually a legacy feature, and may not be fully supported on newer motherboards, even despite backwards and forewords compatibility.

---

### Post by agentorange2 on 2014-09-23
There's me saying I'm not running any IDE drives and after digging around I've noticed my mobo has the SATA interface running in "IDE" mode and not "ACHI".

Unlikely to get time before the weekend but I'll update once changed.

---

### Post by agentorange2 on 2014-10-03
Finally got some time and it's now resolved. Thanks for pointing me in the right direction. SATA drives weren't 1.5 but 2.5 btw.

I "fixed" it by doing the following:

Removed Ubuntu and Grub from machine - re-instated Win MBR
Removed SATA 160GB 
Switched mobo SATA interface mode from IDE to AHCI (Updated Win7 prior to change [http://support2.microsoft.com/kb/922976](http://support2.microsoft.com/kb/922976)) 
[SIZE=1]       PS. FWIW - 30% increase in performance of the SSD in Win by switching to AHCI.[/SIZE]

Bought and installed new Samsung 840 EVO SSD (just before they announced the performance bug...)
Migrated Win7 from OCZ SSD to Samsung SSD
Installed Ubuntu with manual partitioning on OCZ 120GB SSD as still couldn't recognise Win7 being present

Ubuntu and Win7 now like lightening. :)

So  that's quite a lot of changes to be able to confidently say what was  causing the problem but given the 160GB was working absolutely fine and  HDTune benchmarked it as performing normally I'm inclined to lean  towards 14.04 doesn't like IDE mode on a Gigabyte Z77-D3H  motherboard/Seagate SATA 2.5 160GB drive combo.

---

