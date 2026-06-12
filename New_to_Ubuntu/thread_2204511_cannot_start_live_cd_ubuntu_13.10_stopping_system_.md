---
title: "cannot start live cd ubuntu 13.10 stopping system V runlevel compatibility"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by jeremie4 on 2014-02-08
[COLOR=#000000][FONT=Helvetica]Hi all,[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]since I had trouble installing graphic drivers on opensuse on my new laptop which is a hybrid system (amd radeon card + intel gpu), I would like to try Ubuntu that seems to be more up to date on that topic.
But I cannot even start the live cd:

I validated the downloaded iso with its checksum

without nomodeset boot option, I get a gray screen and cannot see the boot logs.
With nomodeset, the system halts with this last log: **stopping system V runlevel compatibility**

[https://drive.google.com/file/d/0B1EN01jJHIlcNmlWbGI5RWdudENYbFo3ZmNuT1lpZEN0REww/edit?usp=sharing](https://drive.google.com/file/d/0B1EN01jJHIlcNmlWbGI5RWdudENYbFo3ZmNuT1lpZEN0REww/edit?usp=sharing)
[https://drive.google.com/file/d/0B1EN01jJHIlcT0l2SjRqNTE3M2c4QThLeHRjWERVQUFfZDFz/edit?usp=sharing](https://drive.google.com/file/d/0B1EN01jJHIlcT0l2SjRqNTE3M2c4QThLeHRjWERVQUFfZDFz/edit?usp=sharing)

With nomodeset, noapic, nolapic, the system halts with the same last log:
[https://drive.google.com/file/d/0B1EN01jJHIlcaVZpbzdMWmdpazh0ci1vV2FvaTZCakpPa0lN/edit?usp=sharing](https://drive.google.com/file/d/0B1EN01jJHIlcaVZpbzdMWmdpazh0ci1vV2FvaTZCakpPa0lN/edit?usp=sharing)

Any help would be highly appreciated :).

Regards,
Jeremie


[/FONT][/COLOR]```

Below the result of sudo lshw on opensuse:
computer
description: Laptop
product: 870Z5E/880Z5E/680Z5E (SAMSUNG SENS Series)
vendor: SAMSUNG ELECTRONICS CO., LTD.
version: P01ADH
serial: [REMOVED]
width: 64 bits
capabilities: smbios-2.7 dmi-2.7 vsyscall32
configuration: boot=normal chassis=laptop family=SAMSUNG SENS sku=SAMSUNG SENS Series uuid=[REMOVED]
*-core
description: Motherboard
product: NP680Z5E-X01FR
vendor: SAMSUNG ELECTRONICS CO., LTD.
physical id: 0
version: SEC_SW_REVISION_1234567890ABCD
serial: [REMOVED]
slot: Middle
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: P01ADH.005.130402.SK
date: 04/02/2013
size: 64KiB
capacity: 4032KiB
capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
*-cache:0
description: L2 cache
physical id: 34
slot: CPU Internal L2
size: 512KiB
capacity: 512KiB
capabilities: internal write-through unified
*-cache:1
description: L1 cache
physical id: 35
slot: CPU Internal L1
size: 128KiB
capacity: 128KiB
capabilities: internal write-through data
*-cache:2
description: L3 cache
physical id: 36
slot: CPU Internal L3
size: 3MiB
capacity: 3MiB
capabilities: internal write-back unified
*-memory
description: System Memory
physical id: 37
slot: System board or motherboard
size: 8GiB
*-bank:0
description: DIMM [empty]
product: [Empty]
vendor: [Empty]
physical id: 0
serial: [REMOVED]
slot: ChannelA-DIMM0
*-bank:1
description: DIMM [empty]
product: [Empty]
vendor: [Empty]
physical id: 1
serial: [REMOVED]
slot: ChannelA-DIMM1
*-bank:2
description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product: 16KTF1G64HZ-1G6E1
vendor: Micron
physical id: 2
serial: [REMOVED]
slot: ChannelB-DIMM0
size: 8GiB
width: 64 bits
clock: 1600MHz (0.6ns)
*-bank:3
description: DIMM [empty]
product: [Empty]
vendor: [Empty]
physical id: 3
serial: [REMOVED]
slot: ChannelB-DIMM1
*-cpu
description: CPU
product: Core i5 (Fill By OEM)
vendor: Intel Corp.
physical id: 38
bus info: cpu@0
version: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
slot: SOCKET 0
size: 2600MHz
capacity: 3800MHz
width: 64 bits
clock: 100MHz
capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
configuration: cores=2 enabledcores=2 threads=4
*-pci
description: Host bridge
product: 3rd Gen Core processor DRAM Controller
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
resources: irq:42 ioport:e000(size=4096) memory:f7d00000-f7dfffff ioport:e0000000(size=268435456)
*-display UNCLAIMED
description: Display controller
product: Venus XT [Radeon HD 8870M]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi cap_list
configuration: latency=0
resources: memory:e0000000-efffffff memory:f7d00000-f7d3ffff ioport:e000(size=256) memory:f7d40000-f7d5ffff
*-display UNCLAIMED
description: VGA compatible controller
product: 3rd Gen Core processor Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller cap_list
configuration: latency=0
resources: memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)
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
resources: irq:44 memory:f7e00000-f7e0ffff
*-usbhost:0
product: xHCI Host Controller
vendor: Linux 3.13.1-3.gfc9498b-desktop xhci_hcd
physical id: 0
bus info: usb@4
logical name: usb4
version: 3.13
capabilities: usb-3.00
configuration: driver=hub slots=4 speed=5000Mbit/s
*-usbhost:1
product: xHCI Host Controller
vendor: Linux 3.13.1-3.gfc9498b-desktop xhci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 3.13
capabilities: usb-2.00
configuration: driver=hub slots=4 speed=480Mbit/s
*-usb:0
description: Mouse
product: USB Laser Mouse
vendor: Mouse
physical id: 2
bus info: usb@3:2
version: 0.00
capabilities: usb-2.00
configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
*-usb:1
description: Generic USB device
product: USB2.0-CRW
vendor: Generic
physical id: 3
bus info: usb@3:3
logical name: scsi6
version: 39.60
serial: [REMOVED]
capabilities: usb-2.00 emulated scsi-host
configuration: driver=rts5139 maxpower=500mA speed=480Mbit/s
*-disk
description: SCSI Disk
product: xD/SD/M.S.
vendor: Generic-
physical id: 0.0.0
bus info: scsi@6:0.0.0
logical name: /dev/sdb
version: 1.00
serial: [REMOVED]
capabilities: removable
configuration: logicalsectorsize=512 sectorsize=512
*-medium
physical id: 0
logical name: /dev/sdb
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
resources: irq:45 memory:f7e1a000-f7e1a00f
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
resources: irq:16 memory:f7e18000-f7e183ff
*-usbhost
product: EHCI Host Controller
vendor: Linux 3.13.1-3.gfc9498b-desktop ehci_hcd
physical id: 1
bus info: usb@1
logical name: usb1
version: 3.13
capabilities: usb-2.00
configuration: driver=hub slots=2 speed=480Mbit/s
*-usb
description: USB hub
product: Integrated Rate Matching Hub
vendor: Intel Corp.
physical id: 1
bus info: usb@1:1
version: 0.00
capabilities: usb-2.00
configuration: driver=hub slots=6 speed=480Mbit/s
*-usb:0
description: Video
product: WebCam SC-10HDP12631N
vendor: Namuga
physical id: 4
bus info: usb@1:1.4
version: 0.59
capabilities: usb-2.00
configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
*-usb:1
description: Human interface device
product: Atmel maXTouch Digitizer
vendor: Atmel
physical id: 5
bus info: usb@1:1.5
version: 10.32
capabilities: usb-2.00
configuration: driver=usbhid maxpower=250mA speed=12Mbit/s
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
resources: irq:47 memory:f7e10000-f7e13fff
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
resources: irq:16 memory:f7c00000-f7cfffff
*-network
description: Wireless interface
product: Centrino Advanced-N 6235
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlp2s0
version: 24
serial: [REMOVED]
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=3.13.1-3.gfc9498b-desktop firmware=18.168.6.1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
resources: irq:48 memory:f7c00000-f7c01fff
*-pci:2
description: PCI bridge
product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
vendor: Intel Corporation
physical id: 1c.3
bus info: pci@0000:00:1c.3
version: c4
width: 32 bits
clock: 33MHz
capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:19 ioport:d000(size=4096) ioport:f0000000(size=1048576)
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: enp3s0
version: 06
serial: [REMOVED]
size: 10Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:46 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
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
resources: irq:23 memory:f7e17000-f7e173ff
*-usbhost
product: EHCI Host Controller
vendor: Linux 3.13.1-3.gfc9498b-desktop ehci_hcd
physical id: 1
bus info: usb@2
logical name: usb2
version: 3.13
capabilities: usb-2.00
configuration: driver=hub slots=2 speed=480Mbit/s
*-usb
description: USB hub
product: Integrated Rate Matching Hub
vendor: Intel Corp.
physical id: 1
bus info: usb@2:1
version: 0.00
capabilities: usb-2.00
configuration: driver=hub slots=6 speed=480Mbit/s
*-usb
description: Bluetooth wireless interface
vendor: Intel Corp.
physical id: 5
bus info: usb@2:1.5
version: 78.69
capabilities: bluetooth usb-2.00
configuration: driver=btusb speed=12Mbit/s
*-isa
description: ISA bridge
product: HM76 Express Chipset LPC Controller
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: driver=lpc_ich latency=0
resources: irq:0
*-storage
description: SATA controller
product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
version: 04
width: 32 bits
clock: 66MHz
capabilities: storage msi pm ahci_1.0 bus_master cap_list
configuration: driver=ahci latency=0
resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e16000-f7e167ff
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
resources: memory:f7e15000-f7e150ff ioport:f040(size=32)
*-scsi
physical id: 1
logical name: scsi0
capabilities: emulated
*-disk
description: ATA Disk
product: ST1000LM024 HN-M
vendor: Seagate
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: 2AR1
serial: [REMOVED]
size: 931GiB (1TB)
capabilities: gpt-1.00 partitioned partitioned:gpt
configuration: ansiversion=5 guid=7d6024e0-3e20-4431-ad2f-480e57007ec0 logicalsectorsize=512 sectorsize=4096
*-volume:0
description: Windows NTFS volume
vendor: Windows
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
version: 3.1
serial: [REMOVED]
size: 497MiB
capacity: 498MiB
capabilities: boot precious readonly hidden nomount ntfs initialized
configuration: clustersize=4096 created=2013-04-15 19:34:01 filesystem=ntfs label=Windows RE tools modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
*-volume:1
description: Windows FAT volume
vendor: MSDOS5.0
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
logical name: /boot/efi
version: FAT32
serial: [REMOVED]
size: 276MiB
capacity: 299MiB
capabilities: boot fat initialized
configuration: FATs=2 filesystem=fat label=SYSTEM mount.fstype=vfat mount.options=rw,relatime,fmask=0002,dmask=0002,allow_utime=0020,codepage=437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro name=EFI system partition state=mounted
*-volume:2
description: reserved partition
vendor: Windows
physical id: 3
bus info: scsi@0:0.0.0,3
logical name: /dev/sda3
serial: [REMOVED]
capacity: 127MiB
capabilities: nofs
configuration: name=Microsoft reserved partition
*-volume:3
description: Windows NTFS volume
vendor: Windows
physical id: 4
bus info: scsi@0:0.0.0,4
logical name: /dev/sda4
version: 3.1
serial: [REMOVED]
size: 454GiB
capacity: 454GiB
capabilities: ntfs initialized
configuration: clustersize=4096 created=2013-04-15 19:34:05 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
*-volume:4
description: Windows NTFS volume
vendor: Windows
physical id: 5
bus info: scsi@0:0.0.0,5
logical name: /dev/sda5
version: 3.1
serial: [REMOVED]
size: 22GiB
capacity: 22GiB
capabilities: boot precious readonly hidden nomount ntfs initialized
configuration: clustersize=4096 created=2013-04-16 06:15:27 filesystem=ntfs label=SAMSUNG_REC2 modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
*-volume:5
description: Windows FAT volume
vendor: MSDOS5.0
physical id: 6
bus info: scsi@0:0.0.0,6
logical name: /dev/sda6
version: FAT32
serial: [REMOVED]
size: 997MiB
capacity: 1023MiB
capabilities: boot precious readonly hidden nomount fat initialized
configuration: FATs=2 filesystem=fat label=SAMSUNG_REC name=Basic data partition
*-volume:6
description: Linux swap volume
vendor: Windows
physical id: 7
bus info: scsi@0:0.0.0,7
logical name: /dev/sda7
version: 1
serial: [REMOVED]
size: 8199MiB
capacity: 8201MiB
capabilities: swap initialized
configuration: filesystem=swap name=primary pagesize=4095
*-volume:7
description: EXT4 volume
vendor: Linux
physical id: 8
bus info: scsi@0:0.0.0,8
logical name: /dev/sda8
logical name: /
version: 1.0
serial: [REMOVED]
size: 20GiB
capacity: 20GiB
capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration: created=2014-01-26 14:21:58 filesystem=ext4 lastmountpoint=/root modified=2014-02-09 02:32:03 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-02-09 02:32:03 name=primary state=mounted
*-volume:8
description: EXT4 volume
vendor: Linux
physical id: 9
bus info: scsi@0:0.0.0,9
logical name: /dev/sda9
logical name: /home
version: 1.0
serial: [REMOVED]
size: 204GiB
capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration: created=2014-01-26 14:22:04 filesystem=ext4 lastmountpoint=/home modified=2014-02-09 02:32:17 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-02-09 02:32:17 name=primary state=mounted
*-power UNCLAIMED
description: To Be Filled By O.E.M.
product: To Be Filled By O.E.M.
vendor: To Be Filled By O.E.M.
physical id: 1
version: To Be Filled By O.E.M.
serial: [REMOVED]
capacity: 32768mWh

```

---

