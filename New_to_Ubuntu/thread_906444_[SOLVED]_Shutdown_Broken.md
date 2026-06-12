---
title: "[SOLVED] Shutdown Broken"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by .Garrett on 2008-08-31
Ok, so whenever I go to shut down Ubuntu, the bar will go all the way black, then the computer just hangs. Ubuntu is shutting down, but not actually powering off my computer.

I followed someone else's advice adding acpi=off to the end of the menu.lst kernel line, but to no avail.

---

### Post by .Garrett on 2008-08-31
It sems to be sporadic at best. Sometimes the screen will just go black, sometimes the menu will empty completely, and sometimes nothing will happen at all!

Please help.

---

### Post by porchrat on 2008-08-31
please post the output from this command:

```
dmesg
```

you may have to type sudo in font of that I can't quite remember and I'm not in front of an Ubuntu PC now.

By the way if you turn ACPI off then Ubuntu will halt and NOT turn off any of the hardware, as that is ACPI's job.

We need to see the ouput from dmesg in order to see how your machine is handling ACPI, but before we see it I can say that there are generally two ways to solve ACPI problems.

One is a kernel update and the other is a BIOS update.  Turning off ACPI will not solve the problem, just make the errors go away.

Please turn ACPI back on again before you run the dmesg command as we need to see the ACPI errors (if there are any) and the errors won't be accurate if ACPI=off.

Thanks

---

### Post by .Garrett on 2008-08-31
```

garrett@lifebook:~$ sudo dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f6f0000 (usable)
[    0.000000]  BIOS-e820: 000000004f6f0000 - 000000004f6fb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004f6fb000 - 000000004f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f700000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 374MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 325360) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   325360
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   325360
[    0.000000] On node 0 totalpages: 325360
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 749 pages used for memmap
[    0.000000]   HighMem zone: 95235 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec10000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322819
[    0.000000] Kernel command line: root=UUID=fa593083-d0e6-4f70-b2de-c79ca6588ee6 ro quiet splash acpi=off apm=power_off
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01a00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1700.012 MHz processor.
[    7.084831] Console: colour VGA+ 80x25
[    7.084836] console [tty0] enabled
[    7.085266] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.085764] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.143230] Memory: 1277752k/1301440k available (2177k kernel code, 22428k reserved, 1006k data, 368k init, 383936k highmem)
[    7.143241] virtual kernel memory layout:
[    7.143242]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.143243]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.143244]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.143246]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.143247]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.143248]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    7.143249]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    7.143253] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.143329] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.223312] Calibrating delay using timer specific routine.. 3402.22 BogoMIPS (lpj=6804442)
[    7.223359] Security Framework initialized
[    7.223373] SELinux:  Disabled at boot.
[    7.223398] AppArmor: AppArmor initialized
[    7.223403] Failure registering capabilities with primary security module.
[    7.223415] Mount-cache hash table entries: 512
[    7.223616] Initializing cgroup subsys ns
[    7.223624] Initializing cgroup subsys cpuacct
[    7.223640] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    7.223654] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.223657] CPU: L2 cache: 2048K
[    7.223661] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    7.223672] Compat vDSO mapped to ffffe000.
[    7.223692] Checking 'hlt' instruction... OK.
[    7.239759] SMP alternatives: switching to UP code
[    7.241836] Freeing SMP alternatives: 11k freed
[    7.241969] Early unpacking initramfs... done
[    7.606506] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    7.606515] SMP motherboard not detected.
[    7.606517] Local APIC not detected. Using dummy APIC emulation.
[    7.606564] Brought up 1 CPUs
[    7.606584] CPU0 attaching sched-domain:
[    7.606587]  domain 0: span 01
[    7.606589]   groups: 01
[    7.606778] net_namespace: 64 bytes
[    7.606786] Booting paravirtualized kernel on bare hardware
[    7.607252] Time: 14:02:14  Date: 08/31/08
[    7.607280] NET: Registered protocol family 16
[    7.607473] EISA bus registered
[    7.607743] PCI: PCI BIOS revision 2.10 entry at 0xfd982, last bus=3
[    7.607746] PCI: Using configuration type 1
[    7.607755] Setting up standard PCI resources
[    7.609367] ACPI: Interpreter disabled.
[    7.609371] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.609401] pnp: PnP ACPI: disabled
[    7.609405] PnPBIOS: Scanning system for PnP BIOS support...
[    7.609411] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5d90
[    7.609414] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71f, dseg 0x400
[    7.611658] PnPBIOS: 20 nodes reported by PnP BIOS; 20 recorded by driver
[    7.611860] PCI: Probing PCI hardware
[    7.611863] PCI: Probing PCI hardware (bus 00)
[    7.612259] PCI quirk: region fc00-fc7f claimed by ICH4 ACPI/GPIO/TCO
[    7.612263] PCI quirk: region fc80-fcbf claimed by ICH4 GPIO
[    7.612746] PCI: Transparent bridge - 0000:00:1e.0
[    7.613668] PCI: Using IRQ router PIIX/ICH [8086/24cc] at 0000:00:1f.0
[    7.613686] PCI: setting IRQ 11 as level-triggered
[    7.613688] PCI: Found IRQ 11 for device 0000:00:1f.1
[    7.613709] PCI: Sharing IRQ 11 with 0000:01:0d.0
[    7.631090] NET: Registered protocol family 8
[    7.631092] NET: Registered protocol family 20
[    7.631152] AppArmor: AppArmor Filesystem Enabled
[    7.631185] system 00:00: ioport range 0x4d0-0x4d1 has been reserved
[    7.631188] system 00:00: ioport range 0xf400-0xf47f has been reserved
[    7.631191] system 00:00: ioport range 0xf480-0xf4ff has been reserved
[    7.631194] system 00:00: ioport range 0xf800-0xf87f has been reserved
[    7.631197] system 00:00: ioport range 0xf880-0xf8ff has been reserved
[    7.631200] system 00:00: ioport range 0xfc00-0xfc7f has been reserved
[    7.631203] system 00:00: ioport range 0xfc80-0xfcbf has been reserved
[    7.631206] system 00:00: ioport range 0xfd00-0xfd6f has been reserved
[    7.631209] system 00:00: ioport range 0xff00-0xff1f has been reserved
[    7.631212] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[    7.631216] system 00:00: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    7.631226] system 00:0a: iomem range 0xccc00-0xcffff could not be reserved
[    7.631231] system 00:0b: iomem range 0xdc000-0xdffff has been reserved
[    7.631236] system 00:0c: ioport range 0xfe00-0xfe01 has been reserved
[    7.631242] system 00:0f: iomem range 0xffb00000-0xffbfffff could not be reserved
[    7.631623] PCI: Bus 2, cardbus bridge: 0000:01:0a.0
[    7.631625]   IO window: 00003400-000034ff
[    7.631629]   IO window: 00003800-000038ff
[    7.631632]   PREFETCH window: 64000000-67ffffff
[    7.631636]   MEM window: 68000000-6bffffff
[    7.631640] PCI: Bus 3, cardbus bridge: 0000:01:0a.1
[    7.631642]   IO window: 00003c00-00003cff
[    7.631645]   IO window: 00001000-000010ff
[    7.631648]   PREFETCH window: 6c000000-6fffffff
[    7.631652]   MEM window: 70000000-73ffffff
[    7.631655] PCI: Bridge: 0000:00:1e.0
[    7.631658]   IO window: 3000-3fff
[    7.631663]   MEM window: d0200000-d02fffff
[    7.631666]   PREFETCH window: disabled.
[    7.631678] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.631691] PCI: Found IRQ 11 for device 0000:01:0a.0
[    7.631695] PCI: Sharing IRQ 11 with 0000:00:02.0
[    7.631699] PCI: Sharing IRQ 11 with 0000:00:1d.0
[    7.631712] PCI: Sharing IRQ 11 with 0000:01:0a.2
[    7.631728] PCI: Found IRQ 11 for device 0000:01:0a.1
[    7.631740] PCI: Sharing IRQ 11 with 0000:00:1f.3
[    7.631743] PCI: Sharing IRQ 11 with 0000:00:1f.5
[    7.631746] PCI: Sharing IRQ 11 with 0000:00:1f.6
[    7.631751] PCI: Sharing IRQ 11 with 0000:01:0a.3
[    7.631754] PCI: Sharing IRQ 11 with 0000:01:0a.4
[    7.631767] NET: Registered protocol family 2
[    7.635080] Time: tsc clocksource has been installed.
[    7.667125] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.667357] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    7.668403] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    7.669083] TCP: Hash tables configured (established 131072 bind 65536)
[    7.669088] TCP reno registered
[    7.679246] checking if image is initramfs... it is
[    8.386403] Freeing initrd memory: 7301k freed
[    8.387064] audit: initializing netlink socket (disabled)
[    8.387085] audit(1220191334.248:1): initialized
[    8.387297] highmem bounce pool size: 64 pages
[    8.389152] VFS: Disk quotas dquot_6.5.1
[    8.389242] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.389452] io scheduler noop registered
[    8.389455] io scheduler anticipatory registered
[    8.389457] io scheduler deadline registered
[    8.389468] io scheduler cfq registered (default)
[    8.389485] Boot video device is 0000:00:02.0
[    8.389789] isapnp: Scanning for PnP cards...
[    8.743298] isapnp: No Plug & Play device found
[    8.770417] Real Time Clock Driver v1.12ac
[    8.770505] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.770623] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.770863] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    8.771377] 00:13: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.771564] PCI: Found IRQ 11 for device 0000:00:1f.6
[    8.771578] PCI: Sharing IRQ 11 with 0000:00:1f.3
[    8.771581] PCI: Sharing IRQ 11 with 0000:00:1f.5
[    8.771586] PCI: Sharing IRQ 11 with 0000:01:0a.1
[    8.771590] PCI: Sharing IRQ 11 with 0000:01:0a.3
[    8.771593] PCI: Sharing IRQ 11 with 0000:01:0a.4
[    8.772204] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.772275] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    8.772377] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    8.775111] i8042.c: Detected active multiplexing controller, rev 1.1.
[    8.776466] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.776471] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    8.776473] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    8.776476] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    8.776478] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    8.782588] mice: PS/2 mouse device common for all mice
[    8.782704] EISA: Probing bus 0 at eisa.0
[    8.782711] Cannot allocate resource for EISA slot 1
[    8.782713] Cannot allocate resource for EISA slot 2
[    8.782716] Cannot allocate resource for EISA slot 3
[    8.782735] EISA: Detected 0 cards.
[    8.782739] cpuidle: using governor ladder
[    8.782741] cpuidle: using governor menu
[    8.782846] NET: Registered protocol family 1
[    8.782874] Using IPI No-Shortcut mode
[    8.782912] registered taskstats version 1
[    8.783009]   Magic number: 4:787:31
[    8.783014]   hash matches device ttyde
[    8.783088] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    8.783090] EDD information not available.
[    8.783317] Freeing unused kernel memory: 368k freed
[    8.818430] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    9.998617] fuse init (API version 7.9)
[   10.026425] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   10.269709] usbcore: registered new interface driver usbfs
[   10.269738] usbcore: registered new interface driver hub
[   10.285625] usbcore: registered new device driver usb
[   10.297620] USB Universal Host Controller Interface driver v3.0
[   10.297698] PCI: Found IRQ 11 for device 0000:00:1d.0
[   10.297704] PCI: Sharing IRQ 11 with 0000:00:02.0
[   10.297720] PCI: Sharing IRQ 11 with 0000:01:0a.0
[   10.297724] PCI: Sharing IRQ 11 with 0000:01:0a.2
[   10.297740] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.297745] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.298188] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.298214] uhci_hcd 0000:00:1d.0: irq 11, io base 0x000020c0
[   10.298346] usb usb1: configuration #1 chosen from 1 choice
[   10.298370] hub 1-0:1.0: USB hub found
[   10.298376] hub 1-0:1.0: 2 ports detected
[   10.397619] 8139too Fast Ethernet driver 0.9.28
[   10.405224] PCI: Found IRQ 11 for device 0000:00:1d.1
[   10.405262] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.405266] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.405293] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.405319] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000020e0
[   10.405430] usb usb2: configuration #1 chosen from 1 choice
[   10.405456] hub 2-0:1.0: USB hub found
[   10.405462] hub 2-0:1.0: 2 ports detected
[   10.429761] SCSI subsystem initialized
[   10.481537] libata version 3.00 loaded.
[   10.505689] PCI: Found IRQ 11 for device 0000:00:1d.7
[   10.505722] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   10.505726] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   10.505752] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[   10.509666] ehci_hcd 0000:00:1d.7: debug port 1
[   10.509672] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   10.509680] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xd0100000
[   10.525465] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.525597] usb usb3: configuration #1 chosen from 1 choice
[   10.525622] hub 3-0:1.0: USB hub found
[   10.525629] hub 3-0:1.0: 4 ports detected
[   10.629620] PCI: Found IRQ 11 for device 0000:01:0a.2
[   10.629626] PCI: Sharing IRQ 11 with 0000:00:02.0
[   10.629629] PCI: Sharing IRQ 11 with 0000:00:1d.0
[   10.629641] PCI: Sharing IRQ 11 with 0000:01:0a.0
[   10.682362] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[d0200000-d02007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   10.753450] Floppy drive(s): fd0 is 1.44M
[   10.773614] FDC 0 is a post-1991 82077
[   10.777397] PCI: Found IRQ 11 for device 0000:01:0c.0
[   10.777960] eth0: RealTek RTL8139 at 0x3000, 00:0b:5d:71:b8:14, IRQ 11
[   10.777963] eth0:  Identified 8139 chip type 'RTL-8101'
[   10.781297] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   10.781304] PCI: Found IRQ 11 for device 0000:00:1f.1
[   10.781335] PCI: Sharing IRQ 11 with 0000:01:0d.0
[   10.781368] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.794286] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   10.816809] ata_piix 0000:00:1f.1: version 2.12
[   10.816830] PCI: Found IRQ 11 for device 0000:00:1f.1
[   10.816851] PCI: Sharing IRQ 11 with 0000:01:0d.0
[   10.816886] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.822849] scsi0 : ata_piix
[   10.825667] scsi1 : ata_piix
[   10.825703] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2420 irq 14
[   10.825707] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2428 irq 15
[   10.989716] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[   10.989721] ata1.00: 117210240 sectors, multi 16: LBA 
[   11.005704] ata1.00: configured for UDMA/100
[   11.057178] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   11.191566] usb 3-1: configuration #1 chosen from 2 choices
[   11.325403] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830S, 1.00, max UDMA/33
[   11.373045] usbcore: registered new interface driver libusual
[   11.379061] Initializing USB Mass Storage driver...
[   11.379913] scsi2 : SCSI emulation for USB Mass Storage devices
[   11.380315] usbcore: registered new interface driver usb-storage
[   11.380319] USB Mass Storage support registered.
[   11.380378] usb-storage: device found at 2
[   11.380380] usb-storage: waiting for device to settle before scanning
[   11.497217] ata2.00: configured for UDMA/33
[   11.497363] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[   11.499331] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
[   11.506971] Driver 'sd' needs updating - please use bus_type methods
[   11.507048] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   11.507061] sd 0:0:0:0: [sda] Write Protect is off
[   11.507064] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.507080] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.507129] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   11.507139] sd 0:0:0:0: [sda] Write Protect is off
[   11.507141] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.507156] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.507159]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   11.584003]  sda1 sda2 sda3
[   11.610820] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.616326] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.616344] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   11.621130] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.621134] Uniform CD-ROM driver Revision: 3.20
[   11.621180] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   11.744791] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   11.919964] Attempting manual resume
[   11.919969] swsusp: Resume From Partition 8:2
[   11.919971] PM: Checking swsusp image.
[   11.920167] PM: Resume from disk failed.
[   11.922574] usb 2-1: configuration #1 chosen from 1 choice
[   11.933887] EXT3-fs: INFO: recovery required on readonly filesystem.
[   11.933891] EXT3-fs: write access will be enabled during recovery.
[   11.965054] usbcore: registered new interface driver hiddev
[   11.979764] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[   11.988676] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   12.002462] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   12.002473] usbcore: registered new interface driver usbhid
[   12.002476] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.049321] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e10030466ad]
[   14.569060] kjournald starting.  Commit interval 5 seconds
[   14.569080] EXT3-fs: sda3: orphan cleanup on readonly fs
[   14.935257] ext3_orphan_cleanup: deleting unreferenced inode 1151494
[   14.935296] ext3_orphan_cleanup: deleting unreferenced inode 1180471
[   14.953795] ext3_orphan_cleanup: deleting unreferenced inode 1146945
[   14.971877] ext3_orphan_cleanup: deleting unreferenced inode 419878
[   14.971885] ext3_orphan_cleanup: deleting unreferenced inode 418334
[   14.971890] EXT3-fs: sda3: 5 orphan inodes deleted
[   14.971892] EXT3-fs: recovery complete.
[   15.004438] EXT3-fs: mounted filesystem with ordered data mode.
[   16.374440] usb-storage: device scan complete
[   16.375198] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   16.732960] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[   16.734083] sd 2:0:0:0: [sdb] Write Protect is off
[   16.734086] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   16.734089] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   16.736329] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[   16.737455] sd 2:0:0:0: [sdb] Write Protect is off
[   16.737458] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   16.737460] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   16.737463]  sdb: sdb1 sdb2
[   16.769233] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   16.769268] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   27.292079] Linux agpgart interface v0.102
[   27.416172] agpgart: Detected an Intel 855GM Chipset.
[   27.416873] agpgart: Detected 8060K stolen memory.
[   27.425853] agpgart: AGP aperture is 128M @ 0xd8000000
[   27.675917] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.721196] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.755836] iTCO_vendor_support: vendor-support=0
[   27.771798] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   27.771894] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   27.771905] iTCO_wdt: No card detected
[   27.987837] intel_rng: FWH not detected
[   28.011781] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   28.939361] Yenta: CardBus bridge found at 0000:01:0a.0 [10cf:1254]
[   29.047090] ieee80211_crypt: registered algorithm 'NULL'
[   29.067717] Yenta: ISA IRQ mask 0x06b8, PCI irq 11
[   29.067721] Socket status: 30000006
[   29.067725] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   29.067728] cs: IO port probe 0x3000-0x3fff: clean.
[   29.067969] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   29.073884] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   29.073887] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   29.085062] Yenta: CardBus bridge found at 0000:01:0a.1 [10cf:1254]
[   29.211649] Yenta: ISA IRQ mask 0x06b8, PCI irq 11
[   29.211654] Socket status: 30000006
[   29.211657] Yenta: Raising subordinate bus# of parent bus (#01) from #03 to #06
[   29.211664] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   29.211667] cs: IO port probe 0x3000-0x3fff: clean.
[   29.211908] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   29.306950] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   29.306955] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   29.307058] PCI: Found IRQ 11 for device 0000:01:0d.0
[   29.307071] PCI: Sharing IRQ 11 with 0000:00:1f.1
[   29.385524] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   29.642633] input: PS/2 Mouse as /devices/virtual/input/input4
[   29.667078] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input5
[   30.724347] parport_pc 00:17: reported by Plug and Play BIOS
[   30.724378] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   30.761665] irda_init()
[   30.761682] NET: Registered protocol family 23
[   30.774290] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   30.774305] smsc_superio_flat(): fir: 0x400, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[   30.774312] smsc_ircc_present: can't get sir_base of 0x2e8
[   31.606871] ipw2200: Radio Frequency Kill Switch is On:
[   31.606875] Kill switch must be turned off for wireless networking to work.
[   31.737876] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   31.737934] PCI: Found IRQ 11 for device 0000:00:1f.5
[   31.737950] PCI: Sharing IRQ 11 with 0000:00:1f.3
[   31.737954] PCI: Sharing IRQ 11 with 0000:00:1f.6
[   31.737959] PCI: Sharing IRQ 11 with 0000:01:0a.1
[   31.737963] PCI: Sharing IRQ 11 with 0000:01:0a.3
[   31.737967] PCI: Sharing IRQ 11 with 0000:01:0a.4
[   31.737999] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   32.006384] cs: IO port probe 0x100-0x3af: clean.
[   32.007941] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
[   32.008585] cs: IO port probe 0x820-0x8ff: clean.
[   32.009144] cs: IO port probe 0xc00-0xcf7: clean.
[   32.009864] cs: IO port probe 0xa00-0xaff: clean.
[   32.022161] cs: IO port probe 0x100-0x3af: clean.
[   32.023713] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
[   32.024356] cs: IO port probe 0x820-0x8ff: clean.
[   32.024916] cs: IO port probe 0xc00-0xcf7: clean.
[   32.025640] cs: IO port probe 0xa00-0xaff: clean.
[   32.565088] intel8x0_measure_ac97_clock: measured 55482 usecs
[   32.565090] intel8x0: clocking to 48000
[   33.474358] lp0: using parport0 (interrupt-driven).
[   33.552374] apm: BIOS not found.
[   33.613589] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[   34.140595] EXT3 FS on sda3, internal journal
[   35.398113] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.403794] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   36.403850] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   36.404036] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   36.404121] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   37.656735] NET: Registered protocol family 10
[   37.657228] lo: Disabled Privacy Extensions
[   37.916809] apm: BIOS not found.
[   38.066963] ppdev: user-space parallel port driver
[   38.363061] audit(1220216565.009:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4681 profile="/usr/sbin/cupsd" namespace="default"
[   40.690814] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   40.705652] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   40.849395] Bluetooth: Core ver 2.11
[   40.850184] NET: Registered protocol family 31
[   40.850187] Bluetooth: HCI device and connection manager initialized
[   40.850192] Bluetooth: HCI socket layer initialized
[   40.904941] Bluetooth: L2CAP ver 2.9
[   40.904946] Bluetooth: L2CAP socket layer initialized
[   40.940477] Bluetooth: RFCOMM socket layer initialized
[   40.940493] Bluetooth: RFCOMM TTY layer initialized
[   40.940494] Bluetooth: RFCOMM ver 1.8
[   44.334501] NET: Registered protocol family 17
[   44.854428] [drm] Initialized drm 1.1.0 20060810
[   44.858832] PCI: Found IRQ 11 for device 0000:00:02.0
[   44.858841] PCI: Sharing IRQ 11 with 0000:00:1d.0
[   44.858854] PCI: Sharing IRQ 11 with 0000:01:0a.0
[   44.858859] PCI: Sharing IRQ 11 with 0000:01:0a.2
[   44.858867] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.858942] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   44.858951] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   44.858995] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   59.082202] eth0: no IPv6 routers present
[  895.318764] usb 3-1: USB disconnect, address 2
[  897.083745] usb 3-1: new high speed USB device using ehci_hcd and address 4
[  897.217992] usb 3-1: configuration #1 chosen from 2 choices
[  897.237677] scsi3 : SCSI emulation for USB Mass Storage devices
[  897.244003] usb-storage: device found at 4
[  897.244007] usb-storage: waiting for device to settle before scanning
[  902.241215] usb-storage: device scan complete
[  902.241975] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  902.256855] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  902.257927] sd 3:0:0:0: [sdb] Write Protect is off
[  902.257931] sd 3:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  902.257933] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  902.259923] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  902.261174] sd 3:0:0:0: [sdb] Write Protect is off
[  902.261178] sd 3:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  902.261180] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  902.261185]  sdb: sdb1 sdb2
[  902.278213] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  902.278261] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

That's it.

---

### Post by porchrat on 2008-08-31
I can see that you have "acpi=off" in your /boot/grub/menu.lst

Try changing "acpi=off" to "acpi=force"

Then save it and then reboot.

Please before you do this make a copy of your menu.lst just in case you need to reload it later.

Do that by typing this:

```
cd /boot/grub
sudo mkdir backup
sudo cp menu.lst backup/menu.lst.old
```

You will then have a backup stored in /boot/grub/backup named menu.lst.old so that if the menu.lst becomes corrupted you can reload the old menu.lst and still boot properly.  It's just safer that way.

---

### Post by .Garrett on 2008-08-31
Here's my menu.lst entry:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

root		(hd0,2)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fa593083-d0e6-4f70-b2de-c79ca6588ee6 ro quiet splash acpi=force apm=power_off

initrd		/boot/initrd.img-2.6.24-19-generic

quiet


```

And dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f6f0000 (usable)
[    0.000000]  BIOS-e820: 000000004f6f0000 - 000000004f6fb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004f6fb000 - 000000004f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f700000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 374MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 325360) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   325360
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   325360
[    0.000000] On node 0 totalpages: 325360
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 749 pages used for memmap
[    0.000000]   HighMem zone: 95235 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5D50 checksum 0
[    0.000000] ACPI: RSDP 000F5D50, 0014 (r0 FUJ   )
[    0.000000] ACPI: RSDT 4F6F56C9, 0030 (r1 FUJ    FJNB18F   1040000 FUJ       100)
[    0.000000] ACPI: FACP 4F6FAF8C, 0074 (r1 FUJ    FJNB18F   1040000 FUJ       100)
[    0.000000] ACPI: DSDT 4F6F56F9, 5449 (r1 FUJ    FJNB18F   1040000 MSFT  100000E)
[    0.000000] ACPI: FACS 4F6FBFC0, 0040
[    0.000000] ACPI: SSDT 4F6FAB42, 0296 (r1 FUJ    FJNB18F   1040000 INTL 20030522)
[    0.000000] ACPI: BOOT 4F6FAF64, 0028 (r1 FUJ    FJNB18F   1040000 FUJ       100)
[    0.000000] ACPI: PM-Timer IO Port: 0xfc08
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec10000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322819
[    0.000000] Kernel command line: root=UUID=fa593083-d0e6-4f70-b2de-c79ca6588ee6 ro quiet splash acpi=force apm=power_off
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01a00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1700.012 MHz processor.
[    6.947327] Console: colour VGA+ 80x25
[    6.947332] console [tty0] enabled
[    6.947725] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    6.948214] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.005664] Memory: 1277752k/1301440k available (2177k kernel code, 22428k reserved, 1006k data, 368k init, 383936k highmem)
[    7.005673] virtual kernel memory layout:
[    7.005674]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.005676]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.005677]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.005678]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.005679]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.005681]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    7.005682]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    7.005685] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.005759] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.085740] Calibrating delay using timer specific routine.. 3402.21 BogoMIPS (lpj=6804432)
[    7.085786] Security Framework initialized
[    7.085800] SELinux:  Disabled at boot.
[    7.085825] AppArmor: AppArmor initialized
[    7.085830] Failure registering capabilities with primary security module.
[    7.085841] Mount-cache hash table entries: 512
[    7.086041] Initializing cgroup subsys ns
[    7.086050] Initializing cgroup subsys cpuacct
[    7.086067] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    7.086080] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.086083] CPU: L2 cache: 2048K
[    7.086087] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    7.086099] Compat vDSO mapped to ffffe000.
[    7.086117] Checking 'hlt' instruction... OK.
[    7.102187] SMP alternatives: switching to UP code
[    7.104255] Freeing SMP alternatives: 11k freed
[    7.104390] Early unpacking initramfs... done
[    7.468320] ACPI: Core revision 20070126
[    7.468395] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.470474] ACPI: setting ELCR to 0200 (from 0800)
[    7.483571] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    7.483582] SMP motherboard not detected.
[    7.483584] Local APIC not detected. Using dummy APIC emulation.
[    7.483641] Brought up 1 CPUs
[    7.483659] CPU0 attaching sched-domain:
[    7.483662]  domain 0: span 01
[    7.483664]   groups: 01
[    7.483865] net_namespace: 64 bytes
[    7.483874] Booting paravirtualized kernel on bare hardware
[    7.484328] Time: 16:05:05  Date: 08/31/08
[    7.484358] NET: Registered protocol family 16
[    7.484548] EISA bus registered
[    7.484562] ACPI: bus type pci registered
[    7.484801] PCI: PCI BIOS revision 2.10 entry at 0xfd982, last bus=3
[    7.484803] PCI: Using configuration type 1
[    7.484813] Setting up standard PCI resources
[    7.486870] ACPI: EC: Look up EC in DSDT
[    7.492527] ACPI: Interpreter enabled
[    7.492531] ACPI: (supports S0 S3 S4 S5)
[    7.492546] ACPI: Using PIC for interrupt routing
[    7.498428] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.498828] PCI quirk: region fc00-fc7f claimed by ICH4 ACPI/GPIO/TCO
[    7.498831] PCI quirk: region fc80-fcbf claimed by ICH4 GPIO
[    7.499312] PCI: Transparent bridge - 0000:00:1e.0
[    7.499403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.499476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    7.501390] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11)
[    7.501498] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11)
[    7.501616] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11)
[    7.501723] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11)
[    7.501830] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    7.501937] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    7.502045] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    7.502153] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11)
[    7.502258] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.502288] pnp: PnP ACPI init
[    7.502294] ACPI: bus type pnp registered
[    7.506131] pnp: PnP ACPI: found 12 devices
[    7.506133] ACPI: ACPI bus type pnp unregistered
[    7.506138] PnPBIOS: Disabled by ACPI PNP
[    7.506346] PCI: Using ACPI for IRQ routing
[    7.506349] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.521502] NET: Registered protocol family 8
[    7.521504] NET: Registered protocol family 20
[    7.521564] AppArmor: AppArmor Filesystem Enabled
[    7.525493] Time: tsc clocksource has been installed.
[    7.533523] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    7.533526] system 00:01: ioport range 0xf400-0xf47f has been reserved
[    7.533529] system 00:01: ioport range 0xf480-0xf4ff has been reserved
[    7.533532] system 00:01: ioport range 0xf800-0xf87f has been reserved
[    7.533535] system 00:01: ioport range 0xf880-0xf8ff has been reserved
[    7.533538] system 00:01: ioport range 0xfc00-0xfc7f has been reserved
[    7.533541] system 00:01: ioport range 0xfc80-0xfcbf has been reserved
[    7.533544] system 00:01: ioport range 0xfd00-0xfd6f has been reserved
[    7.533547] system 00:01: ioport range 0xfe00-0xfe01 has been reserved
[    7.533549] system 00:01: ioport range 0xff00-0xff1f has been reserved
[    7.533553] system 00:01: iomem range 0xccc00-0xcffff could not be reserved
[    7.533556] system 00:01: iomem range 0xffb00000-0xffbfffff could not be reserved
[    7.533559] system 00:01: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    7.563943] PCI: Bus 2, cardbus bridge: 0000:01:0a.0
[    7.563946]   IO window: 00003400-000034ff
[    7.563950]   IO window: 00003800-000038ff
[    7.563953]   PREFETCH window: 64000000-67ffffff
[    7.563957]   MEM window: 68000000-6bffffff
[    7.563960] PCI: Bus 3, cardbus bridge: 0000:01:0a.1
[    7.563962]   IO window: 00003c00-00003cff
[    7.563966]   IO window: 00001000-000010ff
[    7.563969]   PREFETCH window: 6c000000-6fffffff
[    7.563973]   MEM window: 70000000-73ffffff
[    7.563976] PCI: Bridge: 0000:00:1e.0
[    7.563979]   IO window: 3000-3fff
[    7.563984]   MEM window: d0200000-d02fffff
[    7.563987]   PREFETCH window: disabled.
[    7.563999] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.564135] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    7.564138] PCI: setting IRQ 11 as level-triggered
[    7.564142] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.564267] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    7.564270] ACPI: PCI Interrupt 0000:01:0a.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    7.564283] NET: Registered protocol family 2
[    7.601511] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.601740] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    7.602715] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    7.603327] TCP: Hash tables configured (established 131072 bind 65536)
[    7.603331] TCP reno registered
[    7.613625] checking if image is initramfs... it is
[    8.065212] Switched to high resolution mode on CPU 0
[    8.321561] Freeing initrd memory: 7301k freed
[    8.321838] Simple Boot Flag at 0x7f set to 0x1
[    8.322207] audit: initializing netlink socket (disabled)
[    8.322228] audit(1220198706.312:1): initialized
[    8.322437] highmem bounce pool size: 64 pages
[    8.324376] VFS: Disk quotas dquot_6.5.1
[    8.324457] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.324617] io scheduler noop registered
[    8.324619] io scheduler anticipatory registered
[    8.324621] io scheduler deadline registered
[    8.324632] io scheduler cfq registered (default)
[    8.324650] Boot video device is 0000:00:02.0
[    8.325037] isapnp: Scanning for PnP cards...
[    8.678575] isapnp: No Plug & Play device found
[    8.705753] Real Time Clock Driver v1.12ac
[    8.705865] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.705988] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.706234] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    8.706705] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.706900] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    8.706911] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    8.707537] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.707613] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    8.707712] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    8.710414] i8042.c: Detected active multiplexing controller, rev 1.1.
[    8.712177] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.712181] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    8.712184] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    8.712186] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    8.712189] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    8.713004] mice: PS/2 mouse device common for all mice
[    8.713118] EISA: Probing bus 0 at eisa.0
[    8.713125] Cannot allocate resource for EISA slot 1
[    8.713128] Cannot allocate resource for EISA slot 2
[    8.713130] Cannot allocate resource for EISA slot 3
[    8.713149] EISA: Detected 0 cards.
[    8.713153] cpuidle: using governor ladder
[    8.713155] cpuidle: using governor menu
[    8.713261] NET: Registered protocol family 1
[    8.713290] Using IPI No-Shortcut mode
[    8.713329] registered taskstats version 1
[    8.713441]   Magic number: 4:552:86
[    8.713539] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    8.713541] EDD information not available.
[    8.713771] Freeing unused kernel memory: 368k freed
[    8.748741] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    9.928053] fuse init (API version 7.9)
[    9.948370] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.555666] usbcore: registered new interface driver usbfs
[   10.555694] usbcore: registered new interface driver hub
[   10.576444] usbcore: registered new device driver usb
[   10.616994] SCSI subsystem initialized
[   10.629904] USB Universal Host Controller Interface driver v3.0
[   10.629971] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.629985] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.629989] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.630459] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.630484] uhci_hcd 0000:00:1d.0: irq 11, io base 0x000020c0
[   10.630629] usb usb1: configuration #1 chosen from 1 choice
[   10.630657] hub 1-0:1.0: USB hub found
[   10.630663] hub 1-0:1.0: 2 ports detected
[   10.695341] libata version 3.00 loaded.
[   10.731784] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   10.731790] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   10.731803] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.731808] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.731834] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.731857] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000020e0
[   10.731974] usb usb2: configuration #1 chosen from 1 choice
[   10.732000] hub 2-0:1.0: USB hub found
[   10.732006] hub 2-0:1.0: 2 ports detected
[   10.732062] 8139too Fast Ethernet driver 0.9.28
[   10.835819] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   10.835825] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   10.835840] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   10.835844] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   10.835872] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[   10.839794] ehci_hcd 0000:00:1d.7: debug port 1
[   10.839800] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   10.839809] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xd0100000
[   10.855395] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.855504] usb usb3: configuration #1 chosen from 1 choice
[   10.855530] hub 3-0:1.0: USB hub found
[   10.855536] hub 3-0:1.0: 4 ports detected
[   10.923448] Floppy drive(s): fd0 is 1.44M
[   10.943541] FDC 0 is a post-1991 82077
[   10.959710] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   10.959714] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   10.960257] eth0: RealTek RTL8139 at 0x3000, 00:0b:5d:71:b8:14, IRQ 11
[   10.960260] eth0:  Identified 8139 chip type 'RTL-8101'
[   10.963589] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   10.963723] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.963725] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.963761] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.963774] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   10.963991] ACPI: PCI Interrupt 0000:01:0a.2[C] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.016699] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[d0200000-d02007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   11.025601] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.035526] ata_piix 0000:00:1f.1: version 2.12
[   11.035544] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   11.035582] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.036303] scsi0 : ata_piix
[   11.036779] scsi1 : ata_piix
[   11.037520] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2420 irq 14
[   11.037523] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2428 irq 15
[   11.199686] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[   11.199691] ata1.00: 117210240 sectors, multi 16: LBA 
[   11.215637] ata1.00: configured for UDMA/100
[   11.391064] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   11.525929] usb 3-1: configuration #1 chosen from 1 choice
[   11.535363] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830S, 1.00, max UDMA/33
[   11.707198] ata2.00: configured for UDMA/33
[   11.707345] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[   11.707703] usbcore: registered new interface driver libusual
[   11.713987] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
[   11.714112] Initializing USB Mass Storage driver...
[   11.715196] scsi2 : SCSI emulation for USB Mass Storage devices
[   11.715494] usbcore: registered new interface driver usb-storage
[   11.715497] USB Mass Storage support registered.
[   11.715564] usb-storage: device found at 2
[   11.715565] usb-storage: waiting for device to settle before scanning
[   11.720221] Driver 'sd' needs updating - please use bus_type methods
[   11.720296] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   11.720309] sd 0:0:0:0: [sda] Write Protect is off
[   11.720312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.720327] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.720376] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   11.720386] sd 0:0:0:0: [sda] Write Protect is off
[   11.720388] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.720403] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.720407]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   11.802592]  sda1 sda2 sda3
[   11.829413] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.834850] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.834868] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   11.839973] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.839977] Uniform CD-ROM driver Revision: 3.20
[   11.840022] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.088421] Attempting manual resume
[   12.088426] swsusp: Resume From Partition 8:2
[   12.088427] PM: Checking swsusp image.
[   12.088639] PM: Resume from disk failed.
[   12.110612] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   12.118567] kjournald starting.  Commit interval 5 seconds
[   12.118611] EXT3-fs: mounted filesystem with ordered data mode.
[   12.288087] usb 2-1: configuration #1 chosen from 1 choice
[   12.302563] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e10030466ad]
[   16.711831] usb-storage: device scan complete
[   16.712325] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[   16.713543] sd 2:0:0:0: [sdb] 1952256 512-byte hardware sectors (1000 MB)
[   16.714167] sd 2:0:0:0: [sdb] Write Protect is off
[   16.714170] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   16.714173] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   16.716788] sd 2:0:0:0: [sdb] 1952256 512-byte hardware sectors (1000 MB)
[   16.717415] sd 2:0:0:0: [sdb] Write Protect is off
[   16.717417] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   16.717419] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   16.717422]  sdb: unknown partition table
[   16.719580] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   16.719618] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   24.696932] Linux agpgart interface v0.102
[   24.822613] agpgart: Detected an Intel 855GM Chipset.
[   24.823242] agpgart: Detected 8060K stolen memory.
[   24.832626] agpgart: AGP aperture is 128M @ 0xd8000000
[   25.042408] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.074462] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.126336] iTCO_vendor_support: vendor-support=0
[   25.178312] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.178443] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   25.178453] iTCO_wdt: No card detected
[   25.235388] input: Power Button (FF) as /devices/virtual/input/input2
[   25.250264] ACPI: Power Button (FF) [PWRF]
[   25.250371] input: Power Button (CM) as /devices/virtual/input/input3
[   25.262224] ACPI: Power Button (CM) [PWRB]
[   25.262291] input: Lid Switch as /devices/virtual/input/input4
[   25.262385] ACPI: Lid Switch [LID]
[   25.289072] ACPI: AC Adapter [AC] (on-line)
[   25.404548] intel_rng: FWH not detected
[   25.434994] ACPI: Battery Slot [CMB1] (battery present)
[   26.294091] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   26.305586] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.613056] Yenta: CardBus bridge found at 0000:01:0a.0 [10cf:1254]
[   27.741228] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   27.741233] Socket status: 30000006
[   27.741237] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   27.741240] cs: IO port probe 0x3000-0x3fff: clean.
[   27.741484] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   27.756658] ieee80211_crypt: registered algorithm 'NULL'
[   27.807099] Yenta: CardBus bridge found at 0000:01:0a.1 [10cf:1254]
[   27.912565] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   27.912571] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   27.933092] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   27.933095] Socket status: 30000006
[   27.933098] Yenta: Raising subordinate bus# of parent bus (#01) from #03 to #06
[   27.933105] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   27.933108] cs: IO port probe 0x3000-0x3fff: clean.
[   27.933349] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   28.200567] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   28.200572] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   28.200684] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.292306] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   28.589183] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   28.804246] input: PS/2 Mouse as /devices/virtual/input/input7
[   28.836685] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   28.977292] irda_init()
[   28.977313] NET: Registered protocol family 23
[   29.039927] parport_pc 00:0a: reported by Plug and Play ACPI
[   29.039958] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   29.089129] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   29.089145] smsc_superio_flat(): fir: 0x400, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[   29.089151] smsc_ircc_present: can't get sir_base of 0x2e8
[   29.152196] usbcore: registered new interface driver hiddev
[   29.167470] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input9
[   29.223763] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   29.237120] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1
[   29.237139] usbcore: registered new interface driver usbhid
[   29.237143] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.313839] ipw2200: Radio Frequency Kill Switch is On:
[   30.313842] Kill switch must be turned off for wireless networking to work.
[   30.588392] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   30.588460] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   30.588496] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   30.691071] cs: IO port probe 0x100-0x3af: clean.
[   30.692629] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
[   30.693274] cs: IO port probe 0x820-0x8ff: clean.
[   30.693835] cs: IO port probe 0xc00-0xcf7: clean.
[   30.694544] cs: IO port probe 0xa00-0xaff: clean.
[   30.715190] cs: IO port probe 0x100-0x3af: clean.
[   30.716744] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
[   30.717388] cs: IO port probe 0x820-0x8ff: clean.
[   30.717948] cs: IO port probe 0xc00-0xcf7: clean.
[   30.718657] cs: IO port probe 0xa00-0xaff: clean.
[   31.414311] intel8x0_measure_ac97_clock: measured 55478 usecs
[   31.414316] intel8x0: clocking to 48000
[   31.754014] lp0: using parport0 (interrupt-driven).
[   31.832033] apm: BIOS not found.
[   31.893252] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[   32.538337] EXT3 FS on sda3, internal journal
[   33.905916] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.645970] No dock devices found.
[   36.549640] NET: Registered protocol family 10
[   36.550129] lo: Disabled Privacy Extensions
[   36.809677] apm: BIOS not found.
[   37.002595] ppdev: user-space parallel port driver
[   37.313491] audit(1220223935.675:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4963 profile="/usr/sbin/cupsd" namespace="default"
[  106.232386] Marking TSC unstable due to: cpufreq changes.
[  106.243656] Time: acpi_pm clocksource has been installed.
[  106.795443] Clocksource tsc unstable (delta = -323554803 ns)
[   38.446234] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   38.461320] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[  109.412332] Bluetooth: Core ver 2.11
[  109.413452] NET: Registered protocol family 31
[  109.413461] Bluetooth: HCI device and connection manager initialized
[  109.413470] Bluetooth: HCI socket layer initialized
[   38.638581] Bluetooth: L2CAP ver 2.9
[   38.638584] Bluetooth: L2CAP socket layer initialized
[   38.715456] Bluetooth: RFCOMM socket layer initialized
[   38.715476] Bluetooth: RFCOMM TTY layer initialized
[   38.715477] Bluetooth: RFCOMM ver 1.8
[  114.919933] NET: Registered protocol family 17
[   41.213083] [drm] Initialized drm 1.1.0 20060810
[   41.216951] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.216961] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.217030] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.217040] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   41.217083] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  134.197723] eth0: no IPv6 routers present

```

---

### Post by porchrat on 2008-08-31
If you perform a shutdown now does it shutdown properly, or does linux halt without shutting down any of the hardware?

Give it a try as I can't see any serious errors within that dmesg that would cause a problem with ACPI.

Something else you could try is to add "clocksource=acpi_pm" to your /boot/grub/menu.lst but do that only if it still won't bring down all the hardware automatically.

That should help with those tsc clocksource errors you see there in the dmesg.  It looks like you're using CPU scaling or something.  I don't believe that is causing your shutdown problem, but it is worth a try and I once again ask that you recreate that backup before you add that line as it has caused problems on some systems.  This is done like this:

```
cd /boot/grub
sudo mkdir backup
sudo cp menu.lst backup/menu.lst.old
```

If you encounter a problem whereby you cannot boot then pls launch ubuntu from the "recovery" option in the grub menu and do a ```
sudo cp /boot/grub/backup/menu.lst.old /boot/grub/menu.lst
``` in order to reload the old version

---

### Post by .Garrett on 2008-08-31
Everything works now. Thanks :D

---

### Post by porchrat on 2008-08-31
glad to be of service friend :)...please mark the thead as solved.

---

### Post by .Garrett on 2008-08-31
Ooooookay, never mind. Now when I shut down or restart the screen just goes black, and everything stays on.

I haven't changed anything since. :(

---

### Post by porchrat on 2008-09-01
How old is the machine you are running ubuntu on?  I don't understand why you would need that "apm" setting as ACPI should perform all apm functions as apm is really old now.

Don't worry about the black screen thing, I was hoping the acpi=force would work for you. A lot of people experience the black screen with those settings and it is completely reversible by merely replacing your modified /boot/grub/menu.lst with the backup you made.  To do that you type this:

```
sudo cp /boot/grub/backup/menu.lst.old /boot/grub/menu.lst
```

However before you try that let us know how old the computer is.

---

### Post by Stunt Double on 2008-09-01
After Ubuntu shuts down, wait for the lights to flash at the top right of your keyboard, then just shut it off at the power bar. I do it all the time with no problems.

---

### Post by 4Orbs on 2008-09-01
> After Ubuntu shuts down, wait for the lights to flash at the top right of your keyboard, then just shut it off at the power bar. I do it all the time with no problems.

I have tried more than a dozen Linux distros, and none of them will turn off the power at shutdown. My main concern is the horrible sound the hard drive makes when it spins down to stop. I found a thread on the forums here that offered a suggestion, I followed the suggestion and, by golly, it worked for me. It stopped the terrible HDD noise and shuts off the power as expected.

First, open the /etc/modules file as root in your text editor. If you use Xubuntu use mousepad rather than gedit text editor:
```
gksudo gedit /etc/modules
```

Then add this on the bottom as the last line of the file. Then save and close the text editor:
```
apm power_off=1
```

You gotta reboot once before it will work correctly.

As I said, it works for me in all versions of Ubuntu and Ubuntu derivatives that I have tried.

---

### Post by .Garrett on 2008-09-01
My laptop's about 3 years old - Built for XP SP2, Intel centrino, etc.

I had ubuntu (gutsy) installed on a 10-year-old machine before, and it worked fine.


It seems having can-suspend and can-hibernate set to true in the config editor is what's causing the problem. Disabling those fixes everything, so I'll just go without. :)

---

### Post by porchrat on 2008-09-01
Awesome I'm glad it is sorted.  Sorry we couldn't be of more assistance.

On a side note does your machine really suspend and hibernate properly with all those ACPI problems??

---

### Post by .Garrett on 2008-09-01
Yeah, it actually did. Having them enabled made shutdown and restart not work though. :|

---

### Post by rebaccawood911 on 2008-10-07
Thanks for valuable informations for shutdown broken.Below the codes are very useful for me and getting the shutdown broken problem, i need to use your codes
Code:
cd /boot/grub
sudo mkdir backup
sudo cp menu.lst backup/menu.lst.old
Code:
sudo cp /boot/grub/backup/menu.lst.old /boot/grub/menu.lst

---

