---
title: "Vista Dual Boot - getting Ubuntu to connect to internet"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by qprfact on 2008-06-27
My wife's laptop has Vista Basic pre-installed. I've made it into dual boot with Ubuntu Hardy Heron and it works fine.

However, I can't currently get it to connect to the internet. When I look at the network details it has IP address as 0.0.0.0, so I somehow need to change that to the correct IP address - how do I do that?

Thanks!

---

### Post by Canis familiaris on 2008-06-27
Are you trying to use a wired or a wireless connection?

---

### Post by qprfact on 2008-06-27
I can use either. Last night it was wired as I was sat near the router!

---

### Post by superprash2003 on 2008-06-27
go to system->administration->network and go to the ethernet properties and set it to DHCP..also go to the terminal and type ifconfig and post output here

---

### Post by qprfact on 2008-06-27
This is what I get for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:2d:ea:b2  
          inet6 addr: fe80::21e:ecff:fe2d:eab2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2086 (2.0 KB)  TX bytes:6122 (5.9 KB)
          Interrupt:21 Base address:0x1000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:ec:2d:ea:b2  
          inet addr:169.254.9.160  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75692 (73.9 KB)  TX bytes:75692 (73.9 KB)

---

### Post by Pjotr123 on 2008-06-27
It could be this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)
(number 2 )

---

### Post by superprash2003 on 2008-06-27
hmm.. what is the ip address of your router?? you could try setting up a static ip.. maybe dhcp isnt enabled in your router.

---

### Post by qprfact on 2008-07-10
OK. am getting somewhere now I think! Wired connection now works (using it now, in fact). However, wireless is a different kettle of fish. I tried the approach suggested in the article referred to, namely installing libstdc++5 and then ndisgtk.

Problem is, I'm dual booting with Vista, so I have no idea what .inf file I need to look for, nor where it is. Although I can bring up the Wireless Connections dialog box, I don't know what to put in it!

I'm probably missing something very basic here - can anyone help please? If it helps, here is ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:2d:ea:b2  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe2d:eab2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3749192 (3.5 MB)  TX bytes:332908 (325.1 KB)
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74000 (72.2 KB)  TX bytes:74000 (72.2 KB)
```

and this is dmesg.txt:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f4d2000 (usable)
[    0.000000]  BIOS-e820: 000000003f4d2000 - 000000003f4dd000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4dd000 - 000000003f534000 (usable)
[    0.000000]  BIOS-e820: 000000003f534000 - 000000003f537000 (reserved)
[    0.000000]  BIOS-e820: 000000003f537000 - 000000003f5bb000 (usable)
[    0.000000]  BIOS-e820: 000000003f5bb000 - 000000003f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f67a000 (usable)
[    0.000000]  BIOS-e820: 000000003f67a000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f700000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe270
[    0.000000] Entering add_active_range(0, 0, 259706) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259706
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259706
[    0.000000] On node 0 totalpages: 259706
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 236 pages used for memmap
[    0.000000]   HighMem zone: 30094 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 3F6FE120, 006C (r1 HPQOEM SLIC-MPC        1       1000013)
[    0.000000] ACPI: FACP 3F6FD000, 00F4 (r4 HP     SPARTAN         1 LOHR        0)
[    0.000000] ACPI: DSDT 3F6F4000, 802F (r1 HP     SPARTAN         1 LOHR        0)
[    0.000000] ACPI: FACS 3F67D000, 0040
[    0.000000] ACPI: APIC 3F6F3000, 0068 (r2 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: HPET 3F6F2000, 0038 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: MCFG 3F6F1000, 003C (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: ASF! 3F6F0000, 00A5 (r32 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: SLIC 3F6EF000, 0176 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: BOOT 3F6EE000, 0028 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: SSDT 3F6ED000, 05D7 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    0.000000] ACPI: SSDT 3F6EC000, 04C4 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257678
[    0.000000] Kernel command line: root=UUID=feedf49c-564c-4df2-afeb-7707de078a24 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.063 MHz processor.
[   16.452690] Console: colour VGA+ 80x25
[   16.452693] console [tty0] enabled
[   16.453039] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.453326] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.474113] Memory: 1017616k/1038824k available (2177k kernel code, 20388k reserved, 1006k data, 368k init, 121248k highmem)
[   16.474119] virtual kernel memory layout:
[   16.474120]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.474121]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.474122]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.474123]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.474124]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.474125]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   16.474126]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   16.474128] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.474170] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.474315] hpet clockevent registered
[   16.554183] Calibrating delay using timer specific routine.. 3728.41 BogoMIPS (lpj=7456825)
[   16.554204] Security Framework initialized
[   16.554212] SELinux:  Disabled at boot.
[   16.554227] AppArmor: AppArmor initialized
[   16.554231] Failure registering capabilities with primary security module.
[   16.554238] Mount-cache hash table entries: 512
[   16.554366] Initializing cgroup subsys ns
[   16.554371] Initializing cgroup subsys cpuacct
[   16.554381] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001 00000000
[   16.554388] monitor/mwait feature present.
[   16.554389] using mwait in idle threads.
[   16.554393] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.554395] CPU: L2 cache: 1024K
[   16.554398] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   16.554407] Compat vDSO mapped to ffffe000.
[   16.554421] Checking 'hlt' instruction... OK.
[   16.570540] SMP alternatives: switching to UP code
[   16.572037] Freeing SMP alternatives: 11k freed
[   16.572133] Early unpacking initramfs... done
[   16.880571] ACPI: Core revision 20070126
[   16.880622] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.929990] CPU0: Intel(R) Celeron(R) CPU          540  @ 1.86GHz stepping 01
[   16.930013] Total of 1 processors activated (3728.41 BogoMIPS).
[   16.930207] ENABLING IO-APIC IRQs
[   16.930398] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.077317] Brought up 1 CPUs
[   17.077337] CPU0 attaching sched-domain:
[   17.077339]  domain 0: span 01
[   17.077341]   groups: 01
[   17.077484] net_namespace: 64 bytes
[   17.077494] Booting paravirtualized kernel on bare hardware
[   17.077913] Time: 22:06:03  Date: 07/10/08
[   17.077934] NET: Registered protocol family 16
[   17.078099] EISA bus registered
[   17.078104] ACPI: bus type pci registered
[   17.078327] PCI: Using configuration type 1
[   17.078342] Setting up standard PCI resources
[   17.079744] ACPI: EC: Look up EC in DSDT
[   17.102728] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   17.104604] ACPI: Interpreter enabled
[   17.104607] ACPI: (supports S0 S3 S4 S5)
[   17.104621] ACPI: Using IOAPIC for interrupt routing
[   17.105791] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.244312] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   17.244315] ACPI: EC: driver started in interrupt mode
[   17.244350] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.245100] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   17.245104] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   17.245715] PCI: Transparent bridge - 0000:00:1e.0
[   17.245749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.246066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   17.246168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   17.251527] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   17.251631] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   17.251733] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   17.251835] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   17.251935] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[   17.252036] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[   17.252137] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[   17.252237] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   17.252361] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.252389] pnp: PnP ACPI init
[   17.252396] ACPI: bus type pnp registered
[   17.306257] pnp: PnP ACPI: found 9 devices
[   17.306260] ACPI: ACPI bus type pnp unregistered
[   17.306263] PnPBIOS: Disabled by ACPI PNP
[   17.306456] PCI: Using ACPI for IRQ routing
[   17.306459] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.316879] NET: Registered protocol family 8
[   17.316882] NET: Registered protocol family 20
[   17.316914] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.316918] hpet0: 3 64-bit timers, 14318180 Hz
[   17.317953] AppArmor: AppArmor Filesystem Enabled
[   17.320854] Time: tsc clocksource has been installed.
[   17.320868] Switched to high resolution mode on CPU 0
[   17.328832] system 00:01: ioport range 0x164e-0x164f has been reserved
[   17.328835] system 00:01: ioport range 0x600-0x60f has been reserved
[   17.328837] system 00:01: ioport range 0x610-0x610 has been reserved
[   17.328839] system 00:01: ioport range 0x800-0x80f has been reserved
[   17.328841] system 00:01: ioport range 0x810-0x817 has been reserved
[   17.328843] system 00:01: ioport range 0x400-0x47f has been reserved
[   17.328848] system 00:01: ioport range 0x500-0x53f has been reserved
[   17.328850] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[   17.328853] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.328856] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   17.328858] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.328861] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.328863] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   17.328866] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.328868] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.359185] PCI: Bridge: 0000:00:1c.0
[   17.359188]   IO window: 2000-2fff
[   17.359195]   MEM window: 51300000-523fffff
[   17.359199]   PREFETCH window: 50000000-50ffffff
[   17.359205] PCI: Bridge: 0000:00:1e.0
[   17.359208]   IO window: 1000-1fff
[   17.359214]   MEM window: 51200000-512fffff
[   17.359219]   PREFETCH window: disabled.
[   17.359253] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 18 (level, low) -> IRQ 16
[   17.359260] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.359275] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.359285] NET: Registered protocol family 2
[   17.396743] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.396962] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.397537] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.397907] TCP: Hash tables configured (established 131072 bind 65536)
[   17.397910] TCP reno registered
[   17.408829] checking if image is initramfs... it is
[   18.010894] Freeing initrd memory: 7319k freed
[   18.011081] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[   18.011083] Simple Boot Flag at 0x44 set to 0x1
[   18.011524] audit: initializing netlink socket (disabled)
[   18.011540] audit(1215727564.384:1): initialized
[   18.011705] highmem bounce pool size: 64 pages
[   18.013399] VFS: Disk quotas dquot_6.5.1
[   18.013465] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.013590] io scheduler noop registered
[   18.013591] io scheduler anticipatory registered
[   18.013593] io scheduler deadline registered
[   18.013602] io scheduler cfq registered (default)
[   18.013616] Boot video device is 0000:00:02.0
[   18.013878] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.013941] assign_interrupt_mode Found MSI capability
[   18.013994] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.014024] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.014253] isapnp: Scanning for PnP cards...
[   18.368246] isapnp: No Plug & Play device found
[   18.391463] Real Time Clock Driver v1.12ac
[   18.391655] hpet_resources: 0xfed00000 is busy
[   18.391684] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.392794] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.392856] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.392946] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.429816] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.429820] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.438948] mice: PS/2 mouse device common for all mice
[   18.439044] EISA: Probing bus 0 at eisa.0
[   18.439050] Cannot allocate resource for EISA slot 1
[   18.439052] Cannot allocate resource for EISA slot 2
[   18.439054] Cannot allocate resource for EISA slot 3
[   18.439075] EISA: Detected 0 cards.
[   18.439078] cpuidle: using governor ladder
[   18.439079] cpuidle: using governor menu
[   18.439158] NET: Registered protocol family 1
[   18.439184] Using IPI No-Shortcut mode
[   18.439210] registered taskstats version 1
[   18.439294]   Magic number: 0:157:148
[   18.439322]   hash matches device ttyp2
[   18.439370]   hash matches device device:19
[   18.439378] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.439380] EDD information not available.
[   18.439569] Freeing unused kernel memory: 368k freed
[   18.462869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.641052] fuse init (API version 7.9)
[   19.658090] Monitor-Mwait will be used to enter C-1 state
[   19.658094] Monitor-Mwait will be used to enter C-2 state
[   19.658096] Monitor-Mwait will be used to enter C-3 state
[   19.658204] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.658209] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.658222] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.662104] ACPI: Thermal Zone [TZ01] (0 C)
[   20.182487] usbcore: registered new interface driver usbfs
[   20.182509] usbcore: registered new interface driver hub
[   20.195872] usbcore: registered new device driver usb
[   20.197231] USB Universal Host Controller Interface driver v3.0
[   20.197285] ACPI: PCI Interrupt 0000:00:1d.0[D] -> GSI 21 (level, low) -> IRQ 17
[   20.197297] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.197301] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.197514] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.197549] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00003080
[   20.197677] usb usb1: configuration #1 chosen from 1 choice
[   20.197698] hub 1-0:1.0: USB hub found
[   20.197702] hub 1-0:1.0: 2 ports detected
[   20.268697] 8139too Fast Ethernet driver 0.9.28
[   20.287889] SCSI subsystem initialized
[   20.299763] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 18
[   20.299775] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.299780] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.299802] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.299837] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[   20.299939] usb usb2: configuration #1 chosen from 1 choice
[   20.299959] hub 2-0:1.0: USB hub found
[   20.299963] hub 2-0:1.0: 2 ports detected
[   20.343428] libata version 3.00 loaded.
[   20.403586] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 19 (level, low) -> IRQ 19
[   20.403598] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.403603] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.403623] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.403656] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00003040
[   20.403755] usb usb3: configuration #1 chosen from 1 choice
[   20.403775] hub 3-0:1.0: USB hub found
[   20.403779] hub 3-0:1.0: 2 ports detected
[   20.507570] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   20.507585] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.507589] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.507611] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   20.511513] ehci_hcd 0000:00:1d.7: debug port 1
[   20.511519] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.511528] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x52404800
[   20.527276] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.527414] usb usb4: configuration #1 chosen from 1 choice
[   20.527434] hub 4-0:1.0: USB hub found
[   20.527440] hub 4-0:1.0: 6 ports detected
[   20.631284] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 21
[   20.631300] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   20.632310] eth0: RealTek RTL8139 at 0x1000, 00:1e:ec:2d:ea:b2, IRQ 21
[   20.632313] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.634155] ahci 0000:00:1f.2: version 3.0
[   20.634185] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 17 (level, low) -> IRQ 22
[   20.634231] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   20.634233] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   20.635375] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.870665] usb 4-6: new high speed USB device using ehci_hcd and address 2
[   21.069143] usb 4-6: configuration #1 chosen from 1 choice
[   21.118229] Clocksource tsc unstable (delta = -696300762 ns)
[   21.124651] Time: hpet clocksource has been installed.
[   21.230116] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   21.230120] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
[   21.230126] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.230357] scsi0 : ahci
[   21.230570] scsi1 : ahci
[   21.230695] scsi2 : ahci
[   21.230786] ata1: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 222
[   21.230789] ata2: SATA max UDMA/133 abar m2048@0x52404000 port 0x52404180 irq 222
[   21.230793] ata3: SATA max UDMA/133 abar m2048@0x52404000 port 0x52404200 irq 222
[   21.312189] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.313382] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   21.314159] ata1.00: ATA-8: Hitachi HTS542512K9SA00, BB2OC32P, max UDMA/100
[   21.314162] ata1.00: 234441648 sectors, multi 16: LBA48 
[   21.315494] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   21.316284] ata1.00: configured for UDMA/100
[   21.323568] ata2: SATA link down (SStatus 0 SControl 0)
[   21.330875] ata3: SATA link down (SStatus 0 SControl 0)
[   21.330985] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BB2O PQ: 0 ANSI: 5
[   21.332874] ata_piix 0000:00:1f.1: version 2.12
[   21.332891] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   21.332924] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.333733] scsi3 : ata_piix
[   21.334095] scsi4 : ata_piix
[   21.334532] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30a0 irq 14
[   21.334535] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30a8 irq 15
[   21.340732] Driver 'sd' needs updating - please use bus_type methods
[   21.342513] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.342525] sd 0:0:0:0: [sda] Write Protect is off
[   21.342527] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.342541] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.342589] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.342598] sd 0:0:0:0: [sda] Write Protect is off
[   21.342599] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.342612] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.342615]  sda: sda1 sda2 sda3 < sda5 sda6 >
[   21.396052] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.401421] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.662313] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[   21.849937] ata4.00: configured for MWDMA2
[   21.871891] Attempting manual resume
[   21.871894] swsusp: Resume From Partition 8:6
[   21.871896] PM: Checking swsusp image.
[   21.872045] PM: Resume from disk failed.
[   21.885151] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.885154] EXT3-fs: write access will be enabled during recovery.
[   22.019932] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  HS02 PQ: 0 ANSI: 5
[   22.020020] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   22.031978] Driver 'sr' needs updating - please use bus_type methods
[   22.055873] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.055878] Uniform CD-ROM driver Revision: 3.20
[   22.055935] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   22.441848] kjournald starting.  Commit interval 5 seconds
[   22.441863] EXT3-fs: sda5: orphan cleanup on readonly fs
[   22.441868] ext3_orphan_cleanup: deleting unreferenced inode 235724
[   22.441887] EXT3-fs: sda5: 1 orphan inode deleted
[   22.441889] EXT3-fs: recovery complete.
[   22.457244] EXT3-fs: mounted filesystem with ordered data mode.
[   31.671595] Linux agpgart interface v0.102
[   31.777292] agpgart: Detected an Intel 965GM Chipset.
[   31.777558] agpgart: Detected 7676K stolen memory.
[   31.807784] agpgart: AGP aperture is 256M @ 0x40000000
[   31.918053] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.980389] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.424244] input: Power Button (FF) as /devices/virtual/input/input2
[   32.436139] ACPI: Power Button (FF) [PWRF]
[   32.436218] input: Power Button (CM) as /devices/virtual/input/input3
[   32.452075] ACPI: Power Button (CM) [PWRB]
[   32.452131] input: Lid Switch as /devices/virtual/input/input4
[   32.452193] ACPI: Lid Switch [LID0]
[   32.452232] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.464064] ACPI: Sleep Button (CM) [SLPB]
[   32.536034] ACPI: AC Adapter [AC] (off-line)
[   32.641299] ACPI: Battery Slot [BAT0] (battery present)
[   32.676001] ACPI: WMI-Acer: Mapper loaded
[   32.895317] iTCO_vendor_support: vendor-support=0
[   32.947235] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.947373] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[   32.947425] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.189279] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   33.202741] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   33.741919] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   33.741949] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.792857] ath_hal: module license 'Proprietary' taints kernel.
[   33.853613] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.987469] wlan: 0.9.4
[   34.058916] ath_pci: 0.9.4
[   34.058996] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   34.059012] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.107431] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   34.107447] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[   34.126080] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   34.787942] Linux video capture interface: v2.00
[   34.888355] uvcvideo: Found UVC 1.00 device Webcam-101 (064e:c108)
[   34.895963] usbcore: registered new interface driver uvcvideo
[   34.895968] USB Video Class driver (v0.1.0)
[   35.276128] input: PS/2 Mouse as /devices/virtual/input/input8
[   35.333615] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   36.382385] lp: driver loaded but no devices found
[   36.550189] Adding 481908k swap on /dev/sda6.  Priority:-1 extents:1 across:481908k
[   36.714303] EXT3 FS on sda5, internal journal
[   37.254831] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.577209] No dock devices found.
[   38.577457] apm: BIOS not found.
[   38.693937] ppdev: user-space parallel port driver
[   38.806103] audit(1215723988.543:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4837 profile="/usr/sbin/cupsd" namespace="default"
[   39.787493] eth0: link down
[   39.864882] Bluetooth: Core ver 2.11
[   39.865393] NET: Registered protocol family 31
[   39.865397] Bluetooth: HCI device and connection manager initialized
[   39.865400] Bluetooth: HCI socket layer initialized
[   39.906827] Bluetooth: L2CAP ver 2.9
[   39.906831] Bluetooth: L2CAP socket layer initialized
[   39.960950] Bluetooth: RFCOMM socket layer initialized
[   39.961135] Bluetooth: RFCOMM TTY layer initialized
[   39.961137] Bluetooth: RFCOMM ver 1.8
[   43.096603] [drm] Initialized drm 1.1.0 20060810
[   43.099317] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   43.099325] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.099393] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   85.430394] NET: Registered protocol family 10
[   85.430770] lo: Disabled Privacy Extensions
[   85.431201] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  263.736363] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[  263.736368] Bluetooth: BNEP filters: protocol multicast
[  263.784301] Bridge firewalling registered
[  263.784612] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  533.209856] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  533.211520] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  535.641148] NET: Registered protocol family 17
[  551.375949] eth0: no IPv6 routers present
```

---

### Post by qprfact on 2008-07-25
I've also tried using Auto-NDIS Wrapper, and all that happens is it freezes the PC

---

### Post by m_ad on 2008-07-25
The .inf file you're supposed to use for ndiswrapper is the windows .inf driver. Usually it's on your devices cd, but a lot of times you can just download a .zip from the manufacturers website.

What wireless card do you have?

---

### Post by Growbag on 2008-07-25
It looks like you have an Atheros wireless card, open a terminal and type:

```
lspci
```

And post the output here.

As for ndiswrapper, you need the Windows XP driver, if it came with Vista, chances are you can't even get an XP driver.

Check the drivers/downloads website of the manufacturer for the XP driver for the wireless adapter, and try again using that.

Or better still, search this forum for help with the card you have (from the output of *lspci* above).

---

### Post by qprfact on 2008-07-25
Thanks! I will give it a try this weekend and see where I get!

---

### Post by qprfact on 2008-07-26
Output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by qprfact on 2008-07-26
Thanks Growbag! Using the information you pointed me to in lspci, I found this thread - [ubuntu] [SOLVED] Atheros AR5007 not working on 8.04 Hardy - and here I am working wirelessly!

Thanks again to all the help offered on these forums!

---

