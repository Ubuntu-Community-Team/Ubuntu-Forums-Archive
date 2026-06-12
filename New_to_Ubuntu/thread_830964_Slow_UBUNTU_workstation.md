---
title: "Slow UBUNTU workstation"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by ejbest on 2008-06-16
Hello, I am new to this forum and ubuntu (if I should be posting elsewhere, please help me); however, I have been working with Linux for a great while. The system has installed and I am basically working (at a very slow pace) with everything seeming to function; however, it is very painfully slow. Opening browsers - going through system menus - just about everything is slow slow slow - and I do mean snails crawl slow.

Windows XP was screaming on this PC before crashing and now it is running ubuntu. Since I have seen other posting there hardware listing, I have pasted 'some' of mine.
description: Motherboard
product: P4P8T
vendor: ASUSTek Computer Inc.
physical id: 0
version: Rev 1.xx
serial: MB-1234567890
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 1003.001 (09/02/2004)
size: 64KiB
capacity: 448KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
*-cpu
description: CPU
product: Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 15.4.1
serial: 0000-0F41-0000-0000-0000-0000
slot: Socket 478
size: 3GHz
capacity: 3400MHz
width: 32 bits
clock: 200MHz
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
configuration: id=1
*-cache:0
description: L1 cache
physical id: 5
slot: L1-Cache
size: 16KiB
capacity: 16KiB
capabilities: pipeline-burst internal varies data
*-cache:1
description: L2 cache
physical id: 6
slot: L2-Cache
size: 1MiB
capacity: 1MiB
capabilities: pipeline-burst internal varies unified
*-cache:2 DISABLED
description: L3 cache
physical id: 7
slot: L3-Cache
capabilities: internal
*-logicalcpu:0
description: Logical CPU
physical id: 1.1
width: 32 bits
capabilities: logical
*-logicalcpu:1
description: Logical CPU
physical id: 1.2
width: 32 bits
capabilities: logical
*-memory
description: System Memory
physical id: 33
slot: System board or motherboard
size: 1002MiB
*-pci
description: Host bridge
product: 82865G/PE/P DRAM Controller/Host-Hub Interface
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 02
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-intel module=intel_agp
*-display UNCLAIMED
description: VGA compatible controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm vga_controller bus_master cap_list
configuration: latency=0
module=ata_piix
*-disk
description: ATA Disk
product: WDC WD1600AAJS-2
vendor: Western Digital
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sda
version: 05.0
serial: WD-WMAP94568614
size: 149GiB (160GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=000ddd5d
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@2:0.0.0,1
logical name: /dev/sda1
logical name: /
logical name: /dev/.static/dev
version: 1.0
serial: 112e2c6a-1e7b-45c3-af08-b0cf52dbe25f
size: 146GiB
capacity: 146GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration: created=2008-05-25 12:48:40 filesystem=ext3 modified=2008-06-08 11:28:18 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-06-07 23:08:16 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@2:0.0.0,2
logical name: /dev/sda2
size: 2933MiB
capacity: 2933MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 2933MiB
capabilities: nofs
*-serial UNCLAIMED
description: SMBus
product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
*-multimedia
description: Multimedia audio controller
product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
vendor: Intel Corporation
physical id: 1f.5
bus info: pci@0000:00:1f.5
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=0 module=snd_intel8x0
*-scsi
physical id: 1
bus info: usb@5:7
logical name: scsi4
capabilities: emulated scsi-host
configuration: driver=usb-storage
*-disk:0
description: SCSI Disk
product: CardReader CF
vendor: USB2.0
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
version: 0100
capabilities: removable
*-medium
physical id: 0
logical name: /dev/sdb
*-disk:1
description: SCSI Disk
product: CardReader MS
vendor: USB2.0
physical id: 0.0.1
bus info: scsi@4:0.0.1
logical name: /dev/sdc
version: 0100
capabilities: removable
*-medium
physical id: 0
logical name: /dev/sdc
*-disk:2
description: SCSI Disk
product: CardReader SD
vendor: USB2.0
physical id: 0.0.2
bus info: scsi@4:0.0.2
logical name: /dev/sdd
version: 0100
capabilities: removable
*-medium
physical id: 0
logical name: /dev/sdd
*-disk:3
description: SCSI Disk
product: CardReader SM XD
vendor: USB2.0
physical id: 0.0.3
bus info: scsi@4:0.0.3
logical name: /dev/sde
version: 0100
capabilities: removable
*-medium
physical id: 0
logical name: /dev/sde

---

### Post by cardinals_fan on 2008-06-16
Follow [these instructions]("http://urukrama.wordpress.com/openbox-guide/") to try Openbox.  They look scary, but it's not hard, and Openbox should be faster than regular Ubuntu (GNOME).

---

