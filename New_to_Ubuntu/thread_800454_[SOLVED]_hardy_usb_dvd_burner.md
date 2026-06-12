---
title: "[SOLVED] hardy usb dvd burner"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by linuxlizard on 2008-05-19
Hello All,
I have a usb dvd burner. It's an HP dvd840.

It seems to work every other ubuntu release since breezy badger.

It worked great in gutsy, so I guess it's time for it not to work in Hardy.

Can anyone help me get it working in hardy please?

Thanks!

---

### Post by HotShotDJ on 2008-05-19
> **linuxlizard said:**
> Can anyone help me get it working in hardy please?Is it not working at all?  Can it read CD's or DVD's but just is not detected as a burner or is it just a brick altogether?

---

### Post by linuxlizard on 2008-05-19
No, if I stick a cd or dvd in there, it doesn't appear to be working at all. I mean it's powered and spins and all, but ubuntu doesn't appear to notice.

---

### Post by SunnyRabbiera on 2008-05-19
strange, as usually HP DVD burners are knopwn to work with linux in general.

---

### Post by HotShotDJ on 2008-05-19
> **linuxlizard said:**
> No, if I stick a cd or dvd in there, it doesn't appear to be working at all. I mean it's powered and spins and all, but ubuntu doesn't appear to notice.Ok.  Please unplug it from your computer.  Then, in a terminal (Applications --> Accessories --> Terminal) type:```
dmesg
```Now, plug it back into your computer.  Open a SECOND terminal and again type:```
dmesg
```Please post ONLY the parts that changed toward the end of the dmesg output the second time (if anything).

---

### Post by linuxlizard on 2008-05-19
Ok, I'm not sure if I got the whole thing in terminal because it's so long and I couldn't scroll back up all the way to where I gave the original command, which leads me to believe some stuff at the beginning is chopped off, but here goes for what I could see:

These extra lines were at the end the second time I ran the command with the device plugged in:


[ 3243.039948] usb 4-3.3: new high speed USB device using ehci_hcd and address 17

[ 3243.127809] usb 4-3.3: device descriptor read/64, error -71

[ 3243.319524] usb 4-3.3: device descriptor read/64, error -71

[ 3243.511099] usb 4-3.3: new high speed USB device using ehci_hcd and address 18

[ 3243.598959] usb 4-3.3: device descriptor read/64, error -71

[ 3243.790667] usb 4-3.3: device descriptor read/64, error -71

[ 3243.982369] usb 4-3.3: new high speed USB device using ehci_hcd and address 19

[ 3244.389637] usb 4-3.3: device not accepting address 19, error -71

[ 3244.477487] usb 4-3.3: new high speed USB device using ehci_hcd and address 20

[ 3244.884790] usb 4-3.3: device not accepting address 20, error -71


It may be of interest to note that just prior to these lines were a few more lines of very similar error both times I ran the command (unplugged and plugged in).

---

### Post by HotShotDJ on 2008-05-19
> **linuxlizard said:**
> It may be of interest to note that just prior to these lines were a few more lines of very similar error both times I ran the command (unplugged and plugged in).Those line are enough.  The problem is with the USB port.  I've seen this a couple times.  First, try a different USB port on your computer... one that is not shared by the one you just tried.  See if that helps.  While your doing that, I'm going to check some things.

---

### Post by linuxlizard on 2008-05-19
OK, it was plugged into a hub.
Tried another port directly into the computer and no luck, tried my printer and no luck.

A little more info since you picked up on the port that may be relevant. 

The usb ports on this motherboard stopped working a year or so back. So I got a usb card which I plug everything into now instead of the original ports on the board. Maybe the errors are from the ports on the motherboard rather than the card?

Don't know...
Just in case it helps, here's the dmesg I took with the device plugged in:

[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   196592 
[    0.000000]   HighMem    196592 ->   196592 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   196592 
[    0.000000] On node 0 totalpages: 196592 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 1503 pages used for memmap 
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000]   Movable zone: 0 pages used for memmap 
[    0.000000] DMI 2.3 present. 
[    0.000000] ACPI: RSDP signature @ 0xC00FAA60 checksum 0 
[    0.000000] ACPI: RSDP 000FAA60, 0014 (r0 AMI   ) 
[    0.000000] ACPI: RSDT 2FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B) 
[    0.000000] ACPI: FACP 2FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B) 
[    0.000000] ACPI: DSDT 2FFF0120, 3300 (r1    SiS      746      100 MSFT  100000D) 
[    0.000000] ACPI: FACS 2FFF8000, 0040 
[    0.000000] ACPI: APIC 2FFF00C0, 005A (r1 AMIINT SiS740XX     1000 MSFT  100000B) 
[    0.000000] ACPI: PM-Timer IO Port: 0x808 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[    0.000000] Processor #0 6:10 APIC version 16 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000) 
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057 
[    0.000000] Kernel command line: root=UUID=5f24b8f4-821c-4803-aa93-007e759a69c0 ro quiet splash 
[    0.000000] mapped APIC to ffffb000 (fee00000) 
[    0.000000] mapped IOAPIC to ffffa000 (fec00000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[    0.000000] Detected 2012.546 MHz processor. 
[   26.244910] Console: colour VGA+ 80x25 
[   26.244915] console [tty0] enabled 
[   26.245910] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[   26.246618] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   26.277907] Memory: 767012k/786368k available (2157k kernel code, 18752k reserved, 998k data, 364k init, 0k highmem) 
[   26.277917] virtual kernel memory layout: 
[   26.277918]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) 
[   26.277920]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   26.277921]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB) 
[   26.277922]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB) 
[   26.277923]       .init : 0xc041b000 - 0xc0476000   ( 364 kB) 
[   26.277924]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB) 
[   26.277926]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB) 
[   26.277929] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   26.277994] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   26.357891] Calibrating delay using timer specific routine.. 4027.39 BogoMIPS (lpj=8054781) 
[   26.357938] Security Framework initialized 
[   26.357949] SELinux:  Disabled at boot. 
[   26.357979] AppArmor: AppArmor initialized 
[   26.357985] Failure registering capabilities with primary security module. 
[   26.357998] Mount-cache hash table entries: 512 
[   26.358198] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000 
[   26.358210] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   26.358213] CPU: L2 Cache: 512K (64 bytes/line) 
[   26.358217] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000 
[   26.358231] Compat vDSO mapped to ffffe000. 
[   26.358249] Checking 'hlt' instruction... OK. 
[   26.374184] SMP alternatives: switching to UP code 
[   26.375559] Freeing SMP alternatives: 11k freed 
[   26.375721] Early unpacking initramfs... done 
[   26.745879] ACPI: Core revision 20070126 
[   26.746008] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   26.747563] CPU0: AMD Athlon(tm) XP 2800+ stepping 00 
[   26.747591] Total of 1 processors activated (4027.39 BogoMIPS). 
[   26.747720] ENABLING IO-APIC IRQs 
[   26.747907] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[   26.893134] Brought up 1 CPUs 
[   26.893177] CPU0 attaching sched-domain: 
[   26.893180]  domain 0: span 01 
[   26.893182]   groups: 01 
[   26.893445] net_namespace: 64 bytes 
[   26.893457] Booting paravirtualized kernel on bare hardware 
[   26.893979] Time: 21:22:26  Date: 05/19/08 
[   26.894025] NET: Registered protocol family 16 
[   26.894300] EISA bus registered 
[   26.894325] ACPI: bus type pci registered 
[   26.896285] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2 
[   26.896288] PCI: Using configuration type 1 
[   26.896290] Setting up standard PCI resources 
[   26.898554] ACPI: EC: Look up EC in DSDT 
[   26.901455] ACPI: Interpreter enabled 
[   26.901459] ACPI: (supports S0 S1 S4 S5) 
[   26.901473] ACPI: Using IOAPIC for interrupt routing 
[   26.905405] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   26.905617] Enabling SiS 96x SMBus. 
[   26.906394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   26.916390] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[   26.916475] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   26.916559] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15) 
[   26.916645] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[   26.916730] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[   26.916814] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[   26.916899] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   26.916982] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 *12 14 15) 
[   26.917085] ACPI: Power Resource [URP1] (off) 
[   26.917109] ACPI: Power Resource [URP2] (off) 
[   26.917132] ACPI: Power Resource [FDDP] (off) 
[   26.917156] ACPI: Power Resource [LPTP] (off) 
[   26.917205] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   26.917245] pnp: PnP ACPI init 
[   26.917254] ACPI: bus type pnp registered 
[   26.919423] pnp: PnP ACPI: found 11 devices 
[   26.919426] ACPI: ACPI bus type pnp unregistered 
[   26.919431] PnPBIOS: Disabled by ACPI PNP 
[   26.919729] PCI: Using ACPI for IRQ routing 
[   26.919733] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   26.929045] NET: Registered protocol family 8 
[   26.929047] NET: Registered protocol family 20 
[   26.929160] AppArmor: AppArmor Filesystem Enabled 
[   26.932999] Time: tsc clocksource has been installed. 
[   26.941025] system 00:01: ioport range 0x4d0-0x4d1 has been reserved 
[   26.941029] system 00:01: ioport range 0x295-0x296 has been reserved 
[   26.941032] system 00:01: ioport range 0x800-0x87f has been reserved 
[   26.941035] system 00:01: ioport range 0x880-0x8ff has been reserved 
[   26.941037] system 00:01: ioport range 0xc00-0xc1f has been reserved 
[   26.941041] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved 
[   26.971490] PCI: Bridge: 0000:00:01.0 
[   26.971492]   IO window: disabled. 
[   26.971499]   MEM window: cbd00000-cfefffff 
[   26.971504]   PREFETCH window: aba00000-cbbfffff 
[   26.971535] NET: Registered protocol family 2 
[   27.009011] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   27.009514] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[   27.012446] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[   27.014016] TCP: Hash tables configured (established 131072 bind 65536) 
[   27.014020] TCP reno registered 
[   27.025089] checking if image is initramfs... it is 
[   27.472163] Switched to high resolution mode on CPU 0 
[   27.706076] Freeing initrd memory: 7700k freed 
[   27.707044] audit: initializing netlink socket (disabled) 
[   27.707069] audit(1211232146.324:1): initialized 
[   27.709493] VFS: Disk quotas dquot_6.5.1 
[   27.709587] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   27.709769] io scheduler noop registered 
[   27.709772] io scheduler anticipatory registered 
[   27.709775] io scheduler deadline registered 
[   27.709786] io scheduler cfq registered (default) 
[   27.709877] Boot video device is 0000:01:00.0 
[   27.710227] isapnp: Scanning for PnP cards... 
[   28.063366] isapnp: No Plug & Play device found 
[   28.096829] Real Time Clock Driver v1.12ac 
[   28.096968] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   28.097123] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   28.097902] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   28.098856] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   28.098954] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   28.099067] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[   28.099093] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp 
[   28.099221] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   28.107224] mice: PS/2 mouse device common for all mice 
[   28.107368] EISA: Probing bus 0 at eisa.0 
[   28.107406] EISA: Detected 0 cards. 
[   28.107411] cpuidle: using governor ladder 
[   28.107414] cpuidle: using governor menu 
[   28.107601] NET: Registered protocol family 1 
[   28.107639] Using IPI No-Shortcut mode 
[   28.107700] registered taskstats version 1 
[   28.107825]   Magic number: 8:472:399 
[   28.108133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   28.108136] EDD information not available. 
[   28.108836] Freeing unused kernel memory: 364k freed 
[   28.139063] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   29.354496] fuse init (API version 7.9) 
[   30.032996] SCSI subsystem initialized 
[   30.107326] libata version 3.00 loaded. 
[   30.119508] usbcore: registered new interface driver usbfs 
[   30.119547] usbcore: registered new interface driver hub 
[   30.139666] usbcore: registered new device driver usb 
[   30.151311] sis900.c: v1.08.10 Apr. 2 2006 
[   30.151437] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16 
[   30.152511] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1. 
[   30.163166] 0000:00:04.0: Using transceiver found at address 1 as default 
[   30.166372] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 16, 00:0b:6a:e7:b0:e6 
[   30.187762] pata_sis 0000:00:02.5: version 0.5.2 
[   30.197067] scsi0 : pata_sis 
[   30.203567] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   30.207508] scsi1 : pata_sis 
[   30.208272] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14 
[   30.208276] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15 
[   30.219749] USB Universal Host Controller Interface driver v3.0 
[   30.280659] Floppy drive(s): fd0 is 1.44M 
[   30.299260] FDC 0 is a post-1991 82077 
[   30.395625] ata1.00: ATA-7: WDC WD3200AAJB-00TYA0, 00.02C01, max UDMA/100 
[   30.395633] ata1.00: 625142448 sectors, multi 16: LBA48 
[   30.395777] ata1.01: ATA-7: SAMSUNG SP0802N, SM100-26, max UDMA/100 
[   30.395780] ata1.01: 156368016 sectors, multi 16: LBA48 
[   30.412463] ata1.00: configured for UDMA/100 
[   30.419619] ata1.01: configured for UDMA/100 
[   31.086398] ata2.00: ATAPI: LITE-ON CD-RW SOHR-5239V, 2$0B, max UDMA/33 
[   31.086420] ata2.01: ATAPI: LITE-ON DVD SOHD-16P9S, FS07, max UDMA/33 
[   31.274085] ata2.00: configured for UDMA/33 
[   31.445802] ata2.01: configured for UDMA/33 
[   31.446009] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJB-0 00.0 PQ: 0 ANSI: 5 
[   31.446554] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0802N  SM10 PQ: 0 ANSI: 5 
[   31.447538] scsi 1:0:0:0: CD-ROM            LITE-ON  CD-RW SOHR-5239V 2$0B PQ: 0 ANSI: 5 
[   31.448119] scsi 1:0:1:0: CD-ROM            LITE-ON  DVD SOHD-16P9S   FS07 PQ: 0 ANSI: 5 
[   31.451103] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17 
[   31.451125] ohci_hcd 0000:00:03.0: OHCI Host Controller 
[   31.451577] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1 
[   31.451604] ohci_hcd 0000:00:03.0: irq 17, io mem 0xcfffd000 
[   31.507646] usb usb1: configuration #1 chosen from 1 choice 
[   31.507682] hub 1-0:1.0: USB hub found 
[   31.507696] hub 1-0:1.0: 3 ports detected 
[   31.609473] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18 
[   31.609502] ohci_hcd 0000:00:03.1: OHCI Host Controller 
[   31.609537] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2 
[   31.609562] ohci_hcd 0000:00:03.1: irq 18, io mem 0xcfffe000 
[   31.667350] usb usb2: configuration #1 chosen from 1 choice 
[   31.667383] hub 2-0:1.0: USB hub found 
[   31.667395] hub 2-0:1.0: 3 ports detected 
[   31.769636] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 19 
[   31.769661] ehci_hcd 0000:00:03.2: EHCI Host Controller 
[   31.769701] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3 
[   31.769753] PCI: cache line size of 64 is not supported by device 0000:00:03.2 
[   31.769779] ehci_hcd 0000:00:03.2: irq 19, io mem 0xcffff000 
[   31.781071] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   31.781281] usb usb3: configuration #1 chosen from 1 choice 
[   31.781328] hub 3-0:1.0: USB hub found 
[   31.781340] hub 3-0:1.0: 6 ports detected 
[   31.885021] ACPI: PCI Interrupt 0000:00:0a.2[C] -> GSI 16 (level, low) -> IRQ 20 
[   31.885049] ehci_hcd 0000:00:0a.2: EHCI Host Controller 
[   31.885105] ehci_hcd 0000:00:0a.2: new USB bus registered, assigned bus number 4 
[   31.885177] ehci_hcd 0000:00:0a.2: irq 20, io mem 0xcfffbf00 
[   31.896816] ehci_hcd 0000:00:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   31.896935] usb usb4: configuration #1 chosen from 1 choice 
[   31.896965] hub 4-0:1.0: USB hub found 
[   31.896973] hub 4-0:1.0: 4 ports detected 
[   32.001266] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 21 
[   32.001290] uhci_hcd 0000:00:0a.0: UHCI Host Controller 
[   32.001333] uhci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 5 
[   32.001366] uhci_hcd 0000:00:0a.0: irq 21, io base 0x0000cc00 
[   32.001526] usb usb5: configuration #1 chosen from 1 choice 
[   32.001556] hub 5-0:1.0: USB hub found 
[   32.001571] hub 5-0:1.0: 2 ports detected 
[   32.104659] ACPI: PCI Interrupt 0000:00:0a.1[B] -> GSI 19 (level, low) -> IRQ 16 
[   32.104681] uhci_hcd 0000:00:0a.1: UHCI Host Controller 
[   32.104717] uhci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 6 
[   32.104753] uhci_hcd 0000:00:0a.1: irq 16, io base 0x0000d000 
[   32.104918] usb usb6: configuration #1 chosen from 1 choice 
[   32.104956] hub 6-0:1.0: USB hub found 
[   32.104966] hub 6-0:1.0: 2 ports detected 
[   32.219561] Driver 'sd' needs updating - please use bus_type methods 
[   32.219730] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB) 
[   32.219750] sd 0:0:0:0: [sda] Write Protect is off 
[   32.219753] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   32.219776] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.219851] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB) 
[   32.219863] sd 0:0:0:0: [sda] Write Protect is off 
[   32.219865] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   32.219884] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.219889]  sda: sda1 sda2 sda3 sda4 
[   32.233120] Driver 'sr' needs updating - please use bus_type methods 
[   32.242088] sd 0:0:0:0: [sda] Attached SCSI disk 
[   32.242213] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB) 
[   32.242234] sd 0:0:1:0: [sdb] Write Protect is off 
[   32.242238] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00 
[   32.242260] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.242324] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB) 
[   32.242337] sd 0:0:1:0: [sdb] Write Protect is off 
[   32.242339] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00 
[   32.242358] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.242363]  sdb: sdb1 sdb2 sdb3 
[   32.254213] sd 0:0:1:0: [sdb] Attached SCSI disk 
[   32.263592] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray 
[   32.263604] Uniform CD-ROM driver Revision: 3.20 
[   32.263695] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   32.266384] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray 
[   32.266430] sr 1:0:1:0: Attached scsi CD-ROM sr1 
[   32.269735] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[   32.269765] sd 0:0:1:0: Attached scsi generic sg1 type 0 
[   32.269790] sr 1:0:0:0: Attached scsi generic sg2 type 5 
[   32.269813] sr 1:0:1:0: Attached scsi generic sg3 type 5 
[   32.479864] usb 4-2: new high speed USB device using ehci_hcd and address 3 
[   32.612752] usb 4-2: configuration #1 chosen from 1 choice 
[   32.851270] usb 4-3: new high speed USB device using ehci_hcd and address 4 
[   32.900792] Attempting manual resume 
[   32.900800] swsusp: Resume From Partition 8:2 
[   32.900802] PM: Checking swsusp image. 
[   32.901062] PM: Resume from disk failed. 
[   32.927819] kjournald starting.  Commit interval 5 seconds 
[   32.927845] EXT3-fs: mounted filesystem with ordered data mode. 
[   32.983914] usb 4-3: configuration #1 chosen from 1 choice 
[   32.984154] hub 4-3:1.0: USB hub found 
[   32.984251] hub 4-3:1.0: 4 ports detected 
[   33.326502] usb 5-1: new full speed USB device using uhci_hcd and address 2 
[   33.495167] usb 5-1: configuration #1 chosen from 1 choice 
[   33.497953] hub 5-1:1.0: USB hub found 
[   33.499916] hub 5-1:1.0: 4 ports detected 
[   34.205126] usb 4-3.3: new high speed USB device using ehci_hcd and address 5 
[   34.292989] usb 4-3.3: device descriptor read/64, error -71 
[   34.484699] usb 4-3.3: device descriptor read/64, error -71 
[   34.676277] usb 4-3.3: new high speed USB device using ehci_hcd and address 6 
[   34.764138] usb 4-3.3: device descriptor read/64, error -71 
[   34.955843] usb 4-3.3: device descriptor read/64, error -71 
[   35.147559] usb 4-3.3: new high speed USB device using ehci_hcd and address 7 
[   35.554790] usb 4-3.3: device not accepting address 7, error -71 
[   35.642787] usb 4-3.3: new high speed USB device using ehci_hcd and address 8 
[   36.049970] usb 4-3.3: device not accepting address 8, error -71 
[   36.255309] usb 5-1.3: new low speed USB device using uhci_hcd and address 3 
[   36.392257] usb 5-1.3: configuration #1 chosen from 1 choice 
[   36.397114] usbcore: registered new interface driver libusual 
[   36.436953] Initializing USB Mass Storage driver... 
[   36.437083] scsi2 : SCSI emulation for USB Mass Storage devices 
[   36.437178] usbcore: registered new interface driver usb-storage 
[   36.437183] USB Mass Storage support registered. 
[   36.437500] usb-storage: device found at 3 
[   36.437503] usb-storage: waiting for device to settle before scanning 
[   39.207509] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   39.264744] Linux agpgart interface v0.102 
[   39.320837] agpgart: Detected SiS chipset - id:1857 
[   39.327720] agpgart: AGP aperture is 64M @ 0xd0000000 
[   39.388746] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   39.520528] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00 
[   39.676343] input: Power Button (FF) as /devices/virtual/input/input2 
[   39.688683] ACPI: Power Button (FF) [PWRF] 
[   39.688945] input: Power Button (CM) as /devices/virtual/input/input3 
[   39.703961] ACPI: Power Button (CM) [PWRB] 
[   41.193107] nvidia: module license 'NVIDIA' taints kernel. 
[   41.465065] usb-storage: device scan complete 
[   41.465635] scsi 2:0:0:0: Direct-Access     HP       Photosmart D7100 1.00 PQ: 0 ANSI: 2 
[   41.467007] sd 2:0:0:0: [sdc] Attached SCSI removable disk 
[   41.467058] sd 2:0:0:0: Attached scsi generic sg4 type 0 
[   42.480442] input: PC Speaker as /devices/platform/pcspkr/input/input4 
[   42.858961] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21 
[   42.918987] parport_pc 00:09: reported by Plug and Play ACPI 
[   42.919115] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA] 
[   43.182232] intel8x0_measure_ac97_clock: measured 55719 usecs 
[   43.182242] intel8x0: clocking to 48000 
[   43.546641] usbcore: registered new interface driver hiddev 
[   43.559540] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:0a.0/usb5/5-1/5-1.3/5-1.3:1.0/input/input5 
[   43.561461] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC602 
[   43.593689] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0a.0-1.3 
[   43.593727] usbcore: registered new interface driver usbhid 
[   43.593733] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver 
[   43.594419] usbcore: registered new interface driver usblp 
[   43.615256] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   43.615971] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008 
[   46.286573] lp0: using parport0 (interrupt-driven). 
[   46.347841] Adding 522104k swap on /dev/sda2.  Priority:-1 extents:1 across:522104k 
[   46.352096] Adding 522104k swap on /dev/sdb2.  Priority:-2 extents:1 across:522104k 
[   46.910942] EXT3 FS on sda3, internal journal 
[   47.679233] kjournald starting.  Commit interval 5 seconds 
[   47.679492] EXT3 FS on sda4, internal journal 
[   47.679499] EXT3-fs: mounted filesystem with ordered data mode. 
[   48.460931] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   48.978182] No dock devices found. 
[   50.139700] apm: BIOS not found. 
[   50.265151] ppdev: user-space parallel port driver 
[   50.357579] audit(1211246570.174:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4974 profile="/usr/sbin/cupsd" namespace="default" 
[   53.014465] Bluetooth: Core ver 2.11 
[   53.015938] NET: Registered protocol family 31 
[   53.015945] Bluetooth: HCI device and connection manager initialized 
[   53.015951] Bluetooth: HCI socket layer initialized 
[   53.057295] Bluetooth: L2CAP ver 2.9 
[   53.057305] Bluetooth: L2CAP socket layer initialized 
[   53.193113] usb 4-3.3: new high speed USB device using ehci_hcd and address 9 
[   53.202346] Bluetooth: RFCOMM socket layer initialized 
[   53.203181] Bluetooth: RFCOMM TTY layer initialized 
[   53.203186] Bluetooth: RFCOMM ver 1.8 
[   53.281645] usb 4-3.3: device descriptor read/64, error -71 
[   53.473370] usb 4-3.3: device descriptor read/64, error -71 
[   53.665048] usb 4-3.3: new high speed USB device using ehci_hcd and address 10 
[   53.752911] usb 4-3.3: device descriptor read/64, error -71 
[   53.944649] usb 4-3.3: device descriptor read/64, error -71 
[   54.136201] usb 4-3.3: new high speed USB device using ehci_hcd and address 11 
[   54.543494] usb 4-3.3: device not accepting address 11, error -71 
[   54.631463] usb 4-3.3: new high speed USB device using ehci_hcd and address 12 
[   54.900160] eth0: Media Link On 100mbps full-duplex 
[   55.038694] usb 4-3.3: device not accepting address 12, error -71 
[   55.270124] NET: Registered protocol family 17 
[   55.746530] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0. 
[   55.746558] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode 
[   55.747761] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode 
[   58.666653] NET: Registered protocol family 10 
[   58.667702] lo: Disabled Privacy Extensions 
[   68.891858] eth0: no IPv6 routers present 
[   72.216959] cdrom: sr0: mrw address space DMA selected 
[   72.327140] cdrom: sr0: mrw address space DMA selected 
[   72.347421] UDF-fs: No VRS found 
[   72.383734] ISO 9660 Extensions: Microsoft Joliet Level 3 
[   72.384915] ISOFS: changing to secondary root 
[ 2496.821873] usb 4-3.3: new high speed USB device using ehci_hcd and address 13 
[ 2496.909732] usb 4-3.3: device descriptor read/64, error -71 
[ 2497.101440] usb 4-3.3: device descriptor read/64, error -71 
[ 2497.293143] usb 4-3.3: new high speed USB device using ehci_hcd and address 14 
[ 2497.381008] usb 4-3.3: device descriptor read/64, error -71 
[ 2497.572718] usb 4-3.3: device descriptor read/64, error -71 
[ 2497.764421] usb 4-3.3: new high speed USB device using ehci_hcd and address 15 
[ 2498.171616] usb 4-3.3: device not accepting address 15, error -71 
[ 2498.259532] usb 4-3.3: new high speed USB device using ehci_hcd and address 16 
[ 2498.666802] usb 4-3.3: device not accepting address 16, error -71 
[ 3243.039948] usb 4-3.3: new high speed USB device using ehci_hcd and address 17 
[ 3243.127809] usb 4-3.3: device descriptor read/64, error -71 
[ 3243.319524] usb 4-3.3: device descriptor read/64, error -71 
[ 3243.511099] usb 4-3.3: new high speed USB device using ehci_hcd and address 18 
[ 3243.598959] usb 4-3.3: device descriptor read/64, error -71 
[ 3243.790667] usb 4-3.3: device descriptor read/64, error -71 
[ 3243.982369] usb 4-3.3: new high speed USB device using ehci_hcd and address 19 
[ 3244.389637] usb 4-3.3: device not accepting address 19, error -71 
[ 3244.477487] usb 4-3.3: new high speed USB device using ehci_hcd and address 20 
[ 3244.884790] usb 4-3.3: device not accepting address 20, error -71

---

### Post by HotShotDJ on 2008-05-19
> **linuxlizard said:**
> The usb ports on this motherboard stopped working a year or so back. So I got a usb card which I plug everything into now instead of the original ports on the board. Maybe the errors are from the ports on the motherboard rather than the card?Well, the errors are from the port that you are plugging the device into.  Something is causing a conflict.  That USB card.  Is it a PCI card?  If so, try shutting down your computer and moving it to a different slot.  Believe it or not, I have a nearly 100% "fix" rate by doing this when I start having trouble with a PCI card.

---

### Post by linuxlizard on 2008-05-19
Looks like that did the trick! thank you!

I'm a little nervous using that slot- it's right next to my nvidia agp card, so not a lot of airflow there- very tiny space between them. Hopefully I won't fry anything. But I've only got two pci slots on this motherboard so it's either the one that works but crowding the nvidia card or the one that doesn't...

---

