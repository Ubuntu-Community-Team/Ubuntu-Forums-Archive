---
title: "LIRC error message on startup"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by helixed on 2008-09-09
Hello everybody,

I have a repurposed machine on which I'm running Ubuntu as a media PC.  I use XBMC as my media center, and I have an IR remote set up with LIRC.  Every time I turn on the computer it displays an error message.  Foe some reason the text is too small a font to be completely legible.  The only words I can make out in the message are lirc and $HOME.  Does anybody know how I can check what this message says, and more importantly how I can fix this problem?

Thanks,

helixed

---

### Post by bawilson2 on 2008-09-10
After booting you should be able to run "dmesg" from the terminal and you should be able to find whatever the error was.

---

### Post by helixed on 2008-09-11
Thanks for the reply.

Here's the output.  Any suggestions?

```
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129779
[    0.000000] Kernel command line: root=UUID=deeb076e-0493-4d34-95f8-66dd14a4408e ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2800.206 MHz processor.
[   20.662214] Console: colour VGA+ 80x25
[   20.662218] console [tty0] enabled
[   20.662662] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.663087] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.675648] Memory: 506628k/523200k available (2177k kernel code, 15996k reserved, 1006k data, 368k init, 0k highmem)
[   20.675659] virtual kernel memory layout:
[   20.675660]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.675661]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.675662]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   20.675663]     lowmem  : 0xc0000000 - 0xdfef0000   ( 510 MB)
[   20.675664]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.675665]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   20.675666]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   20.675669] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.675710] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.755591] Calibrating delay using timer specific routine.. 5607.63 BogoMIPS (lpj=11215274)
[   20.755635] Security Framework initialized
[   20.755643] SELinux:  Disabled at boot.
[   20.755658] AppArmor: AppArmor initialized
[   20.755663] Failure registering capabilities with primary security module.
[   20.755672] Mount-cache hash table entries: 512
[   20.755824] Initializing cgroup subsys ns
[   20.755829] Initializing cgroup subsys cpuacct
[   20.755843] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   20.755856] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   20.755859] CPU: L2 cache: 512K
[   20.755862] CPU: Physical Processor ID: 0
[   20.755864] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   20.755876] Compat vDSO mapped to ffffe000.
[   20.755891] Checking 'hlt' instruction... OK.
[   20.771985] SMP alternatives: switching to UP code
[   20.773791] Early unpacking initramfs... done
[   21.076817] ACPI: Core revision 20070126
[   21.076893] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.081218] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   21.081244] SMP alternatives: switching to SMP code
[   21.082022] Booting processor 1/1 eip 3000
[   21.092156] Initializing CPU#1
[   21.170813] Calibrating delay using timer specific routine.. 5600.63 BogoMIPS (lpj=11201268)
[   21.170826] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   21.170837] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.170840] CPU: L2 cache: 512K
[   21.170842] CPU: Physical Processor ID: 0
[   21.170845] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   21.171113] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   21.171162] Total of 2 processors activated (11208.27 BogoMIPS).
[   21.171924] ENABLING IO-APIC IRQs
[   21.172251] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.318728] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   21.338749] Brought up 2 CPUs
[   21.338818] CPU0 attaching sched-domain:
[   21.338822]  domain 0: span 03
[   21.338824]   groups: 01 02
[   21.338828]   domain 1: span 03
[   21.338831]    groups: 03
[   21.338834] CPU1 attaching sched-domain:
[   21.338835]  domain 0: span 03
[   21.338837]   groups: 02 01
[   21.338841]   domain 1: span 03
[   21.338843]    groups: 03
[   21.339226] net_namespace: 64 bytes
[   21.339239] Booting paravirtualized kernel on bare hardware
[   21.339843] Time:  5:45:11  Date: 09/11/08
[   21.339884] NET: Registered protocol family 16
[   21.340193] EISA bus registered
[   21.340200] ACPI: bus type pci registered
[   21.348304] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
[   21.348307] PCI: Using configuration type 1
[   21.348329] Setting up standard PCI resources
[   21.357442] ACPI: EC: Look up EC in DSDT
[   21.363328] ACPI: Interpreter enabled
[   21.363336] ACPI: (supports S0 S1 S4 S5)
[   21.363358] ACPI: Using IOAPIC for interrupt routing
[   21.370470] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.371865] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.414321] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   21.414494] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   21.414667] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   21.414818] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.414976] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.415117] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.415260] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.415400] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.415581] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   21.415743] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   21.415904] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   21.416098] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   21.416269] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.416324] pnp: PnP ACPI init
[   21.416335] ACPI: bus type pnp registered
[   21.420527] pnp: PnP ACPI: found 12 devices
[   21.420531] ACPI: ACPI bus type pnp unregistered
[   21.420536] PnPBIOS: Disabled by ACPI PNP
[   21.420913] PCI: Using ACPI for IRQ routing
[   21.420917] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.462298] NET: Registered protocol family 8
[   21.462301] NET: Registered protocol family 20
[   21.462402] AppArmor: AppArmor Filesystem Enabled
[   21.466280] Time: tsc clocksource has been installed.
[   21.482307] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   21.482311] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   21.482313] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   21.482316] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   21.482319] system 00:00: iomem range 0x1fef0000-0x1fefffff could not be reserved
[   21.482323] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   21.482326] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   21.482329] system 00:00: iomem range 0x100000-0x1feeffff could not be reserved
[   21.482331] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   21.482334] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.482337] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
[   21.482347] system 00:02: ioport range 0x400-0x47f has been reserved
[   21.482349] system 00:02: ioport range 0x500-0x50f has been reserved
[   21.482357] system 00:03: ioport range 0xb78-0xb7b has been reserved
[   21.482360] system 00:03: ioport range 0xf78-0xf7b has been reserved
[   21.482363] system 00:03: ioport range 0xa78-0xa7b has been reserved
[   21.482365] system 00:03: ioport range 0xe78-0xe7b has been reserved
[   21.482368] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[   21.482370] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[   21.482373] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   21.482376] system 00:03: ioport range 0x800-0x87f has been reserved
[   21.482378] system 00:03: ioport range 0x880-0x8ff has been reserved
[   21.482381] system 00:03: ioport range 0x290-0x297 has been reserved
[   21.512959] PCI: Bridge: 0000:00:01.0
[   21.512964]   IO window: b000-bfff
[   21.512970]   MEM window: fb000000-fcffffff
[   21.512974]   PREFETCH window: e8000000-efffffff
[   21.512996] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.513012] NET: Registered protocol family 2
[   21.554222] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   21.554503] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   21.554613] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   21.554724] TCP: Hash tables configured (established 16384 bind 16384)
[   21.554726] TCP reno registered
[   21.566274] checking if image is initramfs... it is
[   22.009469] Switched to high resolution mode on CPU 1
[   22.013260] Switched to high resolution mode on CPU 0
[   22.174436] Freeing initrd memory: 7321k freed
[   22.175255] audit: initializing netlink socket (disabled)
[   22.175274] audit(1221111911.380:1): initialized
[   22.178341] VFS: Disk quotas dquot_6.5.1
[   22.178454] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.178649] io scheduler noop registered
[   22.178652] io scheduler anticipatory registered
[   22.178654] io scheduler deadline registered
[   22.178670] io scheduler cfq registered (default)
[   22.178689] PCI: VIA PCI bridge detected. Disabling DAC.
[   30.161404] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   30.161441] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   30.161465] Boot video device is 0000:01:00.0
[   30.161948] isapnp: Scanning for PnP cards...
[   30.515879] isapnp: No Plug & Play device found
[   30.558037] Real Time Clock Driver v1.12ac
[   30.558186] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.558332] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.558520] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.559378] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.559826] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.561010] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.561109] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   30.561337] PNP: No PS/2 controller found. Probing ports directly.
[   30.561855] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.561863] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.589702] mice: PS/2 mouse device common for all mice
[   30.589900] EISA: Probing bus 0 at eisa.0
[   30.589945] EISA: Detected 0 cards.
[   30.589950] cpuidle: using governor ladder
[   30.589952] cpuidle: using governor menu
[   30.590069] NET: Registered protocol family 1
[   30.590108] Using IPI No-Shortcut mode
[   30.590147] registered taskstats version 1
[   30.590286]   Magic number: 8:607:769
[   30.590406]   hash matches device ptyp5
[   30.590425]   hash matches device kmsg
[   30.590434]   hash matches device 0000:00:05.0
[   30.590451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   30.590453] EDD information not available.
[   30.590986] Freeing unused kernel memory: 368k freed
[   31.878466] fuse init (API version 7.9)
[   31.905072] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.905091] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.168104] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.168119] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   32.220920] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.357577] SCSI subsystem initialized
[   32.457447] usbcore: registered new interface driver usbfs
[   32.457488] usbcore: registered new interface driver hub
[   32.459304] libata version 3.00 loaded.
[   32.459496] usbcore: registered new device driver usb
[   32.466347] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   32.466360] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   32.466421] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   32.466444] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   32.470059] sata_via 0000:00:0f.0: version 2.3
[   32.470113] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   32.470214] sata_via 0000:00:0f.0: routed to hard irq line 11
[   32.470230] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   32.480959] scsi0 : sata_via
[   32.491954] USB Universal Host Controller Interface driver v3.0
[   32.504945] scsi1 : sata_via
[   32.505047] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 17
[   32.505052] ata2: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 17
[   32.708479] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   32.754447] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   32.754458] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   32.837113] FDC 0 is a post-1991 82077
[   32.920107] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   32.931788] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   32.931810] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   32.931839] PCI: Setting latency timer of device 0000:00:10.4 to 64
[   32.931847] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   32.932377] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   32.932477] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
[   32.945036] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.945305] usb usb1: configuration #1 chosen from 1 choice
[   32.945413] hub 1-0:1.0: USB hub found
[   32.945432] hub 1-0:1.0: 8 ports detected
[   33.049746] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   33.049761] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
[   33.049774] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   33.050329] eth0: VIA Rhine II at 0xfdffd000, 00:16:17:4d:07:20, IRQ 19.
[   33.051045] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   33.051107] pata_via 0000:00:0f.1: version 0.3.3
[   33.051157] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   33.052842] scsi2 : pata_via
[   33.052985] scsi3 : pata_via
[   33.055790] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[   33.055798] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[   33.240052] ata3.01: ATA-7: ST3300831A, 3.06, max UDMA/100
[   33.240060] ata3.01: 586072368 sectors, multi 1: LBA48 
[   33.248879] ata3.01: configured for UDMA/100
[   33.287418] hub 1-0:1.0: over-current change on port 5
[   33.574812] hub 1-0:1.0: over-current change on port 6
[   33.626760] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[   33.731116] ata4.00: ATAPI: BENQ    DVD DD DW1650, BCFC, max UDMA/33
[   33.731142] ata4.01: ATAPI: PIONEER DVD-RW  DVR-106D, 1.10, max UDMA/33
[   33.862262] hub 1-0:1.0: over-current change on port 7
[   33.900718] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0010b90211434a9b]
[   33.901818] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0011060000005307]
[   33.906658] ata4.00: configured for UDMA/33
[   33.920203] scsi4 : SBP-2 IEEE-1394
[   33.966032] hub 1-0:1.0: over-current change on port 8
[   34.066092] ata4.01: configured for UDMA/33
[   34.066276] scsi 2:0:1:0: Direct-Access     ATA      ST3300831A       3.06 PQ: 0 ANSI: 5
[   34.068620] scsi 3:0:0:0: CD-ROM            BENQ     DVD DD DW1650    BCFC PQ: 0 ANSI: 5
[   34.074447] scsi 3:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-106D 1.10 PQ: 0 ANSI: 5
[   34.075009] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.075031] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   34.075038] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   34.075094] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   34.075123] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
[   34.075325] usb usb2: configuration #1 chosen from 1 choice
[   34.075368] hub 2-0:1.0: USB hub found
[   34.075379] hub 2-0:1.0: 2 ports detected
[   34.177829] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.177858] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   34.177864] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   34.177920] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   34.177959] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
[   34.178172] usb usb3: configuration #1 chosen from 1 choice
[   34.178221] hub 3-0:1.0: USB hub found
[   34.178238] hub 3-0:1.0: 2 ports detected
[   34.281612] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.281636] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   34.281642] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   34.281698] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   34.281733] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
[   34.281951] usb usb4: configuration #1 chosen from 1 choice
[   34.282008] hub 4-0:1.0: USB hub found
[   34.282020] hub 4-0:1.0: 2 ports detected
[   34.385412] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.385436] PCI: Setting latency timer of device 0000:00:10.3 to 64
[   34.385442] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   34.385488] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   34.385523] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
[   34.385741] usb usb5: configuration #1 chosen from 1 choice
[   34.385789] hub 5-0:1.0: USB hub found
[   34.385802] hub 5-0:1.0: 2 ports detected
[   34.547095] Driver 'sd' needs updating - please use bus_type methods
[   34.549154] sd 2:0:1:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[   34.549181] sd 2:0:1:0: [sda] Write Protect is off
[   34.549185] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   34.549222] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.549319] sd 2:0:1:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[   34.549338] sd 2:0:1:0: [sda] Write Protect is off
[   34.549342] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   34.549375] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.549381]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.565711]  sda1 sda2 < sda5 >
[   34.587967] sd 2:0:1:0: [sda] Attached SCSI disk
[   34.594885] sd 2:0:1:0: Attached scsi generic sg0 type 0
[   34.594925] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   34.594959] scsi 3:0:1:0: Attached scsi generic sg2 type 5
[   34.601592] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   34.601601] Uniform CD-ROM driver Revision: 3.20
[   34.601716] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   34.632416] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   34.632506] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   34.801414] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   34.921603] ieee1394: sbp2: Logged into SBP-2 device
[   34.921662] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   34.924606] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[   34.925410] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   34.926196] sd 4:0:0:0: [sdb] Write Protect is off
[   34.926205] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   34.927296] sd 4:0:0:0: [sdb] Got wrong page
[   34.927304] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   34.928047] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   34.928783] sd 4:0:0:0: [sdb] Write Protect is off
[   34.928788] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   34.929876] sd 4:0:0:0: [sdb] Got wrong page
[   34.929886] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   34.929893]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[   34.954570] sd 4:0:0:0: [sdb] Attached SCSI disk
[   34.954650] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   34.970585] usb 3-2: configuration #1 chosen from 1 choice
[   35.165707] Attempting manual resume
[   35.165712] swsusp: Resume From Partition 8:5
[   35.165714] PM: Checking swsusp image.
[   35.165945] PM: Resume from disk failed.
[   35.208812] kjournald starting.  Commit interval 5 seconds
[   35.208823] EXT3-fs: mounted filesystem with ordered data mode.
[   35.212629] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   35.394591] usb 4-1: configuration #1 chosen from 1 choice
[   35.635792] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   35.816712] usb 4-2: configuration #1 chosen from 1 choice
[   44.655093] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.802268] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.877945] Linux agpgart interface v0.102
[   45.020048] agpgart: Detected VIA VT3314 chipset
[   45.028400] agpgart: AGP aperture is 128M @ 0xf0000000
[   45.269386] input: Power Button (FF) as /devices/virtual/input/input1
[   45.293074] ACPI: Power Button (FF) [PWRF]
[   45.293219] input: Power Button (CM) as /devices/virtual/input/input2
[   45.324993] ACPI: Power Button (CM) [PWRB]
[   45.325133] input: Sleep Button (CM) as /devices/virtual/input/input3
[   45.356978] ACPI: Sleep Button (CM) [SLPB]
[   45.576698] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 20
[   45.576712] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   45.656984] phy0: Selected rate control algorithm 'simple'
[   46.434666] nvidia: module license 'NVIDIA' taints kernel.
[   47.353137] lirc_dev: IR Remote Control driver registered, at major 61 
[   47.397047] 
[   47.397053] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   47.397059] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   47.646947] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   47.760301] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[   47.906351] lirc_dev: lirc_register_plugin: sample_rate: 0
[   47.910336] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb3:2
[   47.910407] usbcore: registered new interface driver lirc_mceusb2
[   48.107847] usbcore: registered new interface driver hiddev
[   48.112779] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.112796] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.113263] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   48.127476] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.0/input/input5
[   48.147603] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:10.2-1
[   48.168087] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.1/input/input6
[   48.195543] input,hidraw1: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:10.2-1
[   48.210241] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.2/usb4/4-2/4-2:1.0/input/input7
[   48.227482] input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.2-2
[   48.227516] usbcore: registered new interface driver usbhid
[   48.227523] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.687709] parport_pc 00:0b: reported by Plug and Play ACPI
[   48.687773] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   48.795284] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   48.795302] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
[   48.795474] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   51.248939] lp0: using parport0 (interrupt-driven).
[   51.316550] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   51.885254] EXT3 FS on sda1, internal journal
[   53.254372] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.924787] No dock devices found.
[   55.647065] NET: Registered protocol family 10
[   55.647641] lo: Disabled Privacy Extensions
[   56.557052] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   56.557063] apm: disabled - APM is not SMP safe.
[   56.736050] ppdev: user-space parallel port driver
[   56.864942] audit(1221111946.753:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5253 profile="/usr/sbin/cupsd" namespace="deflircault"
[   58.108865] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.203405] input: Unspecified device as /devices/virtual/input/input8
[   58.211724] Bluetooth: Core ver 2.11
[   58.212301] NET: Registered protocol family 31
[   58.212308] Bluetooth: HCI device and connection manager initialized
[   58.212314] Bluetooth: HCI socket layer initialized
[   58.230844] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.240163] Bluetooth: L2CAP ver 2.9
[   58.240172] Bluetooth: L2CAP socket layer initialized
[   58.357177] Bluetooth: RFCOMM socket layer initialized
[   58.357211] Bluetooth: RFCOMM TTY layer initialized
[   58.357215] Bluetooth: RFCOMM ver 1.8
[   60.727597] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   60.727621] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   60.727710] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   62.039985] NET: Registered protocol family 17
[   74.543861] eth0: no IPv6 routers present
```

Thanks,

helixed

---

### Post by helixed on 2008-09-13
bump?

---

