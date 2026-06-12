---
title: "Linkstation live and Ubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gav-the-lad on 2008-04-25
Another noob question :confused:

Why cant i find my external hard drive? Its a Linkstation Live NAS. I can play mp3's ok but i cant see the drive. What do i need to do to find it?

Thanks in advance:)

---

### Post by gav-the-lad on 2008-04-25
bump

---

### Post by guitarthrasher on 2008-04-25
Do sudo fdisk -l and tell me what you get.

---

### Post by gav-the-lad on 2008-04-25
This is what i got:

[COLOR="Blue"]Disk /dev/sda: 50.0 GB, 50018393088 bytes
255 heads, 63 sectors/track, 6081 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5896    47359588+  83  Linux
/dev/sda2            5897        6081     1486012+   5  Extended
/dev/sda5            5897        6081     1485981   82  Linux swap / Solaris[/COLOR]

---

### Post by guitarthrasher on 2008-04-25
So, you can play mp3's with the device, but you can't view the file?

---

### Post by guitarthrasher on 2008-04-25
Also, try disconnecting it then reconnecting it, open a terminal and type dmesg to see if ubuntu sees the drive. It should come up in the last ten lines or so.

---

### Post by gav-the-lad on 2008-04-26
Ok here is what i got:

[COLOR="Blue"][    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6970 checksum 0
[    0.000000] ACPI: RSDP 000F6970, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F6E50DA, 0040 (r1 NEC    ND000104        1 MSFT  100000E)
[    0.000000] ACPI: FACP 1F6EAE92, 0074 (r1 NEC    ND000104        1 MSTF  100000E)
[    0.000000] ACPI: DSDT 1F6E5B32, 5360 (r1    NEC ND000104        1 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6FBFC0, 0040
[    0.000000] ACPI: BOOT 1F6EAFD8, 0028 (r1 NEC    ND000104        1 MSFT  100000E)
[    0.000000] ACPI: TCPA 1F6EAFA6, 0032 (r1 Phoeni  x              1  TL         0)
[    0.000000] ACPI: SSDT 1F6E5956, 01D4 (r1 SataRe SataAhci     1000 INTL 20030224)
[    0.000000] ACPI: SSDT 1F6E5511, 02B9 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 1F6E5333, 01DE (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 1F6E511A, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=891c1843-c407-47d5-abe9-9ddc435ece5e ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (013fe000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1596.209 MHz processor.
[    8.424187] Console: colour VGA+ 80x25
[    8.424193] console [tty0] enabled
[    8.424427] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.424686] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.437789] Memory: 498084k/514944k available (2157k kernel code, 16252k reserved, 998k data, 364k init, 0k highmem)
[    8.437800] virtual kernel memory layout:
[    8.437801]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.437803]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.437804]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    8.437806]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    8.437807]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[    8.437808]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[    8.437810]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[    8.437813] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.437857] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.517821] Calibrating delay using timer specific routine.. 3195.99 BogoMIPS (lpj=6391983)
[    8.517853] Security Framework initialized
[    8.517862] SELinux:  Disabled at boot.
[    8.517878] AppArmor: AppArmor initialized
[    8.517885] Failure registering capabilities with primary security module.
[    8.517894] Mount-cache hash table entries: 512
[    8.518043] CPU: After generic identify, caps: afe9f9ff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.518057] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.518060] CPU: L2 cache: 2048K
[    8.518063] CPU: After all inits, caps: afe9f9ff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[    8.518073] Compat vDSO mapped to ffffe000.
[    8.518088] Checking 'hlt' instruction... OK.
[    8.534252] SMP alternatives: switching to UP code
[    8.536350] Freeing SMP alternatives: 11k freed
[    8.536468] Early unpacking initramfs... done
[    8.936909] ACPI: Core revision 20070126
[    8.936982] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.939190] ACPI: setting ELCR to 0200 (from 0800)
[    8.969777] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    8.969783] SMP motherboard not detected.
[    8.969786] Local APIC not detected. Using dummy APIC emulation.
[    8.969832] Brought up 1 CPUs
[    8.969853] CPU0 attaching sched-domain:
[    8.969856]  domain 0: span 01
[    8.969858]   groups: 01
[    8.970049] net_namespace: 64 bytes
[    8.970066] Booting paravirtualized kernel on bare hardware
[    8.970582] Time: 10:53:09  Date: 04/26/08
[    8.970610] NET: Registered protocol family 16
[    8.970820] EISA bus registered
[    8.970835] ACPI: bus type pci registered
[    8.971408] PCI: PCI BIOS revision 2.10 entry at 0xfd920, last bus=6
[    8.971411] PCI: Using configuration type 1
[    8.971413] Setting up standard PCI resources
[    8.979291] ACPI: EC: Look up EC in DSDT
[    8.981421] ACPI: Interpreter enabled
[    8.981425] ACPI: (supports S0 S3 S4 S5)
[    8.981441] ACPI: Using PIC for interrupt routing
[    8.985197] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    8.985200] ACPI: EC: driver started in poll mode
[    8.985239] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.986013] Force enabled HPET at base address 0xfed00000
[    8.986020] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.986025] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.986420] PCI: Transparent bridge - 0000:00:1e.0
[    8.986448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.986894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.988562] ACPI: PCI Interrupt Link [LNKA] (IRQs 5) *11
[    8.988651] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *11
[    8.988738] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *11
[    8.988824] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    8.988909] ACPI: PCI Interrupt Link [LNKE] (IRQs 5) *11
[    8.988995] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    8.989081] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[    8.989167] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[    8.989274] ACPI: Power Resource [QFAN] (off)
[    8.989320] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.989354] pnp: PnP ACPI init
[    8.989362] ACPI: bus type pnp registered
[    8.991375] pnp: PnP ACPI: found 8 devices
[    8.991377] ACPI: ACPI bus type pnp unregistered
[    8.991382] PnPBIOS: Disabled by ACPI PNP
[    8.991615] PCI: Using ACPI for IRQ routing
[    8.991618] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.009473] NET: Registered protocol family 8
[    9.009476] NET: Registered protocol family 20
[    9.009659] hpet clockevent registered
[    9.009666] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.009670] hpet0: 3 64-bit timers, 14318180 Hz
[    9.010711] AppArmor: AppArmor Filesystem Enabled
[    9.013660] Time: tsc clocksource has been installed.
[    9.021692] system 00:04: ioport range 0x200-0x20f has been reserved
[    9.021696] system 00:04: ioport range 0x680-0x6ff has been reserved
[    9.021699] system 00:04: ioport range 0x800-0x80f has been reserved
[    9.021702] system 00:04: ioport range 0x1000-0x107f has been reserved
[    9.021705] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    9.021708] system 00:04: ioport range 0x1640-0x164f has been reserved
[    9.021711] system 00:04: ioport range 0xfe00-0xfefe has been reserved
[    9.021714] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[    9.021718] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[    9.021721] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[    9.021724] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[    9.021728] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.021731] system 00:04: iomem range 0xd0000-0xfffff could not be reserved
[    9.052120] PCI: Bridge: 0000:00:1e.0
[    9.052124]   IO window: 6000-6fff
[    9.052130]   MEM window: b0100000-b01fffff
[    9.052134]   PREFETCH window: disabled.
[    9.052154] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.052168] NET: Registered protocol family 2
[    9.089665] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.089867] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.089981] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    9.090096] TCP: Hash tables configured (established 16384 bind 16384)
[    9.090099] TCP reno registered
[    9.101703] checking if image is initramfs... it is
[    9.513250] Switched to high resolution mode on CPU 0
[    9.891198] Freeing initrd memory: 7703k freed
[    9.891452] Simple Boot Flag at 0x35 set to 0x1
[    9.891842] audit: initializing netlink socket (disabled)
[    9.891863] audit(1209207189.428:1): initialized
[    9.894129] VFS: Disk quotas dquot_6.5.1
[    9.894211] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.894374] io scheduler noop registered
[    9.894377] io scheduler anticipatory registered
[    9.894379] io scheduler deadline registered
[    9.894390] io scheduler cfq registered (default)
[    9.894406] Boot video device is 0000:00:02.0
[    9.894764] isapnp: Scanning for PnP cards...
[   10.248938] isapnp: No Plug & Play device found
[   10.277967] Real Time Clock Driver v1.12ac
[   10.278085] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.278937] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   10.278941] PCI: setting IRQ 5 as level-triggered
[   10.278946] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   10.278958] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   10.279644] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.279722] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.279819] PNP: PS/2 Controller [PNP0303:KBCE,PNP0f13:MSEE] at 0x60,0x64 irq 1,12
[   10.283659] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.283666] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.292621] mice: PS/2 mouse device common for all mice
[   10.292742] EISA: Probing bus 0 at eisa.0
[   10.292749] Cannot allocate resource for EISA slot 1
[   10.292760] Cannot allocate resource for EISA slot 4
[   10.292762] Cannot allocate resource for EISA slot 5
[   10.292765] Cannot allocate resource for EISA slot 6
[   10.292774] EISA: Detected 0 cards.
[   10.292778] cpuidle: using governor ladder
[   10.292780] cpuidle: using governor menu
[   10.292883] NET: Registered protocol family 1
[   10.292912] Using IPI No-Shortcut mode
[   10.292952] registered taskstats version 1
[   10.293062]   Magic number: 4:340:882
[   10.293118]   hash matches device ptyx6
[   10.293175] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.293178] EDD information not available.
[   10.293405] Freeing unused kernel memory: 364k freed
[   10.336545] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.516289] fuse init (API version 7.9)
[   11.527979] ACPI: Transitioning device [FAN] to D3
[   11.527983] ACPI: Transitioning device [FAN] to D3
[   11.527987] ACPI: Fan [FAN] (off)
[   11.533175] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   11.533182] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.533195] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   11.534581] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   11.535114] ACPI: Thermal Zone [THRM] (52 C)
[   12.154612] usbcore: registered new interface driver usbfs
[   12.154641] usbcore: registered new interface driver hub
[   12.167130] usbcore: registered new device driver usb
[   12.182946] USB Universal Host Controller Interface driver v3.0
[   12.183227] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.183230] PCI: setting IRQ 11 as level-triggered
[   12.183235] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.183249] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.183253] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.183661] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.183694] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00004820
[   12.183839] usb usb1: configuration #1 chosen from 1 choice
[   12.183864] hub 1-0:1.0: USB hub found
[   12.183870] hub 1-0:1.0: 2 ports detected
[   12.232041] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   12.287165] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.287170] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.287184] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.287189] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.287214] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.287244] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00004840
[   12.287364] usb usb2: configuration #1 chosen from 1 choice
[   12.287388] hub 2-0:1.0: USB hub found
[   12.287394] hub 2-0:1.0: 2 ports detected
[   12.287654] SCSI subsystem initialized
[   12.334452] libata version 3.00 loaded.
[   12.391071] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   12.391076] PCI: setting IRQ 10 as level-triggered
[   12.391081] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.391095] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.391100] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.391126] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.391159] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00004860
[   12.391278] usb usb3: configuration #1 chosen from 1 choice
[   12.391305] hub 3-0:1.0: USB hub found
[   12.391311] hub 3-0:1.0: 2 ports detected
[   12.494997] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   12.495003] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   12.495016] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.495021] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.495047] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.495080] uhci_hcd 0000:00:1d.3: irq 5, io base 0x00004880
[   12.495205] usb usb4: configuration #1 chosen from 1 choice
[   12.495230] hub 4-0:1.0: USB hub found
[   12.495236] hub 4-0:1.0: 2 ports detected
[   12.598822] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.598840] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.598844] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.598871] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.602783] ehci_hcd 0000:00:1d.7: debug port 1
[   12.602790] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.602799] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xb0040000
[   12.618545] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.618665] usb usb5: configuration #1 chosen from 1 choice
[   12.618691] hub 5-0:1.0: USB hub found
[   12.618698] hub 5-0:1.0: 8 ports detected
[   12.722696] 8139cp 0000:06:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   12.722704] 8139cp 0000:06:00.0: Try the "8139too" driver instead.
[   12.726316] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.726356] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.726373] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   12.727211] 8139too Fast Ethernet driver 0.9.28
[   12.727262] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.728143] eth0: RealTek RTL8139 at 0x6000, 00:c0:9f:be:ec:58, IRQ 11
[   12.728146] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   12.731891] ata_piix 0000:00:1f.1: version 2.12
[   12.731912] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.731952] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.732637] scsi0 : ata_piix
[   12.733125] scsi1 : ata_piix
[   12.733733] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4810 irq 14
[   12.733736] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4818 irq 15
[   13.006209] Clocksource tsc unstable (delta = -4740776128 ns)
[   13.010282] Time: hpet clocksource has been installed.
[   13.015698] ata1.00: ATA-6: ST950212A, 3.05, max UDMA/100
[   13.015702] ata1.00: 97692174 sectors, multi 16: LBA48 
[   13.015729] ata1.01: ATAPI: PHILIPS DVD+/-RW SDVD8441, PX45, max UDMA/33
[   13.017323] ata1.00: configured for UDMA/100
[   13.027720] ata1.01: configured for UDMA/33
[   13.027768] ata2: port disabled. ignoring.
[   13.027917] scsi 0:0:0:0: Direct-Access     ATA      ST950212A        3.05 PQ: 0 ANSI: 5
[   13.029969] scsi 0:0:1:0: CD-ROM            PHILIPS  DVD+-RW SDVD8441 PX45 PQ: 0 ANSI: 5
[   13.042294] Driver 'sd' needs updating - please use bus_type methods
[   13.042374] sd 0:0:0:0: [sda] 97692174 512-byte hardware sectors (50018 MB)
[   13.042388] sd 0:0:0:0: [sda] Write Protect is off
[   13.042391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.042407] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.042457] sd 0:0:0:0: [sda] 97692174 512-byte hardware sectors (50018 MB)
[   13.042467] sd 0:0:0:0: [sda] Write Protect is off
[   13.042469] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.042485] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.042489]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.070901]  sda1 sda2 < sda5 >
[   13.096453] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.102251] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.102271] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   13.155480] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[   13.155485] Uniform CD-ROM driver Revision: 3.20
[   13.155540] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   13.360797] Attempting manual resume
[   13.360802] swsusp: Resume From Partition 8:5
[   13.360803] PM: Checking swsusp image.
[   13.360975] PM: Resume from disk failed.
[   13.416668] kjournald starting.  Commit interval 5 seconds
[   13.416679] EXT3-fs: mounted filesystem with ordered data mode.
[   21.679861] Linux agpgart interface v0.102
[   21.742996] agpgart: Detected an Intel 915GM Chipset.
[   21.743532] agpgart: Detected 7932K stolen memory.
[   21.937124] agpgart: AGP aperture is 256M @ 0xc0000000
[   22.419183] intel_rng: FWH not detected
[   22.662639] input: Power Button (FF) as /devices/virtual/input/input2
[   22.670943] ACPI: Power Button (FF) [PWRF]
[   22.671020] input: Lid Switch as /devices/virtual/input/input3
[   22.717291] ACPI: Lid Switch [LID0]
[   22.717405] input: Power Button (CM) as /devices/virtual/input/input4
[   22.726889] ACPI: Power Button (CM) [PWRB]
[   22.765557] iTCO_vendor_support: vendor-support=0
[   22.802834] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   22.802931] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   22.802970] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.902106] ACPI: AC Adapter [ACAD] (off-line)
[   22.950885] ACPI: Battery Slot [BAT1] (battery absent)
[   23.454031] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   23.526192] ieee80211_crypt: registered algorithm 'NULL'
[   23.570167] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.570172] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.688526] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.688531] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.688637] ACPI: PCI Interrupt 0000:06:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   23.734462] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.476245] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   24.485308] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   25.961409] input: PS/2 Mouse as /devices/virtual/input/input7
[   26.000165] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   26.883982] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   26.884244] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   26.884248] PCI: setting IRQ 9 as level-triggered
[   26.884252] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   26.884283] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   27.202852] intel8x0_measure_ac97_clock: measured 54078 usecs
[   27.202857] intel8x0: clocking to 48000
[   27.290796] NET: Registered protocol family 17
[   27.361142] lp: driver loaded but no devices found
[   27.609459] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   27.641798] EXT3 FS on sda1, internal journal
[   28.311259] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.743263] No dock devices found.
[   29.690685] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.690690] apm: overridden by ACPI.
[   29.838064] ppdev: user-space parallel port driver
[   29.924196] audit(1209207214.992:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4710 profile="/usr/sbin/cupsd" namespace="default"
[   36.045209] Marking TSC unstable due to: cpufreq changes.
[   30.619182] eth0: link down
[   30.635817] Bluetooth: Core ver 2.11
[   30.636453] NET: Registered protocol family 31
[   30.636457] Bluetooth: HCI device and connection manager initialized
[   30.636460] Bluetooth: HCI socket layer initialized
[   30.675316] Bluetooth: L2CAP ver 2.9
[   30.675321] Bluetooth: L2CAP socket layer initialized
[   36.948512] Bluetooth: RFCOMM socket layer initialized
[   36.948526] Bluetooth: RFCOMM TTY layer initialized
[   36.948528] Bluetooth: RFCOMM ver 1.8
[   32.590018] [drm] Initialized drm 1.1.0 20060810
[   32.593568] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   32.593578] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.594550] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   86.578675] NET: Registered protocol family 10
[   86.579766] lo: Disabled Privacy Extensions
[   86.581067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   86.582133] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  765.385884] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  765.407258] eth0: link down
[  765.407506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  765.450465] eth0: link down
[  765.450703] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  765.461000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  765.499667] ieee80211_crypt: registered algorithm 'TKIP'
[  773.402148] eth1: no IPv6 routers present
[  774.611853] eth0: link down
[  774.612096] ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]

There is nothing there that indicates to the Linkstation. When i open my media player i can see the drive as it is under the shared tab, but if i go to places there is no drive showing. I have attached some screen shots to make things clearer, i hope:)

---

### Post by gav-the-lad on 2008-04-26
Bump

---

### Post by gav-the-lad on 2008-04-26
Can anyone help? The Linkstation is connected to my router and is streaming music ok, i just cant see the Linkstation. Which means i cant rip/download music to the Linkstation.

---

### Post by gav-the-lad on 2008-04-27
update:

I can now see the drive in places > network > work groups, but still cant see any files or folders. So i typed dmesg in the terminal and the last six lines are:
[COLOR="Blue"][10120.595490]  CIFS VFS: cifs_mount failed w/return code = -6
[10120.788807]  CIFS VFS: cifs_mount failed w/return code = -6
[11586.766101]  CIFS VFS: cifs_mount failed w/return code = -6
[11586.961049]  CIFS VFS: cifs_mount failed w/return code = -6
[11716.727568]  CIFS VFS: cifs_mount failed w/return code = -6
[11716.952565]  CIFS VFS: cifs_mount failed w/return code = -6
[12046.244091]  CIFS VFS: cifs_mount failed w/return code = -6
[12046.426883]  CIFS VFS: cifs_mount failed w/return code = -6[/COLOR]

What does the above mean?

---

