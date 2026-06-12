---
title: "[SOLVED] Hardy install teething problems"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by SDL on 2008-04-29
Hi all. I upgraded my PC to Hardy last night having previously used Gutsy and Feisty. I am experiencing a few problems that I was hoping somebody could help me with:
- wireless connection is not working
- proprietary nvidia driver is disabled
- my XP partition has to be mounted each time after I login (did I have to configure it do be automatically mounted in Gutsy or did it come as default?)

Regarding the wireless connection, I am using a BCM43xx wireless care. **I have no wired connection, so I'm writing this from XP**. When I installed Gutsy, it was really simple to configure as this screen appeared when I put the CD in:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67924&stc=1&d=1209555592[/IMG]

However, this doesn't happen in Hardy. Instead, I have followed the instructions in the 6th post of [this thread]("http://ubuntuforums.org/showthread.php?t=766800"). I don't think there was any significant errors following this but just in case, the output was:
```
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initialising package states... Done 
Building tag database... Done      
The following NEW packages will be installed: 
  b43-fwcutter 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/15.8kB of archives. After unpacking 102kB will be used. 
Writing extended state information... Done 
Preconfiguring packages ... 
Selecting previously deselected package b43-fwcutter. 
(Reading database ... 95678 files and directories currently installed.) 
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ... 
Setting up b43-fwcutter (1:011-1) ... 
--11:21:22--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o 
           => `wl_apsta-3.130.20.0.o' 
Resolving downloads.openwrt.org... failed: Name or service not known. 
dpkg: error processing b43-fwcutter (--configure): 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 b43-fwcutter 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install.  Trying to recover: 
Setting up b43-fwcutter (1:011-1) ... 
--11:21:23--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o 
           => `wl_apsta-3.130.20.0.o' 
Resolving downloads.openwrt.org... failed: Name or service not known. 
dpkg: error processing b43-fwcutter (--configure): 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 b43-fwcutter 
Reading package lists... Done             
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initialising package states... Done 
Writing extended state information... Done 
Building tag database... Done    
```

Now when I run ```
lshw -C network
``` the output is ```
*-network:0             
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 8 
       bus info: pci@0000:00:08.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8169 Gigabit Ethernet 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: c 
       bus info: pci@0000:00:0c.0 
       logical name: eth0 
       version: 10 
       serial: 00:01:6c:2d:1a:9f 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:11:f5:18:aa:b8 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
```

Here is the output of dmesg:
```
$ dmesg 
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable) 
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable) 
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
[    0.000000] 639MB HIGHMEM available. 
[    0.000000] 896MB LOWMEM available. 
[    0.000000] found SMP MP-table at 000f56c0 
[    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   229376 
[    0.000000]   HighMem    229376 ->   393200 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   393200 
[    0.000000] On node 0 totalpages: 393200 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 1760 pages used for memmap 
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 1279 pages used for memmap 
[    0.000000]   HighMem zone: 162545 pages, LIFO batch:31 
[    0.000000]   Movable zone: 0 pages used for memmap 
[    0.000000] DMI 2.2 present. 
[    0.000000] Intel MultiProcessor Specification v1.4 
[    0.000000]     Virtual Wire compatibility mode. 
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000 
[    0.000000] Processor #0 15:12 APIC version 17 
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Processors: 1 
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000) 
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390129 
[    0.000000] Kernel command line: root=UUID=aa30a4fa-81ff-45af-8a6e-d1ce58afaf9e ro quiet splash acpi=off 
[    0.000000] mapped APIC to ffffb000 (fee00000) 
[    0.000000] mapped IOAPIC to ffffa000 (fec00000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[    0.000000] Detected 1999.498 MHz processor. 
[   19.011443] Console: colour VGA+ 80x25 
[   19.011447] console [tty0] enabled 
[   19.012133] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[   19.012633] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   19.069621] Memory: 1546664k/1572800k available (2157k kernel code, 24908k reserved, 998k data, 364k init, 655296k highmem) 
[   19.069629] virtual kernel memory layout: 
[   19.069630]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) 
[   19.069631]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   19.069633]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB) 
[   19.069634]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB) 
[   19.069635]       .init : 0xc041b000 - 0xc0476000   ( 364 kB) 
[   19.069636]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB) 
[   19.069637]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB) 
[   19.069640] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   19.069688] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   19.149689] Calibrating delay using timer specific routine.. 4000.93 BogoMIPS (lpj=8001866) 
[   19.149723] Security Framework initialized 
[   19.149733] SELinux:  Disabled at boot. 
[   19.149754] AppArmor: AppArmor initialized 
[   19.149759] Failure registering capabilities with primary security module. 
[   19.149768] Mount-cache hash table entries: 512 
[   19.149914] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000 00000000 
[   19.149923] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   19.149925] CPU: L2 Cache: 512K (64 bytes/line) 
[   19.149928] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000 00000000 
[   19.149940] Compat vDSO mapped to ffffe000. 
[   19.149955] Checking 'hlt' instruction... OK. 
[   19.166027] SMP alternatives: switching to UP code 
[   19.167306] Freeing SMP alternatives: 11k freed 
[   19.167428] Early unpacking initramfs... done 
[   19.491616] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00 
[   19.491634] Total of 1 processors activated (4000.93 BogoMIPS). 
[   19.491674] ExtINT not setup in hardware but reported by MP table 
[   19.491725] ENABLING IO-APIC IRQs 
[   19.491895] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0 
[   19.745601] Brought up 1 CPUs 
[   19.745622] CPU0 attaching sched-domain: 
[   19.745625]  domain 0: span 01 
[   19.745626]   groups: 01 
[   19.745777] net_namespace: 64 bytes 
[   19.745782] Booting paravirtualized kernel on bare hardware 
[   19.746194] Time: 13:32:20  Date: 04/30/08 
[   19.746216] NET: Registered protocol family 16 
[   19.746366] EISA bus registered 
[   19.782162] PCI: PCI BIOS revision 2.10 entry at 0xfba50, last bus=1 
[   19.782164] PCI: Using configuration type 1 
[   19.782166] Setting up standard PCI resources 
[   19.785965] ACPI: Interpreter disabled. 
[   19.785968] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   19.785990] pnp: PnP ACPI: disabled 
[   19.785993] PnPBIOS: Scanning system for PnP BIOS support... 
[   19.786004] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc450 
[   19.786006] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc480, dseg 0xf0000 
[   19.786629] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver 
[   19.786795] PCI: Probing PCI hardware 
[   19.786800] PCI: Probing PCI hardware (bus 00) 
[   19.787902] PCI: Using IRQ router SIS [1039/0964] at 0000:00:02.0 
[   19.787910] PCI->APIC IRQ transform: 0000:00:02.7[C] -> IRQ 18 
[   19.787913] PCI->APIC IRQ transform: 0000:00:03.0[A] -> IRQ 20 
[   19.787916] PCI->APIC IRQ transform: 0000:00:03.1[B] -> IRQ 21 
[   19.787918] PCI->APIC IRQ transform: 0000:00:03.2[C] -> IRQ 22 
[   19.787921] PCI->APIC IRQ transform: 0000:00:03.3[D] -> IRQ 23 
[   19.787924] PCI->APIC IRQ transform: 0000:00:05.0[A] -> IRQ 17 
[   19.787926] PCI->APIC IRQ transform: 0000:00:08.0[A] -> IRQ 17 
[   19.787929] PCI->APIC IRQ transform: 0000:00:0c.0[A] -> IRQ 18 
[   19.787932] PCI->APIC IRQ transform: 0000:00:0d.0[A] -> IRQ 19 
[   19.787934] PCI->APIC IRQ transform: 0000:00:0e.0[A] -> IRQ 17 
[   19.787937] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16 
[   19.797613] NET: Registered protocol family 8 
[   19.797615] NET: Registered protocol family 20 
[   19.797674] AppArmor: AppArmor Filesystem Enabled 
[   19.797705] system 00:07: iomem range 0x0-0x9ffff could not be reserved 
[   19.797708] system 00:07: iomem range 0x20000000-0x203fffff could not be reserved 
[   19.797711] system 00:07: iomem range 0xffee0000-0xffefffff has been reserved 
[   19.797714] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved 
[   19.797717] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved 
[   19.797720] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved 
[   19.797722] system 00:07: iomem range 0x100000-0xffffff could not be reserved 
[   19.797728] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved 
[   19.797730] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved 
[   19.797733] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved 
[   19.797735] system 00:08: iomem range 0xfc000-0xfffff could not be reserved 
[   19.797741] system 00:0b: ioport range 0x1000-0x107f has been reserved 
[   19.797743] system 00:0b: ioport range 0x10e0-0x10ff has been reserved 
[   19.798037] PCI: Bridge: 0000:00:01.0 
[   19.798039]   IO window: disabled. 
[   19.798042]   MEM window: e4000000-e5ffffff 
[   19.798045]   PREFETCH window: d0000000-dfffffff 
[   19.798063] NET: Registered protocol family 2 
[   19.801551] Time: tsc clocksource has been installed. 
[   19.833629] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   19.833973] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[   19.835285] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[   19.835970] TCP: Hash tables configured (established 131072 bind 65536) 
[   19.835973] TCP reno registered 
[   19.845683] checking if image is initramfs... it is 
[   20.469812] Freeing initrd memory: 7702k freed 
[   20.470357] audit: initializing netlink socket (disabled) 
[   20.470372] audit(1209562340.296:1): initialized 
[   20.470522] highmem bounce pool size: 64 pages 
[   20.471935] VFS: Disk quotas dquot_6.5.1 
[   20.471996] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   20.472157] io scheduler noop registered 
[   20.472159] io scheduler anticipatory registered 
[   20.472161] io scheduler deadline registered 
[   20.472172] io scheduler cfq registered (default) 
[   20.545388] Boot video device is 0000:01:00.0 
[   20.545560] isapnp: Scanning for PnP cards... 
[   20.898825] isapnp: No Plug & Play device found 
[   20.921003] Real Time Clock Driver v1.12ac 
[   20.921064] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   20.921171] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.921278] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   20.921759] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.921995] 00:10: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   20.922578] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   20.922635] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   20.922711] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12 
[   20.922958] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   20.922963] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   20.925552] mice: PS/2 mouse device common for all mice 
[   20.925645] EISA: Probing bus 0 at eisa.0 
[   20.925651] Cannot allocate resource for EISA slot 1 
[   20.925659] Cannot allocate resource for EISA slot 4 
[   20.925673] EISA: Detected 0 cards. 
[   20.925676] cpuidle: using governor ladder 
[   20.925678] cpuidle: using governor menu 
[   20.925765] NET: Registered protocol family 1 
[   20.925788] Using IPI No-Shortcut mode 
[   20.925822] registered taskstats version 1 
[   20.925903]   Magic number: 4:99:535 
[   20.926059] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   20.926061] EDD information not available. 
[   20.926432] Freeing unused kernel memory: 364k freed 
[   20.953300] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   22.171380] fuse init (API version 7.9) 
[   22.209555] thermal: Unknown symbol acpi_processor_set_thermal_limit 
[   22.449158] SCSI subsystem initialized 
[   22.505485] libata version 3.00 loaded. 
[   22.520975] usbcore: registered new interface driver usbfs 
[   22.520997] usbcore: registered new interface driver hub 
[   22.544942] usbcore: registered new device driver usb 
[   22.552969] ssb: Sonics Silicon Backplane found on PCI device 0000:00:08.0 
[   22.568993] r8169 Gigabit Ethernet driver 2.2LK loaded 
[   22.569224] eth0: RTL8110s at 0xf882a000, 00:01:6c:2d:1a:9f, XID 04000000 IRQ 18 
[   22.581655] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   22.581713] ohci_hcd 0000:00:03.0: OHCI Host Controller 
[   22.581953] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1 
[   22.581969] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe6083000 
[   22.639007] usb usb1: configuration #1 chosen from 1 choice 
[   22.639030] hub 1-0:1.0: USB hub found 
[   22.639039] hub 1-0:1.0: 3 ports detected 
[   22.741677] ohci_hcd 0000:00:03.1: OHCI Host Controller 
[   22.741710] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2 
[   22.741725] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe6085000 
[   22.798983] usb usb2: configuration #1 chosen from 1 choice 
[   22.799007] hub 2-0:1.0: USB hub found 
[   22.799016] hub 2-0:1.0: 3 ports detected 
[   22.832537] FDC 0 is a post-1991 82077 
[   22.901652] ohci_hcd 0000:00:03.2: OHCI Host Controller 
[   22.901680] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3 
[   22.901696] ohci_hcd 0000:00:03.2: irq 22, io mem 0xe6088000 
[   22.958937] usb usb3: configuration #1 chosen from 1 choice 
[   22.958962] hub 3-0:1.0: USB hub found 
[   22.958973] hub 3-0:1.0: 2 ports detected 
[   23.044800] usb 1-2: new low speed USB device using ohci_hcd and address 2 
[   23.061719] ehci_hcd 0000:00:03.3: EHCI Host Controller 
[   23.061747] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4 
[   23.061787] PCI: cache line size of 64 is not supported by device 0000:00:03.3 
[   23.061797] ehci_hcd 0000:00:03.3: irq 23, io mem 0xe6082000 
[   23.232749] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   23.232874] usb usb4: configuration #1 chosen from 1 choice 
[   23.232896] hub 4-0:1.0: USB hub found 
[   23.232903] hub 4-0:1.0: 8 ports detected 
[   23.338508] pata_sis 0000:00:02.5: version 0.5.2 
[   23.344760] scsi0 : pata_sis 
[   23.348330] scsi1 : pata_sis 
[   23.348373] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14 
[   23.348376] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15 
[   23.628640] usb 1-2: device not accepting address 2, error -62 
[   23.672910] ata1.00: ATAPI: _NEC DVD_RW ND-2510A, 2.15, max UDMA/33 
[   23.674196] ata1.01: ATA-6: WDC WD1200JB-00GVC0, 08.02D08, max UDMA/100 
[   23.674199] ata1.01: 234441648 sectors, multi 16: LBA48 
[   23.674211] ata1.01: limited to UDMA/33 due to 40-wire cable 
[   23.844874] ata1.00: configured for UDMA/33 
[   23.862069] ata1.01: configured for UDMA/33 
[   24.017560] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-2510A  2.15 PQ: 0 ANSI: 5 
[   24.017915] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5 
[   24.019228] sata_sil 0000:00:0e.0: version 2.3 
[   24.021948] scsi2 : sata_sil 
[   24.022418] scsi3 : sata_sil 
[   24.022442] ata3: SATA max UDMA/100 mmio m512@0xe6087000 tf 0xe6087080 irq 17 
[   24.022446] ata4: SATA max UDMA/100 mmio m512@0xe6087000 tf 0xe60870c0 irq 17 
[   24.031785] Driver 'sd' needs updating - please use bus_type methods 
[   24.033186] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB) 
[   24.033199] sd 0:0:1:0: [sda] Write Protect is off 
[   24.033202] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   24.033215] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   24.033257] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB) 
[   24.033265] sd 0:0:1:0: [sda] Write Protect is off 
[   24.033267] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   24.033278] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   24.033281]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   24.049336]  sda1 sda3 < sda5 sda6 > 
[   24.066529] sd 0:0:1:0: [sda] Attached SCSI disk 
[   24.072694] sr 0:0:0:0: Attached scsi generic sg0 type 5 
[   24.072712] sd 0:0:1:0: Attached scsi generic sg1 type 0 
[   24.073048] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray 
[   24.073052] Uniform CD-ROM driver Revision: 3.20 
[   24.073088] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[   24.332507] ata3: SATA link down (SStatus 0 SControl 310) 
[   24.365725] Attempting manual resume 
[   24.365729] swsusp: Resume From Partition 8:5 
[   24.365731] PM: Checking swsusp image. 
[   24.365972] PM: Resume from disk failed. 
[   24.400168] kjournald starting.  Commit interval 5 seconds 
[   24.400182] EXT3-fs: mounted filesystem with ordered data mode. 
[   24.644403] ata4: SATA link down (SStatus 0 SControl 310) 
[   24.697332] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e6086000-e60867ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[   24.703281] sata_sis 0000:00:05.0: version 1.0 
[   24.703291] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode 
[   24.703361] scsi4 : sata_sis 
[   24.703400] scsi5 : sata_sis 
[   24.703425] ata5: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 17 
[   24.703429] ata6: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 17 
[   25.004319] usb 3-1: new low speed USB device using ohci_hcd and address 2 
[   25.012320] ata5: SATA link down (SStatus 0 SControl 300) 
[   25.207015] usb 3-1: configuration #1 chosen from 1 choice 
[   25.332249] ata6: SATA link down (SStatus 0 SControl 300) 
[   25.524187] usb 1-2: new low speed USB device using ohci_hcd and address 4 
[   25.738695] usb 1-2: configuration #1 chosen from 1 choice 
[   25.980187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c20000623bb] 
[   26.052064] usb 2-3: new full speed USB device using ohci_hcd and address 2 
[   30.967107] Linux agpgart interface v0.102 
[   31.017786] agpgart: Detected AGP bridge 0 
[   31.020290] agpgart: AGP aperture is 64M @ 0xe0000000 
[   31.071698] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   31.135238] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   31.230998] usb 2-3: device descriptor read/64, error -62 
[   32.722652] intel8x0_measure_ac97_clock: measured 54902 usecs 
[   32.722657] intel8x0: clocking to 48000 
[   32.746545] b43-phy0: Broadcom 4306 WLAN found 
[   32.835520] phy0: Selected rate control algorithm 'simple' 
[   32.887371] input: PC Speaker as /devices/platform/pcspkr/input/input2 
[   32.978461] logips2pp: Detected unknown logitech mouse model 89 
[   33.450529] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input3 
[   33.481811] parport_pc 00:0e: reported by Plug and Play BIOS 
[   33.481859] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   36.513918] usb 2-3: device descriptor read/64, error -62 
[   36.793850] usb 2-3: new full speed USB device using ohci_hcd and address 3 
[   41.973192] usb 2-3: device descriptor read/64, error -62 
[   47.256507] usb 2-3: device descriptor read/64, error -62 
[   47.536440] usb 2-3: new full speed USB device using ohci_hcd and address 4 
[   52.556588] usb 2-3: device descriptor read/8, error -110 
[   52.683535] usb 2-3: device descriptor read/8, error -62 
[   52.959724] usb 2-3: new full speed USB device using ohci_hcd and address 5 
[   57.979908] usb 2-3: device descriptor read/8, error -110 
[   58.106856] usb 2-3: device descriptor read/8, error -62 
[   58.207088] usbcore: registered new interface driver hiddev 
[   58.218908] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input4 
[   58.227097] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input5 
[   58.243080] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input6 
[   58.255080] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input7 
[   58.267063] input,hidraw0: USB HID v1.00 Joystick [Dual PSX-USB Adaptor  Dual PSX-USB Adaptor ] on usb-0000:00:03.2-1 
[   58.278800] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input8 
[   58.287103] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input9 
[   58.303069] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input10 
[   58.315081] input: Dual PSX-USB Adaptor  Dual PSX-USB Adaptor  as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input11 
[   58.327054] input,hidraw1: USB HID v1.00 Joystick [Dual PSX-USB Adaptor  Dual PSX-USB Adaptor ] on usb-0000:00:03.0-2 
[   58.327072] usbcore: registered new interface driver usbhid 
[   58.327076] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver 
[   59.421442] lp0: using parport0 (interrupt-driven). 
[   59.499172] Adding 1156640k swap on /dev/sda5.  Priority:-1 extents:1 across:1156640k 
[   60.037622] EXT3 FS on sda6, internal journal 
[   61.093534] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   61.612602] powernow_k8: Unknown symbol acpi_processor_notify_smm 
[   61.612645] powernow_k8: Unknown symbol acpi_processor_unregister_performance 
[   61.612723] powernow_k8: Unknown symbol acpi_processor_register_performance 
[   61.648205] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm 
[   61.648251] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance 
[   61.648381] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance 
[   61.648443] acpi_cpufreq: Unknown symbol acpi_processor_register_performance 
[   62.367193] apm: BIOS not found. 
[   62.480382] ppdev: user-space parallel port driver 
[   62.544613] audit(1209558783.205:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4616 profile="/usr/sbin/cupsd" namespace="default" 
[   63.350368] r8169: eth0: link down 
[   63.441889] Bluetooth: Core ver 2.11 
[   63.442730] NET: Registered protocol family 31 
[   63.442733] Bluetooth: HCI device and connection manager initialized 
[   63.442737] Bluetooth: HCI socket layer initialized 
[   63.479472] input: b43-phy0 as /devices/virtual/input/input12 
[   63.489835] Bluetooth: L2CAP ver 2.9 
[   63.489840] Bluetooth: L2CAP socket layer initialized 
[   63.577788] Bluetooth: RFCOMM socket layer initialized 
[   63.578385] Bluetooth: RFCOMM TTY layer initialized 
[   63.578388] Bluetooth: RFCOMM ver 1.8 
[   63.607714] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   63.607722] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4). 
[   63.693749] usb 2-3: new full speed USB device using ohci_hcd and address 6 
[   67.445549] input: b43-phy0 as /devices/virtual/input/input13 
[   67.531340] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   67.531348] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4). 
[   68.872992] usb 2-3: device descriptor read/64, error -62 
[   71.470987] NET: Registered protocol family 10 
[   71.471716] lo: Disabled Privacy Extensions 
[   71.472487] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   74.156059] usb 2-3: device descriptor read/64, error -62 
[   74.435977] usb 2-3: new full speed USB device using ohci_hcd and address 7 
[   79.614985] usb 2-3: device descriptor read/64, error -62 
[   84.898084] usb 2-3: device descriptor read/64, error -62 
[   85.178014] usb 2-3: new full speed USB device using ohci_hcd and address 8 
[   85.778208] input: b43-phy0 as /devices/virtual/input/input14 
[   85.868060] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   85.868068] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4). 
[   90.197674] usb 2-3: device descriptor read/8, error -110 
[   90.324611] usb 2-3: device descriptor read/8, error -62 
[   90.601292] usb 2-3: new full speed USB device using ohci_hcd and address 9 
[   95.621004] usb 2-3: device descriptor read/8, error -110 
[   95.747943] usb 2-3: device descriptor read/8, error -62 
[  104.087595] input: b43-phy0 as /devices/virtual/input/input15 
[  104.172784] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[  104.172792] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4). 
[  122.391244] input: b43-phy0 as /devices/virtual/input/input16 
[  122.480369] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[  122.480377] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4). 
[  140.714234] input: b43-phy0 as /devices/virtual/input/input17
```
I visited the linuxwireless site as recommended but that stuff was a bit over my head!


I am aware that some people are using ndiswrapper but I'm not really keen on this approach if I can get away without it. As far as I can see, if it worked in Gutsy, it must surely be able to work OK here!


Regarding the nvidia driver:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67926&stc=1&d=1209556025[/IMG]
If I press enable, it prompts me to restart but it still says 'not in use' following that.

I should point out that although it says my wireless driver is enabled in that screenshot, that was only following the advice of the post that I mentioned and I still don't have a wireless connection.

Thanks for any ideas,

Stephen.

---

### Post by phr0ze on 2008-04-29
My video card says not in use as well, but the effects are working. Strange.

---

### Post by SDL on 2008-04-29
OK. I don't normally enable the effects, so I'll do that and see what happens. My main problem is the whole wireless situation though... it's such a pain to have to restart my computer, boot into xp, find a potential solution, restart and attempt to fix Hardy each time!

---

### Post by Sef on 2008-04-29
What type of NVidia card do you have?

---

### Post by spiderbatdad on 2008-04-29
Regarding the wireless (btw...its hard to deal with multiple issues in a single thread :)) the fwcutter driver leaves much to be desired. I have heard it is faulty and slow. Most users of the wireless card you have prefer to set it up with ndiswrapper. There are several good how-tos in this forum for doing that. I can try to point you to one, if you can't find one.

---

### Post by SDL on 2008-04-29
Hi. Thank you both for your replies.

Sef, I have a GeForce FX5700.

spiderbatdad, I was trying to avoid ndiswrapper but maybe you're right and I'll have to go for it. Don't worry about linking me one, I've found a few, I just can't see why Hardy appears to have taken a backwards step in compatibility with this issue. Oh well, Plan B is to reinstall Gutsy...

Good point about the multiple issues, sorry about that, I figured maybe since they were both to do with the restricted drivers that the issues maybe somehow related but I was probably wrong! ;)

---

### Post by SDL on 2008-04-29
Hello again. Just want to say that my bcm43xx is now working. I followed instructions found in [this thread]("http://ubuntuforums.org/showthread.php?t=767372&highlight=wl_apsta.o") to install the drivers without ndiswrapper which is excellent. That should make sorting out the nvidia drivers much easier!

Edit: The nvidia drivers are now working System->Administration->Hardware Drivers worked well once I had internet connection!

---

