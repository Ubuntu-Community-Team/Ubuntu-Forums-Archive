---
title: "Hardy Heron Boot..."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-26
Hi! I upgraded from Gutsy to Hardy in launch day... When I was asked to restart my computer I noticed I had options "Ubuntu 8.04 Kernel 2......" and the option with "recovery mode" doubled!! :???: I thought it was something easy, and would be again as normal in the next start up... but I was wrong!

Could you please help me giving me a way to delete that double boot options?
It's getting annoying because sometimes one of the options doesn't boot...

I have a dual boot with Vista, but although both options for booting vista read the same (something about a longhorn), one of the options is for starting in a kind of recovery mode, and the other is for starting vista normally.....

---

### Post by ghost_ryder35 on 2008-04-26
> **ALex! said:**
> Hi! I upgraded from Gutsy to Hardy in launch day... When I was asked to restart my computer I noticed I had options "Ubuntu 8.04 Kernel 2......" and the option with "recovery mode" doubled!! :???: I thought it was something easy, and would be again as normal in the next start up... but I was wrong!
 
Could you please help me giving me a way to delete that double boot options?
It's getting annoying because sometimes one of the options doesn't boot...
 
I have a dual boot with Vista, but although both options for booting vista read the same (something about a longhorn), one of the options is for starting in a kind of recovery mode, and the other is for starting vista normally.....
 
```

sudo gedit /boot/grub/menu.lst

```
and remove the old options

---

### Post by ALex! on 2008-04-26
> **ghost_ryder35 said:**
> ```

sudo gedit /boot/grub/menu.lst

```
and remove the old options

excuse me sir... but which of the options should I delete ??? 

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```

I know that there are two for deletion (ubuntu 8.04..... and recovey mode)
but i don't know which pair! :???: 
Notice both ubuntu 8.04 are the same except for the Kernel.... (one is -14 and the other one is -16)
I should also say that when I try to boot on the 1st one (-16) It doesn't boot at all! :???: so I have to manually shut down my computer to booting again, but in the -14 option... Then when I've booted, if I restart my computer and press the -16 option, I DO BOOT! :???:
thanks!

---

### Post by ALex! on 2008-04-26
My Ubuntu 8.04, kernel 2.6.24-16-generic option doesn't work!!! :(
but my Ubuntu 8.04, kernel 2.6.22-14-generic does! 

what should I do?

---

### Post by ghost_ryder35 on 2008-04-26
thats weird that you have to boot into 14 before you can boot into 16.  I would make a copy of /boot/grub/menu.lst and the remove 14 and try booting.  But that is just me :)

---

### Post by Mothinator on 2008-04-27
I believe I am having a similar problem to the OP.

I upgraded from Feisty->Gutsy->Hardy over the past year. I believe the "multiple kernel entries" are just the old kernels from those versions. For instance, I have 3 different kernels to choose from.

My problem is that when I choose "Ubuntu 8.04, kernel 2.6.24-16-generic"
I see the ubuntu splash screen and then i get a blinking cursor at the top left hand corner of the screen. Nothing more happens.

However, when i boot to "Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)" I see the dmesg output and am eventually prompted to "proceed with regular boot." When I select that option, then hardy boots with no problems.

Also booting to "Ubuntu 8.04, kernel 2.6.22-14-generic" works fine.


From my menu.lst, it seems that the only differences are recovery mode has the option "single" while the normal kernel has "quiet splash".

What is the best way to modify GRUB so I can boot the computer unattended.

From grub menu.lst:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

output of dmesg:
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb880
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31

[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA610 checksum 0
[    0.000000] ACPI: RSDP 000FA610, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 1FFF0120, 319A (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro single
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1399.799 MHz processor.
[   14.156101] Console: colour VGA+ 80x25
[   14.156106] console [tty0] enabled
[   14.158875] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.159342] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.179390] Memory: 507428k/524224k available (2157k kernel code, 16204k reserved, 998k data, 364k init, 0k highmem)
[   14.179463] virtual kernel memory layout:
[   14.179464]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.179466]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.179468]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   14.179470]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   14.179472]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   14.179473]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   14.179475]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   14.179843] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.179987] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.260013] Calibrating delay using timer specific routine.. 2802.41 BogoMIPS (lpj=5604836)
[   14.260146] Security Framework initialized
[   14.260198] SELinux:  Disabled at boot.
[   14.260269] AppArmor: AppArmor initialized
[   14.260318] Failure registering capabilities with primary security module.
[   14.260381] Mount-cache hash table entries: 512
[   14.260612] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   14.260626] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.260679] CPU: L2 Cache: 256K (64 bytes/line)
[   14.260727] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000 00000000
[   14.260742] Compat vDSO mapped to ffffe000.
[   14.260802] Checking 'hlt' instruction... OK.
[   14.276344] SMP alternatives: switching to UP code
[   14.277920] Freeing SMP alternatives: 11k freed
[   14.278164] Early unpacking initramfs... done
[   14.761838] ACPI: Core revision 20070126
[   14.762001] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.764501] CPU0: AMD Athlon(tm) XP 1600+ stepping 02
[   14.764644] Total of 1 processors activated (2802.41 BogoMIPS).
[   14.765443] ENABLING IO-APIC IRQs
[   14.765815] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.911652] Brought up 1 CPUs
[   14.911772] CPU0 attaching sched-domain:
[   14.911776]  domain 0: span 01
[   14.911779]   groups: 01
[   14.912093] net_namespace: 64 bytes
[   14.912150] Booting paravirtualized kernel on bare hardware
[   14.912897] Time: 16:36:42  Date: 04/27/08
[   14.912993] NET: Registered protocol family 16
[   14.913366] EISA bus registered
[   14.913442] ACPI: bus type pci registered
[   14.915043] PCI: PCI BIOS revision 2.10 entry at 0xfdb21, last bus=1
[   14.915096] PCI: Using configuration type 1
[   14.915141] Setting up standard PCI resources
[   14.920266] ACPI: EC: Look up EC in DSDT
[   14.924962] ACPI: Interpreter enabled
[   14.925017] ACPI: (supports S0 S3 S4 S5)
[   14.925203] ACPI: Using IOAPIC for interrupt routing
[   14.929565] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.930367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.942057] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   14.942607] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.943217] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.943767] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   14.944322] ACPI: Power Resource [URP1] (off)
[   14.944406] ACPI: Power Resource [URP2] (off)
[   14.944487] ACPI: Power Resource [FDDP] (off)
[   14.944567] ACPI: Power Resource [LPTP] (off)
[   14.944681] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.944782] pnp: PnP ACPI init
[   14.944837] ACPI: bus type pnp registered
[   14.946870] pnp: PnP ACPI: found 8 devices
[   14.946919] ACPI: ACPI bus type pnp unregistered
[   14.946969] PnPBIOS: Disabled by ACPI PNP
[   14.947400] PCI: Using ACPI for IRQ routing
[   14.947449] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.955603] NET: Registered protocol family 8
[   14.955651] NET: Registered protocol family 20
[   14.955815] AppArmor: AppArmor Filesystem Enabled
[   14.959542] Time: tsc clocksource has been installed.
[   14.998191] PCI: Bridge: 0000:00:01.0
[   14.998240]   IO window: a000-afff
[   14.998288]   MEM window: dfe00000-dfefffff
[   14.998336]   PREFETCH window: bfc00000-dfcfffff
[   14.998401] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.998422] NET: Registered protocol family 2
[   15.035636] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.036037] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   15.036366] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   15.036708] TCP: Hash tables configured (established 16384 bind 16384)
[   15.036760] TCP reno registered
[   15.047728] checking if image is initramfs... it is
[   15.499187] Switched to high resolution mode on CPU 0
[   15.960830] Freeing initrd memory: 7598k freed
[   15.962035] audit: initializing netlink socket (disabled)
[   15.962108] audit(1209314202.676:1): initialized
[   15.965349] VFS: Disk quotas dquot_6.5.1
[   15.965524] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.965804] io scheduler noop registered
[   15.965852] io scheduler anticipatory registered
[   15.965899] io scheduler deadline registered
[   15.965958] io scheduler cfq registered (default)
[   15.966023] PCI: VIA PCI bridge detected. Disabling DAC.
[   15.966120] Boot video device is 0000:01:00.0
[   15.966554] isapnp: Scanning for PnP cards...
[   16.320094] isapnp: No Plug & Play device found
[   16.363762] Real Time Clock Driver v1.12ac
[   16.363971] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.365828] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.366001] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.366221] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.368530] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.368585] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.378521] mice: PS/2 mouse device common for all mice
[   16.378773] EISA: Probing bus 0 at eisa.0
[   16.378860] EISA: Detected 0 cards.
[   16.378909] cpuidle: using governor ladder
[   16.378954] cpuidle: using governor menu
[   16.379228] NET: Registered protocol family 1
[   16.379323] Using IPI No-Shortcut mode
[   16.379421] registered taskstats version 1
[   16.379605]   Magic number: 4:295:642
[   16.379920] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.379969] EDD information not available.
[   16.380668] Freeing unused kernel memory: 364k freed
[   16.414429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.696125] fuse init (API version 7.9)
[   16.727938] ACPI: Processor [CPU1] (supports 16 throttling states)
[   17.472278] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   17.472424] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.491682] tulip0:  EEPROM default media type Autosense.
[   17.491733] tulip0:  Index #0 - Media 10baseT (#0) described by a 21140 non-MII (0) block.
[   17.491793] tulip0:  Index #1 - Media 100baseTx (#3) described by a 21140 non-MII (0) block.
[   17.492446] tulip0:  Index #2 - Media 10baseT-FDX (#4) described by a 21140 non-MII (0) block.
[   17.492506] tulip0:  Index #3 - Media 100baseTx-FDX (#5) described by a 21140 non-MII (0) block.
[   17.493030] tulip0:  MII transceiver #1 config 3100 status 7829 advertising 05e1.
[   17.609829] SCSI subsystem initialized
[   17.626957] eth0: Digital DS21140 Tulip rev 34 at Port 0xe800, 00:e0:c5:f4:01:7e, IRQ 16.
[   17.708166] usbcore: registered new interface driver usbfs
[   17.708260] usbcore: registered new interface driver hub
[   17.712222] libata version 3.00 loaded.
[   17.712537] usbcore: registered new device driver usb
[   17.715967] Floppy drive(s): fd0 is 1.44M
[   17.719107] pata_via 0000:00:11.1: version 0.3.3
[   17.729458] scsi0 : pata_via
[   17.733234] FDC 0 is a post-1991 82077
[   17.734665] USB Universal Host Controller Interface driver v3.0
[   17.742455] scsi1 : pata_via
[   17.745482] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   17.745536] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   17.910433] ata1.00: ATA-4: WDC WD153BA, 16.13Q16, max UDMA/66
[   17.910494] ata1.00: 30043440 sectors, multi 16: LBA 
[   17.926283] ata1.00: configured for UDMA/66
[   18.245439] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-M1612, 1004, max UDMA/33
[   18.417242] ata2.00: configured for UDMA/33
[   18.417516] scsi 0:0:0:0: Direct-Access     ATA      WDC WD153BA      16.1 PQ: 0 ANSI: 5
[   18.423207] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1612 1004 PQ: 0 ANSI: 5
[   18.427866] ACPI: PCI Interrupt 0000:00:11.2[D] -> GSI 5 (level, low) -> IRQ 5
[   18.427982] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   18.428457] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[   18.428557] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000d800
[   18.428856] usb usb1: configuration #1 chosen from 1 choice
[   18.428941] hub 1-0:1.0: USB hub found
[   18.428994] hub 1-0:1.0: 2 ports detected
[   18.532951] ACPI: PCI Interrupt 0000:00:11.3[D] -> GSI 5 (level, low) -> IRQ 5
[   18.533067] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   18.533154] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[   18.533239] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000dc00
[   18.533467] usb usb2: configuration #1 chosen from 1 choice
[   18.533548] hub 2-0:1.0: USB hub found
[   18.533601] hub 2-0:1.0: 2 ports detected
[   18.636875] ACPI: PCI Interrupt 0000:00:11.4[D] -> GSI 5 (level, low) -> IRQ 5
[   18.636992] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   18.637084] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
[   18.637169] uhci_hcd 0000:00:11.4: irq 5, io base 0x0000e000
[   18.637383] usb usb3: configuration #1 chosen from 1 choice
[   18.637465] hub 3-0:1.0: USB hub found
[   18.637518] hub 3-0:1.0: 2 ports detected
[   18.764715] Driver 'sd' needs updating - please use bus_type methods
[   18.764933] sd 0:0:0:0: [sda] 30043440 512-byte hardware sectors (15382 MB)
[   18.765007] sd 0:0:0:0: [sda] Write Protect is off
[   18.765056] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.765088] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.765227] sd 0:0:0:0: [sda] 30043440 512-byte hardware sectors (15382 MB)
[   18.765294] sd 0:0:0:0: [sda] Write Protect is off
[   18.765343] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.765372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.765436]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.783877]  sda1 sda2
[   18.806025] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.817369] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.817465] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.824043] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   18.824108] Uniform CD-ROM driver Revision: 3.20
[   18.824243] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   18.900535] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   19.059243] usb 1-2: configuration #1 chosen from 1 choice
[   19.061179] hub 1-2:1.0: USB hub found
[   19.063100] hub 1-2:1.0: 4 ports detected
[   24.235780] kjournald starting.  Commit interval 5 seconds
[   24.235857] EXT3-fs: mounted filesystem with ordered data mode.
[   41.982538] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   42.481962] Linux agpgart interface v0.102
[   42.514890] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   42.520954] agpgart: AGP aperture is 64M @ 0xe0000000
[   42.690878] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[   42.886037] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.945680] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.041446] gameport: EMU10K1 is pci0000:00:07.1/gameport0, io 0xec00, speed 1217kHz
[   43.157405] irda_init()
[   43.157442] NET: Registered protocol family 23
[   43.437474] input: Power Button (FF) as /devices/virtual/input/input4
[   43.449161] ACPI: Power Button (FF) [PWRF]
[   43.449360] input: Power Button (CM) as /devices/virtual/input/input5
[   43.465131] ACPI: Power Button (CM) [PWRB]
[   43.465360] input: Sleep Button (CM) as /devices/virtual/input/input6
[   43.477146] ACPI: Sleep Button (CM) [SLPB]
[   45.946309] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 17
[   48.419036] lp: driver loaded but no devices found
[   48.801187] Adding 1349452k swap on /dev/sda2.  Priority:-1 extents:1 across:1349452k
[   49.257031] EXT3 FS on sda1, internal journal
[   50.240504] ip_tables: (C) 2000-2006 Netfilter Core Team
[   57.076946] No dock devices found.
[   60.824765] NET: Registered protocol family 10
[   60.825083] lo: Disabled Privacy Extensions
[   61.432912] [drm] Initialized drm 1.1.0 20060810
[   61.448031] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.448201] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   61.593287] ppdev: user-space parallel port driver
[   62.046837] audit(1209314249.796:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5489 profile="/usr/sbin/cupsd" namespace="default"
[   62.142488] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   62.142497] apm: overridden by ACPI.
[   62.383143] RPC: Registered udp transport module.
[   62.383153] RPC: Registered tcp transport module.
[   62.504454] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   62.507467] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   62.657673] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   62.664095] NFSD: starting 90-second grace period
[   63.266246] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   63.266274] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   63.266316] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   63.718834] [drm] Setting GART location based on new memory map
[   63.718854] [drm] Loading R200 Microcode
[   63.718897] [drm] writeback test succeeded in 1 usecs
[   64.320245] Bluetooth: Core ver 2.11
[   64.322576] NET: Registered protocol family 31
[   64.322585] Bluetooth: HCI device and connection manager initialized
[   64.322591] Bluetooth: HCI socket layer initialized
[   64.460773] Bluetooth: L2CAP ver 2.9
[   64.460782] Bluetooth: L2CAP socket layer initialized
[   64.577436] Bluetooth: RFCOMM socket layer initialized
[   64.577476] Bluetooth: RFCOMM TTY layer initialized
[   64.577479] Bluetooth: RFCOMM ver 1.8
[   69.885988] NET: Registered protocol family 17
[   82.706954] eth0: no IPv6 routers present
```

---

### Post by Mothinator on 2008-04-27
Doing a little bit of digging, I found that the problem was due to a misconfiguration of the program I use to hibernate my system, s2disk.

Editing grub to remove "quite splash" from the boot parameters led to this error message being displayed:
"Could not stat the resume device file '/dev/hda2' Please type in the full path name to try again or press enter to boot system:"

Pressing enter booted the system normally.

So it seems that the system was hanging because it was trying to read a resume image from /dev/hda2 which doesn't exist on my system. 

In order to fix it, I ran:
```
sudo dpkg-reconfigure uswsusp 
```

Then when it prompted for a device to save to, I selected /dev/sda2

This solved the problem.

---

### Post by thisiam on 2008-04-27
this is what i did and renamed it to just Ubuntu 8.04
and now it doesn't show the options that i commented out.

> 
#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic #root=UUID=bac88e9f-c369-4070-b18f-5f901d20ef8f ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

---

