---
title: "LinuxMint FluxBox/Xubuntu"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by earle79 on 2008-11-30
Ok, little background.  I have an old HP computer, I installed Xubuntu on, long story short was too much for the little resources I have.  But will using it picked up my wireless card on boot up.  It is a Belkin F5D7000f rev20.

Ok, so then I found Mint running FluxBox.  Works great, fairly smooth, little slow, but I expected that.  One issue it doesn't like my wireless card at all.  Why?  Only thing I can guess is that Mint uses 8.4ubuntu and the xubuntu i used was 8.10.  Is there a way to find out exactly how the 8.10 uses this card?  

One more interesting thing is I had a syslog file when i was tried to troubleshoot the xubunto and it list the driver as 8010, but everything i find on this card everyone attempts to use 8510.

i tried the linuxmint wiki for wifi and can't get it to work, found another couple post on this site, and still no luck.

any insight would be helpful.thanks in advance.

---

### Post by gn2 on 2008-11-30
Have you tried Ndiswrapper? [http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)

---

### Post by earle79 on 2008-11-30
> **gn2 said:**
> Have you tried Ndiswrapper? [http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)

yes i did.  it didn't work though, the light on the card flashes orange but no networks was ever found, i don't know if i did it right or not?  im really confused. just don't know where to even start.  this is all very new to me.

---

### Post by earle79 on 2008-11-30
holy crap im pulling my hair out here.  I cant get this card to got to wlan0.  its still registering as a belkin unknown

---

### Post by ugm6hr on 2008-11-30
On both distros, check the output from:
```
lshw -class network
```

This will demonstrate what driver is being used.

---

### Post by yaknowwat on 2008-11-30
You might like CruchBang linux if its resources that your trying to save.

[http://www.crunchbanglinux.org/wiki/release-notes/8.10.01](http://www.crunchbanglinux.org/wiki/release-notes/8.10.01)

---

### Post by earle79 on 2008-11-30
> **ugm6hr said:**
> On both distros, check the output from:
```
lshw -class network
```

This will demonstrate what driver is being used.


```
earle@linuxdesktop ~ $ lshw -class network

WARNING: you should run this program as super-user.

  *-network UNCLAIMED     

       description: Ethernet controller

       product: Belkin

       vendor: Belkin

       physical id: 9

       bus info: pci@0000:01:09.0

       version: 20

       width: 32 bits

       clock: 33MHz

       capabilities: cap_list

       configuration: latency=64 maxlatency=64 mingnt=32
earle@linuxdesktop ~ $ 
```

---

### Post by ugm6hr on 2008-12-01
Is that the same on Xubuntu 8.10?  If so, I can't see how it is working with no driver installed.

---

### Post by aysiu on 2008-12-01
Why not just keep Xubuntu installed and then just use Fluxbox instead of Xfce?

---

### Post by earle79 on 2008-12-01
here is a little up date for what i got going on so far.  i got the ndiswrapper and driver installed but keep restarting an no connection is actually made.  the following is a dmesg but dont know what it all means. any help is apreciated.

> **earle79 said:**
> ok got some issues no connection yet and i have to sleep but here is dmesg for you to look at.  why is it resetting so much?

```
 ________________________
/ I'll burn my books.    \
|                        |
\ -- Christopher Marlowe /
 ------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
earle@linuxdesktop ~ $ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ef0000 - 0000000007effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007effc00 - 0000000007f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007f00000 - 0000000008000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 126MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32496) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32496
[    0.000000]   HighMem     32496 ->    32496
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32496
[    0.000000] On node 0 totalpages: 32496
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 221 pages used for memmap
[    0.000000]   Normal zone: 28179 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7280 checksum 0
[    0.000000] ACPI: RSDP 000F7280, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 07EFCAB8, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 07EFFB64, 0074 (r1 HP     Hawk      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 07EFCAE4, 3080 (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 07EFFFC0, 0040
[    0.000000] ACPI: BOOT 07EFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32243
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0110b000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 801.847 MHz processor.
[   24.265505] Console: colour VGA+ 80x25
[   24.265518] console [tty0] enabled
[   24.265765] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   24.265980] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   24.279298] Memory: 115548k/129984k available (2157k kernel code, 13892k reserved, 998k data, 364k init, 0k highmem)
[   24.279321] virtual kernel memory layout:
[   24.279324]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.279327]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.279331]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   24.279334]     lowmem  : 0xc0000000 - 0xc7ef0000   ( 126 MB)
[   24.279338]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   24.279341]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   24.279345]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   24.279354] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.279444] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.359478] Calibrating delay using timer specific routine.. 1605.25 BogoMIPS (lpj=3210514)
[   24.359553] Security Framework initialized
[   24.359575] SELinux:  Disabled at boot.
[   24.359613] AppArmor: AppArmor initialized
[   24.359624] Failure registering capabilities with primary security module.
[   24.359648] Mount-cache hash table entries: 512
[   24.360002] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   24.360039] CPU: L1 I cache: 16K, L1 D cache: 16K
[   24.360046] CPU: L2 cache: 128K
[   24.360055] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   24.360092] Compat vDSO mapped to ffffe000.
[   24.360134] Checking 'hlt' instruction... OK.
[   24.376106] SMP alternatives: switching to UP code
[   24.379599] Freeing SMP alternatives: 11k freed
[   24.379994] Early unpacking initramfs... done
[   25.451090] ACPI: Core revision 20070126
[   25.451328] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.454048] ACPI: setting ELCR to 0200 (from 0a00)
[   25.454701] CPU0: Intel Celeron (Coppermine) stepping 0a
[   25.454720] SMP motherboard not detected.
[   25.454726] Local APIC not detected. Using dummy APIC emulation.
[   25.454863] Brought up 1 CPUs
[   25.454923] CPU0 attaching sched-domain:
[   25.454932]  domain 0: span 01
[   25.454938]   groups: 01
[   25.455651] net_namespace: 64 bytes
[   25.455677] Booting paravirtualized kernel on bare hardware
[   25.457356] Time:  5:10:36  Date: 12/01/08
[   25.457462] NET: Registered protocol family 16
[   25.458407] EISA bus registered
[   25.458448] ACPI: bus type pci registered
[   25.459775] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[   25.459786] PCI: Using configuration type 1
[   25.459791] Setting up standard PCI resources
[   25.468887] ACPI: EC: Look up EC in DSDT
[   25.474603] ACPI: Interpreter enabled
[   25.474614] ACPI: (supports S0 S1 S5)
[   25.474641] ACPI: Using PIC for interrupt routing
[   25.487841] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.488268] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   25.488279] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   25.488880] PCI: Transparent bridge - 0000:00:1e.0
[   25.488929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.489050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[   25.493487] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   25.493731] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   25.493961] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[   25.494193] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   25.494701] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.494836] pnp: PnP ACPI init
[   25.494866] ACPI: bus type pnp registered
[   25.502510] ACPI Error (dsopcode-0548): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20070126]
[   25.502532] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c5b08360), AE_AML_BUFFER_LIMIT
[   25.502594] ACPI Error (uteval-0233): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node c5b08360), AE_AML_BUFFER_LIMIT
[   25.502612] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0400
[   25.504018] pnp: PnP ACPI: found 13 devices
[   25.504033] ACPI: ACPI bus type pnp unregistered
[   25.504044] PnPBIOS: Disabled by ACPI PNP
[   25.505130] PCI: Using ACPI for IRQ routing
[   25.505146] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.523490] NET: Registered protocol family 8
[   25.523502] NET: Registered protocol family 20
[   25.523798] AppArmor: AppArmor Filesystem Enabled
[   25.527460] Time: tsc clocksource has been installed.
[   25.535672] system 00:01: ioport range 0x1000-0x105f has been reserved
[   25.535683] system 00:01: ioport range 0x1060-0x107f has been reserved
[   25.535691] system 00:01: ioport range 0x1180-0x11bf has been reserved
[   25.535700] system 00:01: ioport range 0x1c00-0x1c7f has been reserved
[   25.535707] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.535714] system 00:01: ioport range 0x800-0x87f has been reserved
[   25.535728] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[   25.567546] PCI: Bridge: 0000:00:1e.0
[   25.567560]   IO window: 2000-2fff
[   25.567571]   MEM window: f4100000-f41fffff
[   25.567578]   PREFETCH window: disabled.
[   25.567601] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.567644] NET: Registered protocol family 2
[   25.607726] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   25.608391] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   25.608511] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   25.608623] TCP: Hash tables configured (established 4096 bind 4096)
[   25.608630] TCP reno registered
[   25.619929] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   26.476223]  it is
[   27.600293] Freeing initrd memory: 8658k freed
[   27.600961] Simple Boot Flag at 0x36 set to 0x1
[   27.602356] audit: initializing netlink socket (disabled)
[   27.602403] audit(1228108238.324:1): initialized
[   27.610834] VFS: Disk quotas dquot_6.5.1
[   27.611190] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.611848] io scheduler noop registered
[   27.611859] io scheduler anticipatory registered
[   27.611865] io scheduler deadline registered
[   27.611936] io scheduler cfq registered (default)
[   27.611974] Boot video device is 0000:00:01.0
[   27.613067] isapnp: Scanning for PnP cards...
[   27.967398] isapnp: No Plug & Play device found
[   28.191006] Real Time Clock Driver v1.12ac
[   28.191529] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.191856] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.192451] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.195020] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.196280] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.199882] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.200163] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.200594] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   28.203868] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.203886] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.207723] mice: PS/2 mouse device common for all mice
[   28.208261] EISA: Probing bus 0 at eisa.0
[   28.208282] Cannot allocate resource for EISA slot 1
[   28.208290] Cannot allocate resource for EISA slot 2
[   28.208324] EISA: Detected 0 cards.
[   28.208334] cpuidle: using governor ladder
[   28.208339] cpuidle: using governor menu
[   28.208915] NET: Registered protocol family 1
[   28.209026] Using IPI No-Shortcut mode
[   28.209124] registered taskstats version 1
[   28.209347]   Magic number: 4:255:162
[   28.209439]   hash matches device ttyq2
[   28.209583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.209589] EDD information not available.
[   28.211345] Freeing unused kernel memory: 364k freed
[   28.238999] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   29.964378] fuse init (API version 7.9)
[   30.056073] ACPI: Invalid PBLK length [5]
[   31.448507] SCSI subsystem initialized
[   31.623801] usbcore: registered new interface driver usbfs
[   31.623879] usbcore: registered new interface driver hub
[   31.664178] usbcore: registered new device driver usb
[   31.822952] USB Universal Host Controller Interface driver v3.0
[   31.823591] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   31.823604] PCI: setting IRQ 11 as level-triggered
[   31.823611] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   31.823638] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.823648] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   31.824289] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   31.824344] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001080
[   31.824773] usb usb1: configuration #1 chosen from 1 choice
[   31.824853] hub 1-0:1.0: USB hub found
[   31.824874] hub 1-0:1.0: 2 ports detected
[   31.887783] libata version 3.00 loaded.
[   31.979065] ata_piix 0000:00:1f.1: version 2.12
[   31.979221] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.997586] scsi0 : ata_piix
[   32.038882] scsi1 : ata_piix
[   32.039073] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
[   32.039081] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
[   32.166919] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   32.203612] ata1.00: ATA-5: QUANTUM FIREBALLlct20 20, APL.0900, max UDMA/100
[   32.203627] ata1.00: 39876480 sectors, multi 8: LBA 
[   32.203673] ata1.00: limited to UDMA/33 due to 40-wire cable
[   32.219610] ata1.00: configured for UDMA/33
[   32.341688] usb 1-1: configuration #1 chosen from 1 choice
[   32.539180] ata2.00: ATAPI: LG      CD-ROM CRD-8485B, 1.00, max MWDMA2
[   32.555204] Floppy drive(s): fd0 is 1.44M
[   32.576625] FDC 0 is a post-1991 82077
[   32.703138] ata2.00: configured for MWDMA2
[   32.703551] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
[   32.704230] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8485B 1.00 PQ: 0 ANSI: 5
[   34.614797] Driver 'sd' needs updating - please use bus_type methods
[   34.619753] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   34.619802] sd 0:0:0:0: [sda] Write Protect is off
[   34.619811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.619869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.620041] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   34.620076] sd 0:0:0:0: [sda] Write Protect is off
[   34.620083] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.620140] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.620154]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.644234] usbcore: registered new interface driver libusual
[   34.659046]  sda1 sda2 <<6>Initializing USB Mass Storage driver...
[   34.673381] scsi2 : SCSI emulation for USB Mass Storage devices
[   34.675416] usbcore: registered new interface driver usb-storage
[   34.675441] USB Mass Storage support registered.
[   34.675780] usb-storage: device found at 2
[   34.675788] usb-storage: waiting for device to settle before scanning
[   34.681365]  sda5 >
[   34.681662] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.702834] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   34.702853] Uniform CD-ROM driver Revision: 3.20
[   34.703033] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   34.713365] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.713428] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   35.906094] Attempting manual resume
[   35.906111] swsusp: Resume From Partition 8:5
[   35.906117] PM: Checking swsusp image.
[   35.918099] PM: Resume from disk failed.
[   36.036054] kjournald starting.  Commit interval 5 seconds
[   36.036100] EXT3-fs: mounted filesystem with ordered data mode.
[   39.675674] usb-storage: device scan complete
[   39.678657] scsi 2:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[   39.689569] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   39.692562] sd 2:0:0:0: [sdb] Write Protect is off
[   39.692574] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   39.692580] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.704558] sd 2:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[   39.707577] sd 2:0:0:0: [sdb] Write Protect is off
[   39.707591] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   39.707598] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.707616]  sdb: sdb1
[   39.753855] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   39.753976] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   52.205929] Linux agpgart interface v0.102
[   52.298867] agpgart: Detected an Intel i810 Chipset.
[   52.433142] intel_rng: FWH not detected
[   52.442597] agpgart: AGP aperture is 64M @ 0xf8000000
[   52.540044] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.607436] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.004908] iTCO_vendor_support: vendor-support=0
[   53.261432] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   53.261707] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   53.261726] iTCO_wdt: No card detected
[   53.325590] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   53.946802] logips2pp: Detected unknown logitech mouse model 63
[   54.154721] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   54.473293] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input2
[   54.497186] input: Power Button (FF) as /devices/virtual/input/input3
[   54.509376] ACPI: Power Button (FF) [PWRF]
[   54.509799] input: Power Button (CM) as /devices/virtual/input/input4
[   54.524725] ACPI: Power Button (CM) [PWRB]
[   55.094580] ndiswrapper: driver blkwgdv7 (Belkin,10/19/2006,5.87.19.106) loaded
[   55.095349] PCI: Enabling device 0000:01:09.0 (0110 -> 0113)
[   55.095821] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   55.095830] PCI: setting IRQ 9 as level-triggered
[   55.095837] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   56.168591] mpu401 00:0c: activated
[   57.066179] ndiswrapper: using IRQ 9
[   63.436628] wlan0: ethernet device 00:17:3f:2e:5d:06 using NDIS driver: blkwgdv7, version: 0x50056, NDIS version: 0x500, vendor: 'Belkin Wireless G Notebook/Desktop Card                                     ', 1799:700F.5.conf
[   63.436783] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   63.437103] usbcore: registered new interface driver ndiswrapper
[   63.437712] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   63.437768] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   64.031732] intel8x0_measure_ac97_clock: measured 55254 usecs
[   64.031745] intel8x0: clocking to 48000
[   64.595530] NET: Registered protocol family 17
[   65.277364] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[   65.373610] lp0: using parport0 (polling).
[   65.869662] Adding 361420k swap on /dev/sda5.  Priority:-1 extents:1 across:361420k
[   66.694318] EXT3 FS on sda1, internal journal
[   67.107627] device-mapper: uevent: version 1.0.3
[   67.107738] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   70.001276] ip_tables: (C) 2000-2006 Netfilter Core Team
[   72.394481] No dock devices found.
[   78.036958] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   78.036974] apm: overridden by ACPI.
[   78.373733] ppdev: user-space parallel port driver
[   79.616648] audit(1228108290.822:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4803 profile="/usr/sbin/cupsd" namespace="default"
[   85.942101] Bluetooth: Core ver 2.11
[   85.944402] NET: Registered protocol family 31
[   85.944419] Bluetooth: HCI device and connection manager initialized
[   85.944430] Bluetooth: HCI socket layer initialized
[   86.169688] Bluetooth: L2CAP ver 2.9
[   86.169705] Bluetooth: L2CAP socket layer initialized
[   86.215292] Bluetooth: RFCOMM socket layer initialized
[   86.216653] Bluetooth: RFCOMM TTY layer initialized
[   86.216673] Bluetooth: RFCOMM ver 1.8
[   93.937284] [drm] Initialized drm 1.1.0 20060810
[   93.961136] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   93.961160] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   93.961176] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   93.961611] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   93.962897] mtrr: base(0xf8000000) is not aligned on a size(0x180000) boundary
[   94.145845] [drm] Using v1.4 init.
[   97.708413] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   97.708425] 	driver to use reclaim_buffers_idlelocked() instead.
[   97.708428] 	I will go on reclaiming the buffers anyway.
[ 1177.327379] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1191.326650] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1201.325057] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1211.324158] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1225.323550] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1237.321615] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1255.319796] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1269.328711] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1283.317087] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1303.315137] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1317.313831] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1329.312646] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1343.311223] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1357.309873] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1371.308498] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1389.317015] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1403.305383] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1431.302730] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1443.301568] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1457.310454] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1469.299441] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1483.297592] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1525.293530] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1543.291811] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1557.290399] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1581.288073] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1597.286574] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1611.285232] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1623.284010] ndiswrapper (mp_reset:62): wlan0 is being reset
[ 1637.290726] ndiswrapper (mp_reset:62): wlan0 is being reset
earle@linuxdesktop ~ $ 

```

> **earle79 said:**
> OK, i finally found the right one its version 7  using the win98 version.  there is still a few issues though.  im rebooting now it was acting wierd.  still dont have actual connection but i got the driver installed. 

when i then type sudo ndiswrapper -m it says "modprobe config already contains alias directive" 

so dont know what that means.  i just know that wcid doest pick anything up but network manager did.  oh its done rebooting.  i will check some things.

---

### Post by ugm6hr on 2008-12-01
> **earle79 said:**
> any help is apreciated.

Unfortunately, I have no idea what you are doing now either.

I would again suggest you give us the information regarding Xubuntu (where it worked automatically).

This would allow any of the following:
1. aysui's suggestion of Fluxbox + 8.10
2. yaknowat's suggestion of Crunchbang (8.10 + Openbox)
3. Asking on the Mint forum how to get the same driver to work in Mint Fluxbox

---

### Post by earle79 on 2008-12-01
> **ugm6hr said:**
> [SIZE="1"]Unfortunately, I have no idea what you are doing now either.

I would again suggest you give us the information regarding Xubuntu (where it worked automatically).

This would allow any of the following:
1. aysui's suggestion of Fluxbox + 8.10
2. yaknowat's suggestion of Crunchbang (8.10 + Openbox)
3. Asking on the Mint forum how to get the same driver to work in Mint Fluxbox[/SIZE]

Ok, you are probably right.  well i guess im just in for the thrill of the hunt?  

Does anyone have any opinions on Fluxbox and Openbox?  Soes anyone have any experience with either one?  Personal preferances? Likes or dislikes on either?

---

### Post by 4Orbs on 2008-12-01
I suggest asking this question on the Other OS Talk section of this forum. That seems to be where the enthusiasts of alternative desktops hang out.

My opinion: Linux Mint Fluxbox CE is the most user friendly Fluxbox distro. Mainly because it auto-updates the menus when you install new stuff. But the 8.10 version is not out yet. Crunchbang 8.10 is my favorite Openbox distro. If Xubuntu already works for you (sluggishly), I suggest keeping it and reducing the demand on your machine by disabling the services you don't use and disabling some of the autostart programs that can be managed at your convenience. like system updates.

---

### Post by snowpine on 2008-12-01
> **earle79 said:**
> Ok, you are probably right.  well i guess im just in for the thrill of the hunt?  

Does anyone have any opinions on Fluxbox and Openbox?  Soes anyone have any experience with either one?  Personal preferances? Likes or dislikes on either?

My favorite Fluxbox distro is Fluxbuntu. The project was defunct for a while, but now they seem to be gearing back up for an Intrepid release (fluxbuntu.org).

However, I am now really, really enjoying Openbox. My two favorite Openbox distros are Crunchbang and SliTaz. Definitely worth checking out!

I think the *box windows managers are far superior to Gnome, KDE, etc. for highly productive every day use. That's just my opinion. :)

---

### Post by ugm6hr on 2008-12-02
> **earle79 said:**
> Does anyone have any opinions on Fluxbox and Openbox?

I only briefly dabbled with both.

However, if you want something "user-friendly" and light, I would suggest LXDE.  It is built on a backbone of Openbox with panels, pcmanfm (file manager like thunar) and a menu package.

[http://wiki.lxde.org/en/Ubuntu#Minimal_Ubuntu_.2B_LXDE_Installation](http://wiki.lxde.org/en/Ubuntu#Minimal_Ubuntu_.2B_LXDE_Installation)

There is a new U-lite, which is 8.10+LXDE, but it is still alpha (and I haven't tried it).

---

