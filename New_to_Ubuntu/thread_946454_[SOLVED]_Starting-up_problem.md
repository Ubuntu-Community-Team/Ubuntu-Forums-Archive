---
title: "[SOLVED] Starting-up problem"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Dacker on 2008-10-13
i was working on the shell but i didn't login in GUI session, after half an hour i tried to to login in but the thing has stuck and the screen becomes fully white, therefore i rebooted and register for fali GUI session and it's working fine. so please how could i solve this problem ??? :confused:

thanks in advance....

---

### Post by jerome1232 on 2008-10-13
Since this sounds like a xorg misconfiguration issue it would be helpful to know what video card you are using and what driver you are using for it. How did you install the driver (restricted driver manager? envy? other?)

If you could post the output of 'cat /etc/X11/xorg.conf' it may prove useful as well.

---

### Post by Dacker on 2008-10-13
i don't know how the catting of this file will benefit you but any way here is the output:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

thank you.....

---

### Post by Nxion on 2008-10-13
> **Dacker said:**
> i don't know how the catting of this file will benefit you but any way here is the output:
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

```thank you.....

I don't see a driver defined in the file. By chance are you using [WUBI]("http://wubi-installer.org/") to use Ubuntu? Or do you have it on a separate partition?

---

### Post by Dacker on 2008-10-13
neither Wubi nor separate partition.

Actually i installed ubuntu on the entire drive .......:lolflag:

---

### Post by Dacker on 2008-10-13
Is there anybody can solve it ????

---

### Post by Nxion on 2008-10-13
> **Dacker said:**
> Is there anybody can solve it ????

We will get it fixed, don't worry.


OK, post the output of this command please:

```
lspci
```

AND...

```
sudo dmesg -tail
```

---

### Post by Dacker on 2008-10-14
here is the output :

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:03.0 Modem: Smart Link Ltd. Unknown device 2800 (rev 02)
01:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

```

the other command (sudo dmesg -tail) the tail option wouldn't be work therefore i post the output of ( sudo dmesg) which seems complicated :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000004ffb0000 - 000000004ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004ffbe000 - 000000004fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff0000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 327600) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327600
[    0.000000] On node 0 totalpages: 327600
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97457 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAF80 checksum 0
[    0.000000] ACPI: RSDP 000FAF80, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 4FFB0000, 0034 (r1 A M I  OEMRSDT   3000603 MSFT       97)
[    0.000000] ACPI: FACP 4FFB0200, 0081 (r1 A M I  OEMFACP   3000603 MSFT       97)
[    0.000000] ACPI: DSDT 4FFB0400, 67DF (r1  A0404 A0404001        1 INTL  2002026)
[    0.000000] ACPI: FACS 4FFBE000, 0040
[    0.000000] ACPI: APIC 4FFB0390, 0070 (r1 A M I  OEMAPIC   3000603 MSFT       97)
[    0.000000] ACPI: OEMB 4FFBE040, 0066 (r1 A M I  AMI_OEM   3000603 MSFT       97)
[    0.000000] ACPI: MCFG 4FFB6BE0, 003C (r1 A M I  OEMMCFG   3000603 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:afb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 325041
[    0.000000] Kernel command line: root=UUID=7c383588-f0bb-418b-9073-df5b1516ef26 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3010.756 MHz processor.
[   18.854254] Console: colour VGA+ 80x25
[   18.854258] console [tty0] enabled
[   18.854806] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.855273] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.903913] Memory: 1286680k/1310400k available (2177k kernel code, 22540k reserved, 1006k data, 368k init, 392896k highmem)
[   18.903924] virtual kernel memory layout:
[   18.903925]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   18.903926]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.903927]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.903927]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.903928]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   18.903929]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   18.903930]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   18.903933] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.903987] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.983987] Calibrating delay using timer specific routine.. 6027.12 BogoMIPS (lpj=12054259)
[   18.984016] Security Framework initialized
[   18.984024] SELinux:  Disabled at boot.
[   18.984039] AppArmor: AppArmor initialized
[   18.984043] Failure registering capabilities with primary security module.
[   18.984052] Mount-cache hash table entries: 512
[   18.984190] Initializing cgroup subsys ns
[   18.984195] Initializing cgroup subsys cpuacct
[   18.984210] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000641d 00000000 00000001 00000000
[   18.984219] monitor/mwait feature present.
[   18.984222] using mwait in idle threads.
[   18.984228] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.984231] CPU: L2 cache: 1024K
[   18.984233] CPU: Physical Processor ID: 0
[   18.984236] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000641d 00000000 00000001 00000000
[   18.984247] Compat vDSO mapped to ffffe000.
[   18.984264] Checking 'hlt' instruction... OK.
[   19.000452] SMP alternatives: switching to UP code
[   19.002374] Early unpacking initramfs... done
[   19.296117] ACPI: Core revision 20070126
[   19.296182] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.309956] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   19.309977] SMP alternatives: switching to SMP code
[   19.310787] Booting processor 1/1 eip 3000
[   19.320902] Initializing CPU#1
[   19.399855] Calibrating delay using timer specific routine.. 6021.78 BogoMIPS (lpj=12043577)
[   19.399866] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000641d 00000000 00000001 00000000
[   19.399874] monitor/mwait feature present.
[   19.399881] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   19.399883] CPU: L2 cache: 1024K
[   19.399886] CPU: Physical Processor ID: 0
[   19.399888] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000641d 00000000 00000001 00000000
[   19.400266] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   19.400308] Total of 2 processors activated (12048.91 BogoMIPS).
[   19.400437] ENABLING IO-APIC IRQs
[   19.400617] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.547961] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.567971] Brought up 2 CPUs
[   19.568001] CPU0 attaching sched-domain:
[   19.568004]  domain 0: span 03
[   19.568007]   groups: 01 02
[   19.568010]   domain 1: span 03
[   19.568012]    groups: 03
[   19.568015] CPU1 attaching sched-domain:
[   19.568016]  domain 0: span 03
[   19.568018]   groups: 02 01
[   19.568021]   domain 1: span 03
[   19.568023]    groups: 03
[   19.568303] net_namespace: 64 bytes
[   19.568314] Booting paravirtualized kernel on bare hardware
[   19.568874] Time:  7:00:09  Date: 10/14/08
[   19.568900] NET: Registered protocol family 16
[   19.569172] EISA bus registered
[   19.569178] ACPI: bus type pci registered
[   19.569526] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   19.569529] PCI: Using configuration type 1
[   19.569546] Setting up standard PCI resources
[   19.584382] ACPI: EC: Look up EC in DSDT
[   19.592703] ACPI: Interpreter enabled
[   19.592707] ACPI: (supports S0 S1 S3 S4 S5)
[   19.592727] ACPI: Using IOAPIC for interrupt routing
[   19.601030] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.601585] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   19.601589] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.602251] PCI: Transparent bridge - 0000:00:1e.0
[   19.602279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.602450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   19.605025] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   19.605152] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.605275] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   19.605399] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.605523] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.605646] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.605779] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.605904] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.606063] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  C9, should be BC [20070126]
[   19.606072] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.606114] pnp: PnP ACPI init
[   19.606124] ACPI: bus type pnp registered
[   19.611149] pnp: PnP ACPI: found 17 devices
[   19.611152] ACPI: ACPI bus type pnp unregistered
[   19.611157] PnPBIOS: Disabled by ACPI PNP
[   19.611473] PCI: Using ACPI for IRQ routing
[   19.611478] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.636016] NET: Registered protocol family 8
[   19.636019] NET: Registered protocol family 20
[   19.636101] AppArmor: AppArmor Filesystem Enabled
[   19.639868] Time: tsc clocksource has been installed.
[   19.652115] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   19.652127] system 00:08: ioport range 0x290-0x297 has been reserved
[   19.652133] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   19.652136] system 00:09: ioport range 0x800-0x87f has been reserved
[   19.652139] system 00:09: ioport range 0x480-0x4bf has been reserved
[   19.652142] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   19.652145] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   19.652152] system 00:0b: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   19.652158] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   19.652161] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   19.652168] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   19.652174] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[   19.652181] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[   19.652184] system 00:10: iomem range 0xc0000-0xdffff could not be reserved
[   19.652186] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[   19.652189] system 00:10: iomem range 0x100000-0x4fffffff could not be reserved
[   19.652192] system 00:10: iomem range 0x0-0x0 could not be reserved
[   19.682728] PCI: Bridge: 0000:00:1c.0
[   19.682732]   IO window: e000-efff
[   19.682737]   MEM window: dff00000-dfffffff
[   19.682741]   PREFETCH window: c0000000-deffffff
[   19.682747] PCI: Bridge: 0000:00:1e.0
[   19.682750]   IO window: d000-dfff
[   19.682754]   MEM window: dfe00000-dfefffff
[   19.682758]   PREFETCH window: bf000000-bfffffff
[   19.682787] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.682794] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.682805] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.682817] NET: Registered protocol family 2
[   19.720284] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.720616] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.721302] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.721880] TCP: Hash tables configured (established 131072 bind 65536)
[   19.721883] TCP reno registered
[   19.732439] checking if image is initramfs... it is
[   20.183968] Switched to high resolution mode on CPU 0
[   20.184105] Switched to high resolution mode on CPU 1
[   20.312780] Freeing initrd memory: 7318k freed
[   20.313756] audit: initializing netlink socket (disabled)
[   20.313774] audit(1223967609.280:1): initialized
[   20.314004] highmem bounce pool size: 64 pages
[   20.316451] VFS: Disk quotas dquot_6.5.1
[   20.316552] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.316710] io scheduler noop registered
[   20.316712] io scheduler anticipatory registered
[   20.316714] io scheduler deadline registered
[   20.316726] io scheduler cfq registered (default)
[   20.316817] Boot video device is 0000:02:00.0
[   20.316949] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.316993] assign_interrupt_mode Found MSI capability
[   20.317032] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.317078] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.317394] isapnp: Scanning for PnP cards...
[   20.668950] isapnp: No Plug & Play device found
[   20.706085] Real Time Clock Driver v1.12ac
[   20.706211] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.706341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.707213] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.707371] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   20.707379] ACPI: PCI interrupt for device 0000:01:03.0 disabled
[   20.708243] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.708324] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.708527] PNP: No PS/2 controller found. Probing ports directly.
[   20.711002] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.711009] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.731576] mice: PS/2 mouse device common for all mice
[   20.731739] EISA: Probing bus 0 at eisa.0
[   20.731769] EISA: Detected 0 cards.
[   20.731773] cpuidle: using governor ladder
[   20.731775] cpuidle: using governor menu
[   20.731861] NET: Registered protocol family 1
[   20.731891] Using IPI No-Shortcut mode
[   20.731923] registered taskstats version 1
[   20.732019]   Magic number: 12:776:15
[   20.732030]   hash matches device ttycc
[   20.732149] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.732151] EDD information not available.
[   20.732441] Freeing unused kernel memory: 368k freed
[   21.976043] fuse init (API version 7.9)
[   21.999234] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.191974] usbcore: registered new interface driver usbfs
[   22.192011] usbcore: registered new interface driver hub
[   22.193340] usbcore: registered new device driver usb
[   22.207950] USB Universal Host Controller Interface driver v3.0
[   22.208033] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   22.208047] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.208052] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.208352] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.208385] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000b880
[   22.208591] usb usb1: configuration #1 chosen from 1 choice
[   22.208633] hub 1-0:1.0: USB hub found
[   22.208642] hub 1-0:1.0: 2 ports detected
[   22.311962] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   22.311979] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.311985] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.312022] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.312056] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bc00
[   22.312232] usb usb2: configuration #1 chosen from 1 choice
[   22.312271] hub 2-0:1.0: USB hub found
[   22.312280] hub 2-0:1.0: 2 ports detected
[   22.415928] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   22.415947] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.415953] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.415990] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.416026] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000c000
[   22.416222] usb usb3: configuration #1 chosen from 1 choice
[   22.416261] hub 3-0:1.0: USB hub found
[   22.416270] hub 3-0:1.0: 2 ports detected
[   22.452104] SCSI subsystem initialized
[   22.483785] libata version 3.00 loaded.
[   22.519922] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   22.519939] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.519944] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.519984] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.520018] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c080
[   22.520190] usb usb4: configuration #1 chosen from 1 choice
[   22.520231] hub 4-0:1.0: USB hub found
[   22.520241] hub 4-0:1.0: 2 ports detected
[   22.551769] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   22.623870] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   22.623935] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.623953] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   22.623995] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   22.624028] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.624043] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   22.629250] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   22.629265] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.629270] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.629313] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.633232] ehci_hcd 0000:00:1d.7: debug port 1
[   22.633240] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.633250] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xdfdffc00
[   22.653554] 8139too Fast Ethernet driver 0.9.28
[   22.678691] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.678870] usb usb5: configuration #1 chosen from 1 choice
[   22.678909] hub 5-0:1.0: USB hub found
[   22.678919] hub 5-0:1.0: 8 ports detected
[   22.753379] Floppy drive(s): fd0 is 1.44M
[   22.771409] FDC 0 is a post-1991 82077
[   22.782839] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 21
[   22.783755] eth0: RealTek RTL8139 at 0xd400, 00:17:31:28:94:54, IRQ 21
[   22.783760] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   22.797041] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.831740] ata_piix 0000:00:1f.1: version 2.12
[   22.831772] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   22.831836] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.836477] scsi0 : ata_piix
[   22.836887] scsi1 : ata_piix
[   22.838869] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   22.838874] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   23.083528] usb 1-1: device not accepting address 2, error -71
[   23.506695] ata1.00: ATAPI: HL-DT-ST GCE-8527B, 1.01, max UDMA/33
[   23.506723] ata1.01: ATAPI: LITE-ON DVDRW SHW-1635S, YS0Q, max UDMA/66
[   23.695562] ata1.00: configured for UDMA/33
[   23.875226] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   23.883506] ata1.01: configured for UDMA/66
[   24.048676] scsi 0:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8527B  1.01 PQ: 0 ANSI: 5
[   24.049605] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YS0Q PQ: 0 ANSI: 5
[   24.049696] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   24.049724] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   24.049778] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.049897] scsi2 : ata_piix
[   24.051166] scsi3 : ata_piix
[   24.051218] ata3: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
[   24.051222] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
[   24.056945] usb 1-1: configuration #1 chosen from 1 choice
[   24.298055] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   24.379336] ata4.00: ATA-7: SAMSUNG HD160JJ, ZM100-41, max UDMA7
[   24.379341] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.419332] ata4.00: configured for UDMA/133
[   24.419485] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   24.433365] Driver 'sd' needs updating - please use bus_type methods
[   24.433509] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.433530] sd 3:0:0:0: [sda] Write Protect is off
[   24.433534] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.435965] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.436064] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.436083] sd 3:0:0:0: [sda] Write Protect is off
[   24.436088] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.436116] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.436122]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.441254] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   24.441260] Uniform CD-ROM driver Revision: 3.20
[   24.441330] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.446604]  sda1 sda2 <sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   24.447402] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   24.469506]  sda5 >
[   24.469640] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.477916] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.477950] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.478007] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   24.479831] usb 1-2: configuration #1 chosen from 1 choice
[   24.482826] usbcore: registered new interface driver hiddev
[   24.497052] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   24.518077] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1
[   24.531429] input: Genius NetScroll + Mini Traveler as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   24.551047] input,hidraw1: USB HID v1.10 Mouse [Genius NetScroll + Mini Traveler] on usb-0000:00:1d.0-2
[   24.551080] usbcore: registered new interface driver usbhid
[   24.551087] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.704875] Attempting manual resume
[   24.704880] swsusp: Resume From Partition 8:5
[   24.704882] PM: Checking swsusp image.
[   24.705090] PM: Resume from disk failed.
[   24.752650] kjournald starting.  Commit interval 5 seconds
[   24.752658] EXT3-fs: mounted filesystem with ordered data mode.
[   31.398969] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   31.760276] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.820359] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.960091] intel_rng: FWH not detected
[   32.020150] Linux agpgart interface v0.102
[   32.396047] parport_pc 00:07: reported by Plug and Play ACPI
[   32.396166] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   32.523203] iTCO_vendor_support: vendor-support=0
[   32.550870] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.551004] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   32.551047] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.633498] input: Power Button (FF) as /devices/virtual/input/input4
[   32.650784] ACPI: Power Button (FF) [PWRF]
[   32.650950] input: Power Button (CM) as /devices/virtual/input/input5
[   32.666770] ACPI: Power Button (CM) [PWRB]
[   33.787100] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.787132] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.149428] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
[   36.292983] lp0: using parport0 (interrupt-driven).
[   36.357122] Adding 3791300k swap on /dev/sda5.  Priority:-1 extents:1 across:3791300k
[   36.929178] EXT3 FS on sda1, internal journal
[   38.169531] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.669215] No dock devices found.
[   39.782586] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   39.782593] apm: disabled - APM is not SMP safe.
[   40.029421] ppdev: user-space parallel port driver
[   40.164536] audit(1223967629.989:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5034 profile="/usr/sbin/cupsd" namespace="default"
[   41.657046] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   41.752302] Bluetooth: Core ver 2.11
[   41.752787] NET: Registered protocol family 31
[   41.752793] Bluetooth: HCI device and connection manager initialized
[   41.752799] Bluetooth: HCI socket layer initialized
[   41.771321] Bluetooth: L2CAP ver 2.9
[   41.771329] Bluetooth: L2CAP socket layer initialized
[   41.838712] Bluetooth: RFCOMM socket layer initialized
[   41.838730] Bluetooth: RFCOMM TTY layer initialized
[   41.838733] Bluetooth: RFCOMM ver 1.8
[   43.669405] [drm] Initialized drm 1.1.0 20060810
[   44.863394] NET: Registered protocol family 17
[   47.481593] NET: Registered protocol family 10
[   47.482019] lo: Disabled Privacy Extensions
[   57.912999] eth0: no IPv6 routers present
```
```

```

---

### Post by Ryadt on 2008-10-14
Try to boot in recovery mode and do ```
xfix
```

---

### Post by Dacker on 2008-10-14
i inputed that command but noting has occurred, and the problem still roaming around even i tried to reboot several times...

is it because of the VGA's failure?

---

### Post by Nxion on 2008-10-14
> **Dacker said:**
> i inputed that command but noting has occurred, and the problem still roaming around even i tried to reboot several times...

is it because of the VGA's failure?

Looks like you have a ATI X1300 video card. I have that on my workstation at work, and it can be tricky, OK I want to see one more thing then we can go over howw to reload the video drivers. Can you post the output of this please?

```
sudo dmesg | grep ati
```

Thanks,
Nx

---

### Post by Dacker on 2008-10-14
```
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:afb80000)
[   17.643634] Calibrating delay using timer specific routine.. 6027.26 BogoMIPS (lpj=12054538)
[   17.660098] SMP alternatives: switching to UP code
[   17.969308] SMP alternatives: switching to SMP code
[   18.059501] Calibrating delay using timer specific routine.. 6021.71 BogoMIPS (lpj=12043428)
[   18.207607] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   18.229172] PCI: Using configuration type 1
[   19.368067] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.395773] EDD information not available.
[   20.852247] usb usb1: configuration #1 chosen from 1 choice
[   20.955862] usb usb2: configuration #1 chosen from 1 choice
[   21.059798] usb usb3: configuration #1 chosen from 1 choice
[   21.163745] usb usb4: configuration #1 chosen from 1 choice
[   21.323479] usb usb5: configuration #1 chosen from 1 choice
[   22.702593] usb 1-1: configuration #1 chosen from 1 choice
[   23.117420] Driver 'sd' needs updating - please use bus_type methods
[   23.117779]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   23.126449] usb 1-2: configuration #1 chosen from 1 choice
[   38.811388] audit(1223970400.965:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5035 profile="/usr/sbin/cupsd" namespace="default"
```

i really appreciate your effort......

---

### Post by Nxion on 2008-10-14
Give this a try:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This should get you going. If it doesn't, let us know so we can see why it is not working.

Regards,
Nxion

---

### Post by Dacker on 2008-10-14
solved ..............

appreciate your effort :)

---

### Post by Nxion on 2008-10-14
> **Dacker said:**
> solved ..............

appreciate your effort :)

No worries :) Glad I could help. 

I assume the guide worked for you? Or did you get it working a different way?

Nxion

---

### Post by Dacker on 2008-10-14
the guide that you gave it to me was efficient and worked appropriately.

once again,thanks............

---

### Post by Nxion on 2008-10-14
> **Dacker said:**
> the guide that you gave it to me was efficient and worked appropriately.

once again,thanks............


Your Welcome :)

---

