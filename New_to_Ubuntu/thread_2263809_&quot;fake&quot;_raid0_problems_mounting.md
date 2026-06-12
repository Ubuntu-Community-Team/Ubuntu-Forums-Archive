---
title: "&quot;fake&quot; raid0 problems mounting"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by dave_van_loo on 2015-02-03
greetings fellow ubuntu/kubuntu users. for a while now i have been trying to mount an existing raid0 drive

my system is configured as follows:

6 drives pressent:

/dev/sda 111.79 GiB ssd mounted to: /media/SSD
/dev/sdb 465.76 GiB hd mounted to: /media/sda1
/dev/sdc 0.91 TiB hd mounted to: /media/sdc1
/dev/sdd 1.82 TiB hd < 1 of the 2 drives in "fake" raid 0 >
/dev/sde 1.82 TiB hd < 1 of the 2 drives in "fake" raid 0 >
/dev/sdf 238.47 GiB PCI-e ssd mounted to /media/dave/PCIe SSD  ( i am aware the space can couse issues sometimes )
the PCI-e drive also containst the swap partition

i am at a total loss on how to achieve this.., and if possible.. at boot :)

---

### Post by SeijiSensei on 2015-02-03
Probably not going to work.  "Fake" RAID requires a proprietary driver at the operating system level.  There are often drivers for Windows, but rarely ones for Linux.  If you can identify the controller, you might want to check at the manufacturer's site.  Try "lspci" at a command prompt.  If it doesn't show up there, use "sudo lshw" to get a complete hardware census.

Is there only one partition on /dev/sdd, say /dev/sdd1?  Then create a temporary mount point like you did for /dev/sdc1 and see if you can mount /dev/sdd1 there.  If so, you have a couple of options.  One is to mount /dev/sde1 as well, and run rsync nightly to make /dev/sde1 a copy of /dev/sdd1.  Another, better, option is available if you have another drive, like an external, large enough to contain all the data on /dev/sdd1.  If so, back up /dev/sdd1, then [create a Linux software RAID array using mdadm]("https://raid.wiki.kernel.org/index.php/RAID_setup#RAID-1").

---

### Post by dave_van_loo on 2015-02-03
mhmm, ok... to make sure im not getting my terms mixed up, "fake" raid is raid using the motherboards bios config..? if so.. just to satisfy my curiosity. were would i be able to "search" weither im a really lucky dude and proprietary drivers are avaible for my motherboard? ( assuming thats the part i would need to find drivers for )

---

### Post by SeijiSensei on 2015-02-03
As I said, use lspci or lshw to identify the manufacturer of the disk controller.  It may be the same manufacturer as the motherboard; it may not.

"Fake" RAID has nothing to do with whether it is located on the motherboard or on a separate controller card.  It's simply a RAID based in software like Linux MD, but one that requires special proprietary drivers.

---

### Post by dave_van_loo on 2015-02-03
thank you for your help, i will get to work on this and will update the thread as i make progress, thank you a lot for your help and information on this subject.

---

### Post by dave_van_loo on 2015-02-03
oke, the command provides me with the following output, should i be looking at the SATA controller, or is the required componant not listed ammong this? :

> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
02:00.0 SATA controller: Device 1c28:0122 (rev 14)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)

---

### Post by SeijiSensei on 2015-02-03
Searching for "SATA controller: Device 1c28:0122" brings me to [this item at LLKL]("https://lkml.org/lkml/2015/2/2/617") from just yesterday.  That looks to be the SSD device.
> 
The long name for this device is
Lite-On IT Corp. / Plextor M6e PCI Express SSD [Marvell 88SS9183] (rev 14)


At the Intel site I could only find this: [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=18440&lang=eng](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=18440&lang=eng)

Operating Systems: Windows Server 2003 *, Windows Server 2008 *, Windows 2000 Server*, Windows 7 *, Windows Vista *, Windows XP *

Have you tried looking on the motherboard site?  If this is a pre-built system, did you try contacting the manufacturer?

You might trying using the dmraid utility described in this article:  [https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID](https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID)

I've now exhausted my level of knowledge of this subject since I've only ever used Linux MD software RAID.  I don't like having to rely on dicey support from manufacturers for something as basic as storage.

---

### Post by dave_van_loo on 2015-02-03
yes, the SSD is an intel SSD. the motherboard site (asus) does not have any linux drivers on them, and no the system is custom build. i do indeed understand now why for linux this kind of raid is a bad idea.. i dual boot with windows, so having the largest drive ( raid 0 on 2 2tb = 4 tb drive..) not avaible.. is a nuisence, luckily i have other drives to make up for it :)

---

### Post by dave_van_loo on 2015-02-07
i have searched some more arround the internet, and came up blank so far.. i also did a full report on my system.. but failed to locate the component.

here is the report:

  [SPOILER]> description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=2042172F-CB5B-D911-A063-C860006E411A
  *-core
       description: Motherboard
       product: P8Z68-V LX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MT7021K10800440
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4001
          date: 06/12/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal unified
     *-memory
          description: System Memory
          physical id: 5d
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ8GX3M2A1866C9
             vendor: AMI
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ8GX3M2A1866C9
             vendor: AMI
             physical id: 1
             serial: 00000000
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ8GX3M2A1866C9
             vendor: AMI
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ8GX3M2A1866C9
             vendor: AMI
             physical id: 3
             serial: 00000000
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK104 [GeForce GTX 760]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:51 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GK104 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:49 memory:f730b000-f730b00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7308000-f73083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f7300000-f7303fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f7200000-f72fffff
           *-storage
                description: SATA controller
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 14
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:48 ioport:d050(size=8) ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4) ioport:d000(size=32) memory:f7220000-f72201ff memory:f7200000-f721ffff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7100000-f71fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:f7100000-f7107fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: c8:60:00:6e:41:1a
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.19 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:47 ioport:c000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7307000-f73073ff
        *-isa
             description: ISA bridge
             product: Z68 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7306000-f73067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7305000-f73050ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: INTEL SSDSC2CW12
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 400i
             serial: CVCV1530003K120BGN
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=141ba6b7
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/SSD
                version: 3.1
                serial: d6d3305e-a53d-8449-8d5a-4b6c5e8d8c49
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-09-06 07:20:46 filesystem=ntfs label=SSD mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 01.0
             serial: WD-WMASY3354613
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=e7f70907
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/sda1
                version: 3.1
                serial: 1e9c9050-2769-cd47-971f-26b10a4d4371
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-02-24 22:13:15 filesystem=ntfs label=Data mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EADS-00M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             version: 01.0
             serial: WD-WCAV51166434
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=e8aadeea
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/sdc1
                version: 3.1
                serial: 7ab82e58-e53b-fe48-b26a-8ff138ebad54
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-02-18 21:52:24 filesystem=ntfs label=1 tb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:3
          physical id: 5
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000NM0033-9ZM
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdd
             version: SN04
             serial: Z1X35638
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=5c81fd34-4f9e-4535-8154-4cf1ac7de037 sectorsize=512
           *-volume:0
                description: reserved partition
                vendor: Windows
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdd1
                serial: c1058c80-6883-41e4-894e-08bc0dafc50a
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:1 UNCLAIMED
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@4:0.0.0,2
                version: 3.1
                serial: e68487a2-3abc-c049-84de-7c84721ab05c
                size: 1677GiB
                capacity: 3725GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-11-09 00:53:05 filesystem=ntfs label=raid-0 name=Basic data partition state=clean
     *-scsi:4
          physical id: 6
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000NM0033-9ZM
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sde
             version: SN04
             serial: Z1X355K2
             size: 1863GiB (2TB)
             configuration: ansiversion=5 sectorsize=512
     *-scsi:5
          physical id: 7
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: PLEXTOR PX-AG256
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdf
             version: 1.04
             serial: P02443111536
             size: 238GiB (256GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=8416b3f7
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdf1
                logical name: /media/dave/PCIe SSD
                version: 3.1
                serial: 2426e71e-b906-c642-8c98-1400beb47267
                size: 191GiB
                capacity: 191GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-11-08 18:30:13 filesystem=ntfs label=PCIe SSD mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdf2
                size: 46GiB
                capacity: 46GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdf5
                   capacity: 15GiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdf6
                   logical name: /
                   capacity: 30GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
  *-power:0 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-power:1 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
[/SPOILER]

---

