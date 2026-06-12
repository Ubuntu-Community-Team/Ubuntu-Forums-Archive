---
title: "How to install AVerMedia AVer TV Super 007 in Hardy"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by azsarker on 2008-08-02
Hi,
I'm totally new in Ubuntu 8.04 (GNU/Linux), started using this two months back for the first time. I was a MS Windows XP user.
All my hardware is working fine except that my TV card AVerMedia AVer TV Super 007 is not working at all. And I don't even know how to install the software (the tv card does not have any Linux software) or drivers (I don't know what they are called in Linux).
Can anyone please help me to install the relevant software and make it work, from the scratch?
I installed and tried the TVtime Television Viewer from the menu Applications-Sound & Video, but nothing happens, also there are no options for channel scanning in TVtime.
I really like Ubuntu and am planning to shift totally if my tv card works (I hate to keep a copy of Windows ONLY for the tv card).

---

### Post by cariboo on 2008-08-02
In a terminal type:

```
lspci
```

Post the output in your next post. We should be able to tell what chipset your tv tuner card has.

Another thing is to look here:

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

to see if your card is listed and what driver it needs.

Jim

---

### Post by azsarker on 2008-08-03
The command gave me the following result:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

---

### Post by azsarker on 2008-08-03
Thank you for answering and helping. Hope things will work out fine.

---

### Post by tarasin on 2008-08-03
I have the same card and it is auto detected in hardy. The problem is picking the correct program to watch tv with.

For Ubuntu you should install me-tv from system-administration-synaptic package manager. 

When you first set it up it will ask you if it should scan for channels, just enter your region and there you have it.

An alternative is kaffeine from kubuntu which requires a little bit more setup but is a great player.

Hope this helps.

---

### Post by azsarker on 2008-08-03
> For Ubuntu you should install me-tv from system-administration-synaptic package manager.

Thanks tarasin,

I've installed the me-tv like you suggested, but when trying to run the program I got the following message: "No tuner device"

This is very strange. I use the same pc and use the card with Windows (on a different hard drive).

I don't have kaffeine, but will try to install and try.

Thanks.

---

### Post by azsarker on 2008-08-03
I just installed kaffeine, but don't see anything to handle the tv settings, channels etc. I'm totally lost...

---

### Post by tarasin on 2008-08-03
this message is saying that your device is not recognized.
could you open a terminal and type in:  dmesg This will print out a huge list of devices on your system look for:

> [   39.766368] saa7133[0]: found at 0000:00:06.0, rev: 209, irq: 21, latency: 84, mmio: 0xdffff000
[   39.766373] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]
[   39.766382] saa7133[0]: board init: gpio is 40000
[   39.831481] Driver 'sr' needs updating - please use bus_type methods
[   39.868173] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   39.868178] Uniform CD-ROM driver Revision: 3.20
[   39.868222] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   39.898008] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   39.898066] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   39.899082] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   39.899088] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   39.899094] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   39.899100] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.899105] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[   39.899111] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.899117] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.899123] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.990313] nvidia: module license 'NVIDIA' taints kernel.
[   40.628841] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   40.682586] tda8290 0-004b: setting tuner address to 60
[   40.786546] tuner 0-004b: type set to tda8290+75a
[   40.842479] tda8290 0-004b: setting tuner address to 60
[   40.950435] tuner 0-004b: type set to tda8290+75a
[   40.953156] saa7133[0]: registered device video0 [v4l2]
[   40.953176] saa7133[0]: registered device vbi0
[   40.953323] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 22
[   40.953332] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   40.953556] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.961655] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   40.961664] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 23
[   40.961805] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.157400] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   41.196596] parport_pc 00:0a: reported by Plug and Play ACPI
[   41.196640] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.197822] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   41.501255] saa7134 ALSA driver for DMA sound loaded
[   41.501282] saa7133[0]/alsa: saa7133[0] at 0xdffff000 irq 21 registered as card -2
[   41.545419] DVB: registering new adapter (saa7133[0])
[   41.545426] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   41.617940] tda1004x: setting up plls for 48MHz sampling clock
[   41.900751] tda1004x: found firmware revision 20 -- ok


your card should = no 117 and firmware revision 20 ok.
I will await your reply before continuing.

Please note this card is a analogue/digital card at the moment only the digital portion is supported. 
More information can be obtained from [http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007")
Hope this helps.

---

### Post by azsarker on 2008-08-03
Hi,

I just typed what you said and I got the following message. If I'm not mistaken, my card is not detected, neither do I have firmware 20. Pls tell me what to do next.

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-20-openvz (buildd@rothera) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jul 28 17:34:35 UTC 2008 (Ubuntu 2.6.24-4.6-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003e677000 (usable)
[    0.000000]  BIOS-e820: 000000003e677000 - 000000003e715000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003e715000 - 000000003f595000 (usable)
[    0.000000]  BIOS-e820: 000000003f595000 - 000000003f59d000 (reserved)
[    0.000000]  BIOS-e820: 000000003f59d000 - 000000003f62b000 (usable)
[    0.000000]  BIOS-e820: 000000003f62b000 - 000000003f62f000 (reserved)
[    0.000000]  BIOS-e820: 000000003f62f000 - 000000003f6a9000 (usable)
[    0.000000]  BIOS-e820: 000000003f6a9000 - 000000003f6e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e9000 - 000000003f6ed000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ed000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe200
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 259840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259840
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259840
[    0.000000] On node 0 totalpages: 259840
[    0.000000]   DMA zone: 36 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4060 pages, LIFO batch:0
[    0.000000]   Normal zone: 1980 pages used for memmap
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 267 pages used for memmap
[    0.000000]   HighMem zone: 30197 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 3F6FD038, 0050 (r1 INTEL  D945GCR        11       1000013)
[    0.000000] ACPI: FACP 3F6FC000, 0074 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: DSDT 3F6F7000, 4C39 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: FACS 3F6A9000, 0040
[    0.000000] ACPI: APIC 3F6F6000, 0078 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: WDDT 3F6F5000, 0040 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: MCFG 3F6F4000, 003C (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: ASF! 3F6F3000, 00A6 (r32 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: HPET 3F6F2000, 0038 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6F1000, 01BC (r1 INTEL     CpuPm       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6F0000, 01B7 (r1 INTEL   Cpu0Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6EF000, 01B7 (r1 INTEL   Cpu1Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6EE000, 01B7 (r1 INTEL   Cpu2Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6ED000, 01B7 (r1 INTEL   Cpu3Ist       11 MSFT  1000013)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000008f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257557
[    0.000000] Kernel command line: root=UUID=4d21a4f3-1ccf-491b-982f-5abff5575e54 ro quiet splash vga=792
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.064 MHz processor.
[   16.430322] Console: colour dummy device 80x25
[   16.430326] console [tty0] enabled
[   16.430539] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.430772] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.451077] Memory: 1015376k/1039360k available (2211k kernel code, 22152k reserved, 1044k data, 384k init, 120848k highmem)
[   16.451085] virtual kernel memory layout:
[   16.451087]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   16.451088]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   16.451090]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   16.451092]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.451094]       .init : 0xc0434000 - 0xc0494000   ( 384 kB)
[   16.451095]       .data : 0xc0328ceb - 0xc042df64   (1044 kB)
[   16.451097]       .text : 0xc0100000 - 0xc0328ceb   (2211 kB)
[   16.451101] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.451158] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.451286] hpet clockevent registered
[   16.601208] Calibrating delay using timer specific routine.. 3992.52 BogoMIPS (lpj=19962634)
[   16.621229] Mount-cache hash table entries: 512
[   16.621362] Initializing cgroup subsys ns
[   16.621368] Initializing cgroup subsys cpuacct
[   16.621380] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   16.621388] monitor/mwait feature present.
[   16.621390] using mwait in idle threads.
[   16.621395] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.621397] CPU: L2 cache: 1024K
[   16.621400] CPU: Physical Processor ID: 0
[   16.621403] CPU: Processor Core ID: 0
[   16.621405] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   16.621415] Compat vDSO mapped to ffffe000.
[   16.621428] Checking 'hlt' instruction... OK.
[   16.661596] SMP alternatives: switching to UP code
[   16.663035] Early unpacking initramfs... done
[   16.971621] ACPI: Core revision 20070126
[   16.971659] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.974673] Page beancounter hash is 65536 entries.
[   16.974827] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[   16.974846] SMP alternatives: switching to SMP code
[   16.975518] Booting processor 1/1 eip 3000
[   16.985721] Initializing CPU#1
[   17.130910] Calibrating delay using timer specific routine.. 3990.01 BogoMIPS (lpj=19950090)
[   17.130918] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   17.130924] monitor/mwait feature present.
[   17.130928] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.130930] CPU: L2 cache: 1024K
[   17.130933] CPU: Physical Processor ID: 0
[   17.130935] CPU: Processor Core ID: 1
[   17.130937] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   17.131358] CPU1: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[   17.131377] Total of 2 processors activated (7982.54 BogoMIPS).
[   17.131524] ENABLING IO-APIC IRQs
[   17.131693] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.350906] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.370911] Brought up 2 CPUs
[   17.370934] CPU0 attaching sched-domain:
[   17.370937]  domain 0: span 03
[   17.370939]   groups: 01 02
[   17.370942] CPU1 attaching sched-domain:
[   17.370944]  domain 0: span 03
[   17.370947]   groups: 02 01
[   17.371144] net_namespace: 76 bytes
[   17.371159] Booting paravirtualized kernel on bare hardware
[   17.371236] Time:  3:13:35  Date: 08/04/08
[   17.371268] NET: Registered protocol family 16
[   17.371447] EISA bus registered
[   17.371452] ACPI: bus type pci registered
[   17.373351] PCI: Using configuration type 1
[   17.373377] Setting up standard PCI resources
[   17.380029] ACPI: EC: Look up EC in DSDT
[   17.381862] ACPI: Interpreter enabled
[   17.381866] ACPI: (supports S0 S1 S3 S4 S5)
[   17.381879] ACPI: Using IOAPIC for interrupt routing
[   17.385253] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.385847] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   17.385852] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   17.386471] PCI: Transparent bridge - 0000:00:1e.0
[   17.386504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.386748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   17.386882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   17.386974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   17.387065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   17.387157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   17.390485] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   17.390569] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   17.390651] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[   17.390731] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[   17.390821] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   17.390902] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   17.390983] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   17.391063] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   17.391192] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.391221] pnp: PnP ACPI init
[   17.391229] ACPI: bus type pnp registered
[   17.393352] pnp: PnP ACPI: found 13 devices
[   17.393355] ACPI: ACPI bus type pnp unregistered
[   17.393360] PnPBIOS: Disabled by ACPI PNP
[   17.393580] PCI: Using ACPI for IRQ routing
[   17.393584] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.461113] NET: Registered protocol family 8
[   17.461116] NET: Registered protocol family 20
[   17.461151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.461156] hpet0: 3 64-bit timers, 14318180 Hz
[   17.470806] Time: tsc clocksource has been installed.
[   17.470824] Switched to high resolution mode on CPU 0
[   17.470931] Switched to high resolution mode on CPU 1
[   17.490870] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   17.490877] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   17.490883] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   17.490889] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   17.490895] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   17.490901] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   17.490908] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[   17.490914] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[   17.490920] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[   17.490926] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[   17.490940] system 00:06: ioport range 0x500-0x53f has been reserved
[   17.490947] system 00:06: ioport range 0x400-0x47f has been reserved
[   17.490952] system 00:06: ioport range 0x680-0x6ff has been reserved
[   17.490958] system 00:06: ioport range 0x770-0x77f has been reserved
[   17.521345] PCI: Bridge: 0000:00:1c.0
[   17.521348]   IO window: disabled.
[   17.521353]   MEM window: disabled.
[   17.521357]   PREFETCH window: disabled.
[   17.521362] PCI: Bridge: 0000:00:1c.1
[   17.521365]   IO window: 1000-1fff
[   17.521370]   MEM window: 50100000-501fffff
[   17.521374]   PREFETCH window: 50300000-503fffff
[   17.521379] PCI: Bridge: 0000:00:1c.2
[   17.521381]   IO window: disabled.
[   17.521385]   MEM window: disabled.
[   17.521389]   PREFETCH window: disabled.
[   17.521393] PCI: Bridge: 0000:00:1c.3
[   17.521395]   IO window: disabled.
[   17.521400]   MEM window: disabled.
[   17.521403]   PREFETCH window: disabled.
[   17.521408] PCI: Bridge: 0000:00:1e.0
[   17.521410]   IO window: disabled.
[   17.521415]   MEM window: 50000000-500fffff
[   17.521419]   PREFETCH window: disabled.
[   17.521445] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   17.521452] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.521469] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   17.521475] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.521492] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.521498] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.521515] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   17.521521] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.521531] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.521540] NET: Registered protocol family 2
[   17.620784] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.620881] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.621385] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.621693] TCP: Hash tables configured (established 131072 bind 65536)
[   17.621697] TCP reno registered
[   17.650942] checking if image is initramfs... it is
[   18.264986] Freeing initrd memory: 7902k freed
[   18.265777] audit: initializing netlink socket (disabled)
[   18.265791] audit(1217819615.680:1): initialized
[   18.265981] highmem bounce pool size: 64 pages
[   18.265986] Total HugeTLB memory allocated, 0
[   18.268670] VFS: Disk quotas dquot_6.5.1
[   18.268731] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.268884] io scheduler noop registered
[   18.268887] io scheduler anticipatory registered
[   18.268889] io scheduler deadline registered
[   18.268943] io scheduler cfq registered (default)
[   18.268956] Boot video device is 0000:00:02.0
[   18.269221] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.269260] assign_interrupt_mode Found MSI capability
[   18.269295] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.269329] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.269406] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.269444] assign_interrupt_mode Found MSI capability
[   18.269476] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.269508] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.269582] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.269621] assign_interrupt_mode Found MSI capability
[   18.269652] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.269682] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.269757] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.269796] assign_interrupt_mode Found MSI capability
[   18.269827] Allocate Port Service[0000:00:1c.3:pcie00]
[   18.269858] Allocate Port Service[0000:00:1c.3:pcie02]
[   18.270076] isapnp: Scanning for PnP cards...
[   18.625898] isapnp: No Plug & Play device found
[   18.648606] Real Time Clock Driver v1.12ac
[   18.648710] hpet_resources: 0xfed00000 is busy
[   18.648736] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.648855] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.649501] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.650220] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.650284] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.650373] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   18.653011] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.653016] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.702818] mice: PS/2 mouse device common for all mice
[   18.702944] EISA: Probing bus 0 at eisa.0
[   18.702950] Cannot allocate resource for EISA slot 1
[   18.702953] Cannot allocate resource for EISA slot 2
[   18.702974] EISA: Detected 0 cards.
[   18.702977] cpuidle: using governor ladder
[   18.702980] cpuidle: using governor menu
[   18.703105] NET: Registered protocol family 1
[   18.703164] Using IPI No-Shortcut mode
[   18.703193] registered taskstats version 1
[   18.703289]   Magic number: 4:793:208
[   18.703313]   hash matches device ttyt6
[   18.703354]   hash matches device vcsa
[   18.703371] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   18.703710] Freeing unused kernel memory: 384k freed
[   18.722136] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.969482] fuse init (API version 7.9)
[   20.029720] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.029732] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.415442] usbcore: registered new interface driver usbfs
[   20.415467] usbcore: registered new interface driver hub
[   20.415502] usbcore: registered new device driver usb
[   20.431857] r8169 Gigabit Ethernet driver 2.2LK loaded
[   20.431886] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   20.431907] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.432096] eth0: RTL8168b/8111b at 0xf8870000, 00:1c:c0:0e:92:dd, XID 38500000 IRQ 219
[   20.479241] USB Universal Host Controller Interface driver v3.0
[   20.479314] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   20.479326] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.479330] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.479551] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   20.479581] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002080
[   20.479699] usb usb1: configuration #1 chosen from 1 choice
[   20.479722] hub 1-0:1.0: USB hub found
[   20.479728] hub 1-0:1.0: 2 ports detected
[   20.542012] SCSI subsystem initialized
[   20.574545] libata version 3.00 loaded.
[   20.591761] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   20.591775] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.591781] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.591805] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.591837] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[   20.591941] usb usb2: configuration #1 chosen from 1 choice
[   20.591964] hub 2-0:1.0: USB hub found
[   20.591969] hub 2-0:1.0: 2 ports detected
[   20.701685] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.701697] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.701702] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.701724] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.701752] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[   20.701850] usb usb3: configuration #1 chosen from 1 choice
[   20.701871] hub 3-0:1.0: USB hub found
[   20.701876] hub 3-0:1.0: 2 ports detected
[   20.811641] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   20.811654] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   20.811659] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   20.811682] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.811712] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00002020
[   20.811818] usb usb4: configuration #1 chosen from 1 choice
[   20.811843] hub 4-0:1.0: USB hub found
[   20.811849] hub 4-0:1.0: 2 ports detected
[   20.871524] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   20.919259] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   20.919274] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.919279] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.919308] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.923226] ehci_hcd 0000:00:1d.7: debug port 1
[   20.923232] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.923243] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x502c4000
[   21.008939] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.009048] usb usb5: configuration #1 chosen from 1 choice
[   21.009070] hub 5-0:1.0: USB hub found
[   21.009076] hub 5-0:1.0: 8 ports detected
[   21.141432] ata_piix 0000:00:1f.1: version 2.12
[   21.141454] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   21.141491] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.142331] scsi0 : ata_piix
[   21.142510] scsi1 : ata_piix
[   21.142797] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[   21.142801] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[   21.408724] usb 1-1: device not accepting address 2, error -71
[   21.481541] ata1.01: ATAPI: PHILIPS SPD2414T, P1.0, max UDMA/66
[   21.481554] ata1.01: limited to UDMA/33 due to 40-wire cable
[   21.681358] ata1.01: configured for UDMA/33
[   21.681399] ata2: port disabled. ignoring.
[   21.682134] scsi 0:0:1:0: CD-ROM            PHILIPS  SPD2414T         P1.0 PQ: 0 ANSI: 5
[   21.682231] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   21.682279] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   21.682315] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.682386] scsi2 : ata_piix
[   21.682433] scsi3 : ata_piix
[   21.682860] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[   21.682864] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[   21.858693] ata3.00: ATA-7: ST380815AS, 3.CHF, max UDMA/100
[   21.858698] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   21.898665] ata3.00: configured for UDMA/100
[   22.071714] scsi 2:0:0:0: Direct-Access     ATA      ST380815AS       3.CH PQ: 0 ANSI: 5
[   22.150876] Driver 'sd' needs updating - please use bus_type methods
[   22.151675] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.151690] sd 2:0:0:0: [sda] Write Protect is off
[   22.151693] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.151711] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.151768] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.151779] sd 2:0:0:0: [sda] Write Protect is off
[   22.151782] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.151799] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.151803]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   22.175552] sr0: scsi3-mmc drive: 16x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.175559] Uniform CD-ROM driver Revision: 3.20
[   22.175631] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   22.193390]  sda5 >
[   22.193511] sd 2:0:0:0: [sda] Attached SCSI disk
[   22.210861] sr 0:0:1:0: Attached scsi generic sg0 type 5
[   22.210883] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   22.408265] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   22.494074] Attempting manual resume
[   22.494079] swsusp: Resume From Partition 8:5
[   22.494081] PM: Checking swsusp image.
[   22.494233] PM: Resume from disk failed.
[   22.579662] usb 1-1: configuration #1 chosen from 1 choice
[   22.643242] EXT3-fs: INFO: recovery required on readonly filesystem.
[   22.643249] EXT3-fs: write access will be enabled during recovery.
[   22.857945] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   23.045729] usb 2-2: configuration #1 chosen from 1 choice
[   23.117844] usbcore: registered new interface driver hiddev
[   23.139632] input: Padix Co. Ltd. USB, 3-axis, 4-button joystick as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
[   23.139671] input,hidraw0: USB HID v1.00 Joystick [Padix Co. Ltd. USB, 3-axis, 4-button joystick] on usb-0000:00:1d.1-2
[   23.139694] usbcore: registered new interface driver usbhid
[   23.139705] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.709399] kjournald starting.  Commit interval 5 seconds
[   23.709417] EXT3-fs: sda1: orphan cleanup on readonly fs
[   23.709427] ext3_orphan_cleanup: deleting unreferenced inode 1876031
[   23.709457] ext3_orphan_cleanup: deleting unreferenced inode 1876028
[   23.709469] ext3_orphan_cleanup: deleting unreferenced inode 1875981
[   23.709480] EXT3-fs: sda1: 3 orphan inodes deleted
[   23.709484] EXT3-fs: recovery complete.
[   23.743379] EXT3-fs: mounted filesystem with ordered data mode.
[   31.755688] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.113008] nf_conntrack version 0.5.0 (16240 buckets, 64960 max)
[   33.155021] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.235002] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.362338] Linux agpgart interface v0.102
[   33.544837] agpgart: Detected an Intel 945G Chipset.
[   33.545317] agpgart: Detected 7932K stolen memory.
[   33.559540] agpgart: AGP aperture is 256M @ 0x40000000
[   33.634838] input: Power Button (FF) as /devices/virtual/input/input3
[   33.704896] ACPI: Power Button (FF) [PWRF]
[   33.704975] input: Sleep Button (CM) as /devices/virtual/input/input4
[   33.774621] ACPI: Sleep Button (CM) [SLPB]
[   34.104568] usbcore: registered new interface driver usbserial
[   34.104586] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   34.104615] usbcore: registered new interface driver usbserial_generic
[   34.104618] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   34.144532] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial support registered for cp2101
[   34.144565] cp2101 1-1:1.0: cp2101 converter detected
[   34.274336] usb 1-1: reset full speed USB device using uhci_hcd and address 4
[   34.314325] intel_rng: FWH not detected
[   34.444493] usb 1-1: cp2101 converter now attached to ttyUSB0
[   34.444510] usbcore: registered new interface driver cp2101
[   34.444513] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/cp2101.c: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07
[   34.721698] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   34.751639] Linux video capture interface: v2.00
[   34.874158] iTCO_vendor_support: vendor-support=0
[   34.914258] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.914360] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   34.914393] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.747641] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   35.823753] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   35.823783] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.884082] parport_pc 00:07: reported by Plug and Play ACPI
[   35.884111] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   35.890988] saa7130/34: v4l2 driver version 0.2.14 loaded
[   35.912798] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   35.962664] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   35.962675] saa7133[0]: found at 0000:05:04.0, rev: 209, irq: 18, latency: 32, mmio: 0x50000000
[   35.962683] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]
[   35.962693] saa7133[0]: board init: gpio is 40000
[   36.113383] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   36.113400] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   36.113414] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[   36.113429] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.113442] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[   36.113456] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.113470] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.113484] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.113832] saa7133[0]: registered device video0 [v4l2]
[   36.113853] saa7133[0]: registered device vbi0
[   36.193301] saa7134 ALSA driver for DMA sound loaded
[   36.193336] saa7133[0]/alsa: saa7133[0] at 0x50000000 irq 18 registered as card -2
[   37.052930] lp0: using parport0 (interrupt-driven).
[   37.106383] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   37.689540] EXT3 FS on sda1, internal journal
[   37.832530] device-mapper: uevent: version 1.0.3
[   37.832565] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   39.591603] No dock devices found.
[   41.350636] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.350642] apm: disabled - APM is not SMP safe.
[   41.540562] ppdev: user-space parallel port driver
[   42.689898] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   42.689908] vboxdrv: Successfully done.
[   42.689978] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   42.689983] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[   43.039644] tun: Universal TUN/TAP device driver, 1.6
[   43.039653] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   45.005197] r8169: eth0: link down
[   45.148529] Bluetooth: Core ver 2.11
[   45.148687] NET: Registered protocol family 31
[   45.148692] Bluetooth: HCI device and connection manager initialized
[   45.148699] Bluetooth: HCI socket layer initialized
[   45.188518] Bluetooth: L2CAP ver 2.9
[   45.188526] Bluetooth: L2CAP socket layer initialized
[   45.306065] Bluetooth: RFCOMM socket layer initialized
[   45.306086] Bluetooth: RFCOMM TTY layer initialized
[   45.306090] Bluetooth: RFCOMM ver 1.8
[   47.147570] [drm] Initialized drm 1.1.0 20060810
[   47.267503] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   47.267519] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.267623] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   48.012516] vmmon: module license 'unspecified' taints kernel.
[   48.027111] /dev/vmmon[5897]: Module vmmon: registered with major=10 minor=165
[   48.027136] /dev/vmmon[5897]: Module vmmon: initialized
[   48.594231] /dev/vmnet: open called by PID 5926 (vmnet-bridge)
[   48.594244] /dev/vmnet: hub 0 does not exist, allocating memory.
[   48.594254] /dev/vmnet: port on hub 0 successfully opened
[   48.594269] bridge-eth0: enabling the bridge
[   48.594274] bridge-eth0: up
[   48.594276] bridge-eth0: already up
[   48.594279] bridge-eth0: attached
[   48.624948] /dev/vmnet: open called by PID 5935 (vmnet-netifup)
[   48.624965] /dev/vmnet: hub 1 does not exist, allocating memory.
[   48.624982] /dev/vmnet: port on hub 1 successfully opened
[   48.624987] /dev/vmnet: open called by PID 5940 (vmnet-netifup)
[   48.624997] /dev/vmnet: hub 8 does not exist, allocating memory.
[   48.625013] /dev/vmnet: port on hub 8 successfully opened
[   48.700673] /dev/vmnet: open called by PID 5942 (vmnet-natd)
[   48.700695] /dev/vmnet: port on hub 8 successfully opened
[   48.935118] /dev/vmnet: open called by PID 5965 (vmnet-dhcpd)
[   48.935143] /dev/vmnet: port on hub 8 successfully opened
[   49.118331] /dev/vmnet: open called by PID 5966 (vmnet-dhcpd)
[   49.118353] /dev/vmnet: port on hub 1 successfully opened
[   62.979266] NET: Registered protocol family 10
[   62.979551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.153515] vmnet8: no IPv6 routers present
[   73.803162] vmnet1: no IPv6 routers present
[  266.599998] PPP generic driver version 2.4.2
[  267.349594] PPP BSD Compression module registered
[  267.479544] PPP Deflate Compression module registered
[ 1988.248451] usb 5-3: new high speed USB device using ehci_hcd and address 4
[ 1988.399419] usb 5-3: configuration #1 chosen from 1 choice
[ 1988.563241] usbcore: registered new interface driver libusual
[ 1988.618265] Initializing USB Mass Storage driver...
[ 1988.620001] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1988.620415] usbcore: registered new interface driver usb-storage
[ 1988.620423] USB Mass Storage support registered.
[ 1988.620990] usb-storage: device found at 4
[ 1988.620995] usb-storage: waiting for device to settle before scanning
[ 1993.615543] usb-storage: device scan complete
[ 1993.616730] scsi 4:0:0:0: Direct-Access     USB2.0   Mobile Disk      1.00 PQ: 0 ANSI: 2
[ 1993.619321] sd 4:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
[ 1993.620210] sd 4:0:0:0: [sdb] Write Protect is off
[ 1993.620219] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1993.620224] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.623078] sd 4:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
[ 1993.623694] sd 4:0:0:0: [sdb] Write Protect is off
[ 1993.623701] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1993.623705] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.623714]  sdb: sdb1
[ 1993.697424] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1993.697483] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2275.103410] usb 5-3: USB disconnect, address 4
[ 2275.107598] VFS: Busy inodes after unmount. sb = e30d3400, fs type = vfat, sb count = 1073741825, sb->s_root = /
[ 2275.107618] inode = f687b038, inode->i_count = 1, inode->i_nlink = 5, inode->i_mode = 16832, inode->i_state = 0, inode->i_flags = 0, inode->i_devices.next = f687b150, inode->i_devices.prev = f687b150, inode->i_ino = 1
[ 2275.107628] inode dump: 00 00 00 00 98 69 99 c1 a0 f8 d9 f0 a0 fe 81 f6 70 34 0d e3 e8 b1 87 f6 c0 e4 82 f7 c0 e4 82 f7 01 00 00 00 01 00 00 00 05 00 00 00 e8 03 00 00 00 00 00 00 00 00 00 00 03 00 00 00 00 04 00 00 00 00 00 00 00 00 00 00 ae 7b 96 48 00 00 00 00 ae 7b 96 48 00 00 00 00 ae 7b 96 48 00 00 00 00 09 00 00 00 02 00 00 00 00 00 c0 41 01 00 00 00 01 00 00 00 01 00 00 00 b0 b0 87 f6 b0 b0 87 f6 00 00 00 00 01 00 00 00 c0 b0 87 f6 c0 b0 87 f6 e0 7b 26 f9 a0 b8 2a f9 00 34 0d e3 00 00 00 00 dc b0 87 f6 38 b0 87 f6 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 01 00 01 00 fc b0 87 f6 fc b0 87 f6 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 bb 4f c0 d2 00 12 00 c8 4c 6e f7 01 00 00 00 24 b1 87 f6 24 b1 87 f6 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 50 b1 87 f6 50 b1 87 f6 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6c b1 87 f6 6c b1 87 f6 01 00 00 00 01 00 00 00 7c b1 87 f6 7c b1 87 f6 00 00 00 00 29 98 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
[ 2275.107868]   d_alias / d_count=2 d_flags=10
[ 2275.107871] 02 00 00 00 10 00 00 00 01 00 00 00 38 b0 87 f6 00 00 00 00 00 00 00 00 80 e4 82 f7 00 00 00 00 01 00 00 00 ec e4 82 f7 a8 e4 82 f7 a8 e4 82 f7 b0 e4 82 f7 b0 e4 82 f7 b8 e4 82 f7 b8 e4 82 f7 50 b0 87 f6 50 b0 87 f6 00 00 00 00 40 93 26 f9 00 34 0d e3 00 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 fc 01 00 00 20 d3 4e c0 2f 00 64 75 6c 65 73 00 6c 65 5c 78 32 66 76 66 61 74 00 00 00 00 a4 81 01 00 00 00 01 00 00 00 01 00 00 00 
[ 2275.107981] mnt=f7c89700 count=1 flags=23 exp_mask=0
[ 2275.107985] b0 6e c0 f7 b0 6e c0 f7 00 75 c0 f7 80 cd 90 f7 80 e4 82 f7 00 34 0d e3 18 97 c8 f7 18 97 c8 f7 18 75 c0 f7 a0 94 c8 f7 23 00 00 00 d0 b0 cd f7 88 11 c0 f7 30 7a c0 f7 38 97 c8 f7 38 97 c8 f7 40 97 c8 f7 40 97 c8 f7 48 97 c8 f7 48 97 c8 f7 50 97 c8 f7 50 97 c8 f7 00 00 00 00 80 11 c0 f7 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

---

### Post by azsarker on 2008-08-03
Sorry to post it with double click, therefore had to remove the second post.

---

### Post by tarasin on 2008-08-04
There are a couple of things you can try.

the first thing is to check if v4l driver is present on your system. Go to synaptic and seach for these 3 programmes
> xserver-xorg-video-v4l
> libpt-1.10.10-plugins-v4l
> libpt-1.10.10-plugins-v4l2
The version numbers may vary but not be less than these.
If they are installed or not, then install/reinstall them.
These are the ones I have in mine Ubuntu Hardy Heron 32bit

You may need to reboot your computer again then use > dsmeg in a terminal to see if your device has registered correctly.

Failing this you can download the latest v4l driver and install it yourself which I will help you with as I have had to do it on previous versions.
Let me know how you get on

---

### Post by azsarker on 2008-08-04
Thanks again!
I checked with synaptic and all the three programmes are installed. But with dmesg I get the following again. Pls tell me what to do next...

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-20-openvz (buildd@rothera) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jul 28 17:34:35 UTC 2008 (Ubuntu 2.6.24-4.6-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003e677000 (usable)
[    0.000000]  BIOS-e820: 000000003e677000 - 000000003e715000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003e715000 - 000000003f595000 (usable)
[    0.000000]  BIOS-e820: 000000003f595000 - 000000003f59d000 (reserved)
[    0.000000]  BIOS-e820: 000000003f59d000 - 000000003f62b000 (usable)
[    0.000000]  BIOS-e820: 000000003f62b000 - 000000003f62f000 (reserved)
[    0.000000]  BIOS-e820: 000000003f62f000 - 000000003f6a9000 (usable)
[    0.000000]  BIOS-e820: 000000003f6a9000 - 000000003f6e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e9000 - 000000003f6ed000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ed000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe200
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 259840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259840
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259840
[    0.000000] On node 0 totalpages: 259840
[    0.000000]   DMA zone: 36 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4060 pages, LIFO batch:0
[    0.000000]   Normal zone: 1980 pages used for memmap
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 267 pages used for memmap
[    0.000000]   HighMem zone: 30197 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 3F6FD038, 0050 (r1 INTEL  D945GCR        11       1000013)
[    0.000000] ACPI: FACP 3F6FC000, 0074 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: DSDT 3F6F7000, 4C39 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: FACS 3F6A9000, 0040
[    0.000000] ACPI: APIC 3F6F6000, 0078 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: WDDT 3F6F5000, 0040 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: MCFG 3F6F4000, 003C (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: ASF! 3F6F3000, 00A6 (r32 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: HPET 3F6F2000, 0038 (r1 INTEL  D945GCR        11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6F1000, 01BC (r1 INTEL     CpuPm       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6F0000, 01B7 (r1 INTEL   Cpu0Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6EF000, 01B7 (r1 INTEL   Cpu1Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6EE000, 01B7 (r1 INTEL   Cpu2Ist       11 MSFT  1000013)
[    0.000000] ACPI: SSDT 3F6ED000, 01B7 (r1 INTEL   Cpu3Ist       11 MSFT  1000013)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000008f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257557
[    0.000000] Kernel command line: root=UUID=4d21a4f3-1ccf-491b-982f-5abff5575e54 ro quiet splash vga=792
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.088 MHz processor.
[   32.305541] Console: colour dummy device 80x25
[   32.305545] console [tty0] enabled
[   32.305759] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   32.305992] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.326305] Memory: 1015376k/1039360k available (2211k kernel code, 22152k reserved, 1044k data, 384k init, 120848k highmem)
[   32.326314] virtual kernel memory layout:
[   32.326315]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   32.326317]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   32.326319]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   32.326320]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   32.326322]       .init : 0xc0434000 - 0xc0494000   ( 384 kB)
[   32.326324]       .data : 0xc0328ceb - 0xc042df64   (1044 kB)
[   32.326326]       .text : 0xc0100000 - 0xc0328ceb   (2211 kB)
[   32.326329] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.326386] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   32.326513] hpet clockevent registered
[   32.476434] Calibrating delay using timer specific routine.. 3992.51 BogoMIPS (lpj=19962582)
[   32.496457] Mount-cache hash table entries: 512
[   32.496590] Initializing cgroup subsys ns
[   32.496595] Initializing cgroup subsys cpuacct
[   32.496606] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   32.496615] monitor/mwait feature present.
[   32.496617] using mwait in idle threads.
[   32.496621] CPU: L1 I cache: 32K, L1 D cache: 32K
[   32.496624] CPU: L2 cache: 1024K
[   32.496627] CPU: Physical Processor ID: 0
[   32.496629] CPU: Processor Core ID: 0
[   32.496631] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   32.496642] Compat vDSO mapped to ffffe000.
[   32.496654] Checking 'hlt' instruction... OK.
[   32.536822] SMP alternatives: switching to UP code
[   32.538257] Early unpacking initramfs... done
[   32.846808] ACPI: Core revision 20070126
[   32.846846] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.849854] Page beancounter hash is 65536 entries.
[   32.850008] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[   32.850027] SMP alternatives: switching to SMP code
[   32.850698] Booting processor 1/1 eip 3000
[   32.860900] Initializing CPU#1
[   33.006137] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=19950156)
[   33.006145] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   33.006151] monitor/mwait feature present.
[   33.006155] CPU: L1 I cache: 32K, L1 D cache: 32K
[   33.006157] CPU: L2 cache: 1024K
[   33.006160] CPU: Physical Processor ID: 0
[   33.006162] CPU: Processor Core ID: 1
[   33.006164] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   33.006540] CPU1: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[   33.006560] Total of 2 processors activated (7982.54 BogoMIPS).
[   33.006700] ENABLING IO-APIC IRQs
[   33.006868] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   33.226132] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   33.246137] Brought up 2 CPUs
[   33.246160] CPU0 attaching sched-domain:
[   33.246163]  domain 0: span 03
[   33.246165]   groups: 01 02
[   33.246169] CPU1 attaching sched-domain:
[   33.246171]  domain 0: span 03
[   33.246173]   groups: 02 01
[   33.246368] net_namespace: 76 bytes
[   33.246383] Booting paravirtualized kernel on bare hardware
[   33.246459] Time:  0:14:57  Date: 08/05/08
[   33.246491] NET: Registered protocol family 16
[   33.246669] EISA bus registered
[   33.246674] ACPI: bus type pci registered
[   33.248558] PCI: Using configuration type 1
[   33.248584] Setting up standard PCI resources
[   33.255244] ACPI: EC: Look up EC in DSDT
[   33.257079] ACPI: Interpreter enabled
[   33.257083] ACPI: (supports S0 S1 S3 S4 S5)
[   33.257096] ACPI: Using IOAPIC for interrupt routing
[   33.260467] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.261061] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   33.261066] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   33.261684] PCI: Transparent bridge - 0000:00:1e.0
[   33.261718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.261962] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   33.262095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   33.262188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   33.262279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   33.262370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   33.265700] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   33.265784] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   33.265866] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[   33.265946] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[   33.266036] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   33.266117] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   33.266198] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   33.266277] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   33.266406] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.266436] pnp: PnP ACPI init
[   33.266443] ACPI: bus type pnp registered
[   33.268568] pnp: PnP ACPI: found 13 devices
[   33.268571] ACPI: ACPI bus type pnp unregistered
[   33.268575] PnPBIOS: Disabled by ACPI PNP
[   33.268796] PCI: Using ACPI for IRQ routing
[   33.268799] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.336341] NET: Registered protocol family 8
[   33.336344] NET: Registered protocol family 20
[   33.336379] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   33.336383] hpet0: 3 64-bit timers, 14318180 Hz
[   33.346034] Time: tsc clocksource has been installed.
[   33.346052] Switched to high resolution mode on CPU 0
[   33.346157] Switched to high resolution mode on CPU 1
[   33.366097] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   33.366104] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   33.366110] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   33.366116] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   33.366123] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   33.366129] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   33.366135] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[   33.366142] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[   33.366148] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[   33.366154] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[   33.366168] system 00:06: ioport range 0x500-0x53f has been reserved
[   33.366174] system 00:06: ioport range 0x400-0x47f has been reserved
[   33.366179] system 00:06: ioport range 0x680-0x6ff has been reserved
[   33.366185] system 00:06: ioport range 0x770-0x77f has been reserved
[   33.396569] PCI: Bridge: 0000:00:1c.0
[   33.396572]   IO window: disabled.
[   33.396577]   MEM window: disabled.
[   33.396580]   PREFETCH window: disabled.
[   33.396586] PCI: Bridge: 0000:00:1c.1
[   33.396589]   IO window: 1000-1fff
[   33.396594]   MEM window: 50100000-501fffff
[   33.396598]   PREFETCH window: 50300000-503fffff
[   33.396603] PCI: Bridge: 0000:00:1c.2
[   33.396604]   IO window: disabled.
[   33.396609]   MEM window: disabled.
[   33.396612]   PREFETCH window: disabled.
[   33.396617] PCI: Bridge: 0000:00:1c.3
[   33.396619]   IO window: disabled.
[   33.396623]   MEM window: disabled.
[   33.396627]   PREFETCH window: disabled.
[   33.396632] PCI: Bridge: 0000:00:1e.0
[   33.396634]   IO window: disabled.
[   33.396639]   MEM window: 50000000-500fffff
[   33.396642]   PREFETCH window: disabled.
[   33.396668] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   33.396675] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   33.396693] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   33.396698] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   33.396716] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   33.396721] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   33.396739] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   33.396744] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   33.396755] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   33.396763] NET: Registered protocol family 2
[   33.496013] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.496111] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   33.496604] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   33.496912] TCP: Hash tables configured (established 131072 bind 65536)
[   33.496915] TCP reno registered
[   33.526167] checking if image is initramfs... it is
[   34.137254] Freeing initrd memory: 7902k freed
[   34.138043] audit: initializing netlink socket (disabled)
[   34.138056] audit(1217895297.680:1): initialized
[   34.138255] highmem bounce pool size: 64 pages
[   34.138261] Total HugeTLB memory allocated, 0
[   34.140942] VFS: Disk quotas dquot_6.5.1
[   34.141002] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.141154] io scheduler noop registered
[   34.141156] io scheduler anticipatory registered
[   34.141159] io scheduler deadline registered
[   34.141212] io scheduler cfq registered (default)
[   34.141225] Boot video device is 0000:00:02.0
[   34.141490] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.141529] assign_interrupt_mode Found MSI capability
[   34.141564] Allocate Port Service[0000:00:1c.0:pcie00]
[   34.141598] Allocate Port Service[0000:00:1c.0:pcie02]
[   34.141675] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   34.141713] assign_interrupt_mode Found MSI capability
[   34.141745] Allocate Port Service[0000:00:1c.1:pcie00]
[   34.141777] Allocate Port Service[0000:00:1c.1:pcie02]
[   34.141851] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   34.141889] assign_interrupt_mode Found MSI capability
[   34.141921] Allocate Port Service[0000:00:1c.2:pcie00]
[   34.141951] Allocate Port Service[0000:00:1c.2:pcie02]
[   34.142026] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   34.142064] assign_interrupt_mode Found MSI capability
[   34.142096] Allocate Port Service[0000:00:1c.3:pcie00]
[   34.142126] Allocate Port Service[0000:00:1c.3:pcie02]
[   34.142344] isapnp: Scanning for PnP cards...
[   34.498166] isapnp: No Plug & Play device found
[   34.520993] Real Time Clock Driver v1.12ac
[   34.521098] hpet_resources: 0xfed00000 is busy
[   34.521125] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.521246] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.521901] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.522613] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.522677] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   34.522761] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   34.525513] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.525519] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.565555] mice: PS/2 mouse device common for all mice
[   34.565680] EISA: Probing bus 0 at eisa.0
[   34.565687] Cannot allocate resource for EISA slot 1
[   34.565690] Cannot allocate resource for EISA slot 2
[   34.565711] EISA: Detected 0 cards.
[   34.565715] cpuidle: using governor ladder
[   34.565717] cpuidle: using governor menu
[   34.565844] NET: Registered protocol family 1
[   34.565904] Using IPI No-Shortcut mode
[   34.565933] registered taskstats version 1
[   34.566028]   Magic number: 4:550:202
[   34.566051]   hash matches device ttyt0
[   34.566107] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   34.566446] Freeing unused kernel memory: 384k freed
[   34.584629] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   35.824767] fuse init (API version 7.9)
[   35.894960] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.894973] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   36.257114] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.257141] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   36.257161] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   36.257337] eth0: RTL8168b/8111b at 0xf8890000, 00:1c:c0:0e:92:dd, XID 38500000 IRQ 219
[   36.306096] usbcore: registered new interface driver usbfs
[   36.306120] usbcore: registered new interface driver hub
[   36.307846] usbcore: registered new device driver usb
[   36.347247] SCSI subsystem initialized
[   36.398979] libata version 3.00 loaded.
[   36.436967] USB Universal Host Controller Interface driver v3.0
[   36.437054] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   36.437068] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   36.437073] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   36.437300] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   36.437333] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002080
[   36.437466] usb usb1: configuration #1 chosen from 1 choice
[   36.437491] hub 1-0:1.0: USB hub found
[   36.437497] hub 1-0:1.0: 2 ports detected
[   36.554466] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   36.554480] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.554485] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.554510] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   36.554540] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[   36.554646] usb usb2: configuration #1 chosen from 1 choice
[   36.554669] hub 2-0:1.0: USB hub found
[   36.554675] hub 2-0:1.0: 2 ports detected
[   36.664412] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   36.664428] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.664433] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.664459] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   36.664489] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[   36.664593] usb usb3: configuration #1 chosen from 1 choice
[   36.664615] hub 3-0:1.0: USB hub found
[   36.664622] hub 3-0:1.0: 2 ports detected
[   36.774363] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   36.774377] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   36.774382] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   36.774407] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   36.774438] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00002020
[   36.774543] usb usb4: configuration #1 chosen from 1 choice
[   36.774568] hub 4-0:1.0: USB hub found
[   36.774575] hub 4-0:1.0: 2 ports detected
[   36.834229] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   36.884519] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   36.884535] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   36.884539] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   36.884566] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   36.888483] ehci_hcd 0000:00:1d.7: debug port 1
[   36.888490] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   36.888500] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x502c4000
[   36.976673] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.976835] usb usb5: configuration #1 chosen from 1 choice
[   36.976860] hub 5-0:1.0: USB hub found
[   36.976868] hub 5-0:1.0: 8 ports detected
[   37.124124] ata_piix 0000:00:1f.1: version 2.12
[   37.124145] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   37.124181] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   37.125033] scsi0 : ata_piix
[   37.125986] scsi1 : ata_piix
[   37.126299] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[   37.126303] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[   37.386449] usb 1-1: device not accepting address 2, error -71
[   37.464231] ata1.01: ATAPI: PHILIPS SPD2414T, P1.0, max UDMA/66
[   37.664059] ata1.01: configured for UDMA/66
[   37.664099] ata2: port disabled. ignoring.
[   37.664823] scsi 0:0:1:0: CD-ROM            PHILIPS  SPD2414T         P1.0 PQ: 0 ANSI: 5
[   37.664920] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   37.664966] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   37.665005] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.665055] scsi2 : ata_piix
[   37.665102] scsi3 : ata_piix
[   37.665530] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[   37.665534] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[   37.863895] ata3.00: ATA-7: ST380815AS, 3.CHF, max UDMA/100
[   37.863900] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.893928] ata3.00: configured for UDMA/100
[   38.066929] scsi 2:0:0:0: Direct-Access     ATA      ST380815AS       3.CH PQ: 0 ANSI: 5
[   38.126087] Driver 'sd' needs updating - please use bus_type methods
[   38.126181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   38.126194] sd 2:0:0:0: [sda] Write Protect is off
[   38.126197] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.126214] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.126259] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   38.126270] sd 2:0:0:0: [sda] Write Protect is off
[   38.126273] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.126290] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.126295]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   38.150759] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   38.150766] Uniform CD-ROM driver Revision: 3.20
[   38.150838] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   38.169234]  sda5 >
[   38.169359] sd 2:0:0:0: [sda] Attached SCSI disk
[   38.196132] sr 0:0:1:0: Attached scsi generic sg0 type 5
[   38.196154] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   38.393441] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   38.469440] Attempting manual resume
[   38.469444] swsusp: Resume From Partition 8:5
[   38.469447] PM: Checking swsusp image.
[   38.469586] PM: Resume from disk failed.
[   38.567394] usb 1-1: configuration #1 chosen from 1 choice
[   38.594291] kjournald starting.  Commit interval 5 seconds
[   38.594304] EXT3-fs: mounted filesystem with ordered data mode.
[   38.843234] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   39.029419] usb 2-2: configuration #1 chosen from 1 choice
[   45.941964] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.331773] nf_conntrack version 0.5.0 (16240 buckets, 64960 max)
[   47.228845] Linux agpgart interface v0.102
[   47.341351] agpgart: Detected an Intel 945G Chipset.
[   47.341831] agpgart: Detected 7932K stolen memory.
[   47.355845] agpgart: AGP aperture is 256M @ 0x40000000
[   47.401365] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.501292] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.691239] input: Power Button (FF) as /devices/virtual/input/input2
[   47.751035] ACPI: Power Button (FF) [PWRF]
[   47.751124] input: Sleep Button (CM) as /devices/virtual/input/input3
[   47.818523] ACPI: Sleep Button (CM) [SLPB]
[   48.550603] intel_rng: FWH not detected
[   48.840599] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   49.097921] usbcore: registered new interface driver usbserial
[   49.097939] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   49.097971] usbcore: registered new interface driver usbserial_generic
[   49.097974] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   49.257746] iTCO_vendor_support: vendor-support=0
[   49.277737] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   49.277852] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   49.277887] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   49.350358] parport_pc 00:07: reported by Plug and Play ACPI
[   49.350387] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   49.470288] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/usb-serial.c: USB Serial support registered for cp2101
[   49.470321] cp2101 1-1:1.0: cp2101 converter detected
[   49.597621] usb 1-1: reset full speed USB device using uhci_hcd and address 4
[   49.782604] usb 1-1: cp2101 converter now attached to ttyUSB0
[   49.782637] usbcore: registered new interface driver cp2101
[   49.782642] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/usb/serial/cp2101.c: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07
[   49.782665] usbcore: registered new interface driver hiddev
[   49.812781] input: Padix Co. Ltd. USB, 3-axis, 4-button joystick as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input5
[   49.850049] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   49.850079] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   49.867517] input,hidraw0: USB HID v1.00 Joystick [Padix Co. Ltd. USB, 3-axis, 4-button joystick] on usb-0000:00:1d.1-2
[   49.867537] usbcore: registered new interface driver usbhid
[   49.867541] /build/buildd/linux-2.6.24/debian/build/custom-source-openvz/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   49.917404] Linux video capture interface: v2.00
[   49.941726] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   50.049936] saa7130/34: v4l2 driver version 0.2.14 loaded
[   50.050010] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   50.050019] saa7133[0]: found at 0000:05:04.0, rev: 209, irq: 18, latency: 32, mmio: 0x50000000
[   50.050027] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]
[   50.050040] saa7133[0]: board init: gpio is 40000
[   50.225859] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   50.247229] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   50.247240] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   50.247248] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[   50.247257] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247265] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[   50.247273] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247281] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247289] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247298] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247306] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247314] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247322] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247330] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247339] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247347] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.247355] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   50.250900] saa7133[0]: registered device video0 [v4l2]
[   50.250924] saa7133[0]: registered device vbi0
[   50.290147] saa7134_alsa: disagrees about version of symbol saa7134_tvaudio_setmute
[   50.290153] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[   50.290287] saa7134_alsa: disagrees about version of symbol saa_dsp_writel
[   50.290290] saa7134_alsa: Unknown symbol saa_dsp_writel
[   50.290441] saa7134_alsa: disagrees about version of symbol videobuf_dma_free
[   50.290444] saa7134_alsa: Unknown symbol videobuf_dma_free
[   50.290611] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_alloc
[   50.290615] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[   50.290659] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_build
[   50.290662] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[   50.290698] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_free
[   50.290701] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[   50.290738] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_init
[   50.290741] saa7134_alsa: Unknown symbol saa7134_dmasound_init
[   50.290865] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_exit
[   50.290868] saa7134_alsa: Unknown symbol saa7134_dmasound_exit
[   50.290958] saa7134_alsa: disagrees about version of symbol videobuf_dma_init
[   50.290961] saa7134_alsa: Unknown symbol videobuf_dma_init
[   50.291095] saa7134_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   50.291099] saa7134_alsa: Unknown symbol videobuf_dma_init_kernel
[   50.291210] saa7134_alsa: Unknown symbol videobuf_pci_dma_unmap
[   50.291337] saa7134_alsa: Unknown symbol videobuf_pci_dma_map
[   50.291380] saa7134_alsa: disagrees about version of symbol saa7134_set_dmabits
[   50.291383] saa7134_alsa: Unknown symbol saa7134_set_dmabits
[   51.259288] lp0: using parport0 (interrupt-driven).
[   51.317384] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   51.915738] EXT3 FS on sda1, internal journal
[   52.088890] device-mapper: uevent: version 1.0.3
[   52.088925] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   54.027864] No dock devices found.
[   55.896851] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   55.896858] apm: disabled - APM is not SMP safe.
[   56.116763] ppdev: user-space parallel port driver
[   57.266115] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   57.266122] vboxdrv: Successfully done.
[   57.266178] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   57.266181] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[   57.615879] tun: Universal TUN/TAP device driver, 1.6
[   57.615888] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   59.538625] r8169: eth0: link down
[   59.654895] Bluetooth: Core ver 2.11
[   59.655033] NET: Registered protocol family 31
[   59.655039] Bluetooth: HCI device and connection manager initialized
[   59.655046] Bluetooth: HCI socket layer initialized
[   59.712293] Bluetooth: L2CAP ver 2.9
[   59.712302] Bluetooth: L2CAP socket layer initialized
[   59.784875] Bluetooth: RFCOMM socket layer initialized
[   59.784896] Bluetooth: RFCOMM TTY layer initialized
[   59.784900] Bluetooth: RFCOMM ver 1.8
[   62.723258] [drm] Initialized drm 1.1.0 20060810
[   62.803213] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   62.803228] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   62.803354] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   63.455686] vmmon: module license 'unspecified' taints kernel.
[   63.472947] /dev/vmmon[5864]: Module vmmon: registered with major=10 minor=165
[   63.472973] /dev/vmmon[5864]: Module vmmon: initialized
[   63.995672] /dev/vmnet: open called by PID 5893 (vmnet-bridge)
[   63.995689] /dev/vmnet: hub 0 does not exist, allocating memory.
[   63.995700] /dev/vmnet: port on hub 0 successfully opened
[   63.995716] bridge-eth0: enabling the bridge
[   63.995720] bridge-eth0: up
[   63.995722] bridge-eth0: already up
[   63.995726] bridge-eth0: attached
[   64.045155] /dev/vmnet: open called by PID 5908 (vmnet-netifup)
[   64.045172] /dev/vmnet: hub 1 does not exist, allocating memory.
[   64.045183] /dev/vmnet: port on hub 1 successfully opened
[   64.045549] /dev/vmnet: open called by PID 5909 (vmnet-netifup)
[   64.045558] /dev/vmnet: hub 8 does not exist, allocating memory.
[   64.045570] /dev/vmnet: port on hub 8 successfully opened
[   64.060377] /dev/vmnet: open called by PID 5907 (vmnet-natd)
[   64.060394] /dev/vmnet: port on hub 8 successfully opened
[   64.322469] /dev/vmnet: open called by PID 5936 (vmnet-dhcpd)
[   64.322493] /dev/vmnet: port on hub 1 successfully opened
[   64.535031] /dev/vmnet: open called by PID 5935 (vmnet-dhcpd)
[   64.535053] /dev/vmnet: port on hub 8 successfully opened
[   81.233831] NET: Registered protocol family 10
[   81.234103] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   91.378198] vmnet8: no IPv6 routers present
[   92.005370] vmnet1: no IPv6 routers present
[  138.473605] PPP generic driver version 2.4.2
[  139.213319] PPP BSD Compression module registered
[  139.313289] PPP Deflate Compression module registered

---

### Post by tarasin on 2008-08-04
did you reinstall the packages by right clicking on them and then rebooting?

---

### Post by azsarker on 2008-08-04
I din't know that I had to reinstall them. Now I have and also rebooted. What should I do now?

---

### Post by tarasin on 2008-08-04
run dmesg in terminal and see if card=117 no need to post results just say if it works. if it has then start me-tv

---

### Post by tarasin on 2008-08-04
It looks like you will have to install the driver manually
To ensure the driver compiles correctly you will need to check that you have the kernel headers installed
search for kernel in synaptic and you should see something like this
> linux-headers-2.6.24-19

Download the driver from
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz]("http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz") this will start a download of the driver.
download it to your desktop and right click it and extract it there.

open a terminal and change into the v4l directory by using the cd command
cd /home/yourname/Desktop/v4lfoldername

then run these commands to compile a new driver and install the driver. Please check the output from these commands to ensure there are no errors
> make
Then as root 
> sudo make install

if it has installed correctly reboot your computer and use dmesg in a terminal to check output.
if it is card =117 and firmware found ok then start up me-tv or kaffeine to watch tv.

---

### Post by azsarker on 2008-08-04
Sorry to inform you that after doing everything you suggested, still I have no card detected and get this following info from dmesg:

[   29.285423] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]

Thanks again for your efforts. Right now it's quite late for me and I need some sleep. I'll catch you up tomorrow.

---

### Post by azsarker on 2008-08-05
Hi tarasin,
just wanted to inform you that I deleted all those files, reinstalled all of them (as you explained) once again, rebooted the machine - still same results.

Just curious: I'm using an EDGE modem (USB), Could it be that, that thing is using any DMA or IRQ channels? I personally don't know anything much about them, but in Windows they created problems at times, so I had to change slots.

---

### Post by tarasin on 2008-08-05
I dont think it would as linux assigns the channels for devices its possible I suppose.
I had an idea if you still have the live cd then why not run it and see if dmesg gives the correct card number and also install me-tv into the live cd and see if it plays.
I'm off to work now let me know how you get on.

---

### Post by azsarker on 2008-08-06
After booting with the Live-CD I get the following:

[   85.257912] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]

I guess it is the same result.

---

### Post by db260179 on 2008-10-05
It appears you have a newer Super 007 card. Do you still have the card? i could add support if you wish?

---

### Post by azsarker on 2008-10-05
> **db260179 said:**
> It appears you have a newer Super 007 card. Do you still have the card? i could add support if you wish?

Yes, I still have the card and watch the tv using Windows since I could not configure it in Ubuntu. I'd definitely appreciate it, if you could help me out to install the card in Ubuntu. Thanks!

---

### Post by db260179 on 2008-10-05
ok, i will need a few things from you.

Open a terminal (accessories), in the terminal type as follows:

pwd (this shows your current working directory)

lspci -vvnm >lspci1.output && lspci -vvn >lspci2.output (copy the lspci files and attach to this post)

If possible, can you take a picture of the card and manual and box if possible. Also the remote if it has one?

Also send your /var/log/syslog aswell.

Join the #linuxtv  irc channel
i'm db, boot the pc into ubuntu, as i might need some more info

Thanks
David Bentham

---

### Post by azsarker on 2008-10-05
Hi David,

sorry to answer late. I was busy trying to find the box and taking pictures; sending you all the things you've asked as attachment - but couldn't take the picture of the card. It'll take up more time to open the cpu, take the card out to take a pic. Hope these picture in the attachment will suffice.
I don't know how to join you in linuxtv irc channel (still have to learn a lot).
Regards.

---

### Post by db260179 on 2008-10-05
This card is a Analog super 007 (M135a) card. Currently not supported in the linux kernel.

Download the latest v4l-dvb patches, some of the remote keys dont work

Thanks

---

### Post by db260179 on 2008-10-05
duplicate

---

### Post by db260179 on 2008-10-06
Hi, check you private messages!

Thanks

David

---

### Post by aditeman on 2009-02-20
Has this problem been solved?
I've been going through forums for two days trying to get my AverTv Super 007 to work on Ubuntu 8.10 or on MythBuntu 8.10... so far, no luck...

I'm a real newbie to linux (just started this week), so please give me a step by step :)

---

### Post by azsarker on 2009-02-20
Hi Aditeman,

if you read the previous message, you'll see that David (db260179) has tried to help me to run TV with my AverMedia 007. I must thank him a lot for his genuine efforts to make the card work. He made a special Kernel for the card and can be found at his site at: [http://archive.mulberry.towerhamlets.sch.uk/](http://archive.mulberry.towerhamlets.sch.uk/)

Just go to his site and download the file
([http://archive.mulberry.towerhamlets.sch.uk/linux-image-2.6.24-19-avermedia_2.6.24-19.41_i386.deb](http://archive.mulberry.towerhamlets.sch.uk/linux-image-2.6.24-19-avermedia_2.6.24-19.41_i386.deb)) and click, it will install automatically.

Then install the TVTime Television Viewer from System->Administration->Synaptic Package Manager.

After that you have to reboot.

When the Login window comes, go to Options and choose to boot with AverMedia Kernel and then run TVTime.

I must say that something is wrong with my machine or may be I did something wrong (I am not an expert myself in Ubuntu), I can watch TV and set all channels but I somehow do not get any sound, for which David tried a lot for several days, but I could not manage to get the sound working. So right now I watch the TV booting with another Hard Disk with Windows XP, otherwise I am quite satisfied with Ubuntu for all other things.

---

### Post by azsarker on 2009-02-20
Hi Aditeman,

if you read the previous message, you'll see that David (db260179) has tried to help me to run TV with my AverMedia 007. I must thank him a lot for his genuine efforts to make the card work. He made a special Kernel for the card and can be found at his site at: [http://archive.mulberry.towerhamlets.sch.uk/](http://archive.mulberry.towerhamlets.sch.uk/)

Just go to his site and download the file
([http://archive.mulberry.towerhamlets.sch.uk/linux-image-2.6.24-19-avermedia_2.6.24-19.41_i386.deb](http://archive.mulberry.towerhamlets.sch.uk/linux-image-2.6.24-19-avermedia_2.6.24-19.41_i386.deb)) and click, it will install automatically.

Then install the TVTime Television Viewer from System->Administration->Synaptic Package Manager.

After that you have to reboot.

When the Login window comes, go to Options and choose to boot with AverMedia Kernel and then run TVTime.

I must say that something is wrong with my machine or may be I did something wrong (I am not an expert myself in Ubuntu), I can watch TV and set all channels but I somehow do not get any sound, for which David tried a lot for several days, but I could not manage to get the sound working. So right now I watch the TV booting with another Hard Disk with Windows XP, otherwise I am quite satisfied with Ubuntu for all other things.

---

### Post by kenn e on 2009-04-01
Hello,

Is work going on now to support this card in Ubuntu Intrepid?
Will the 'kernel' file posted above (and still available from the link) work with Intrepid?

Interestingly, i can't get my LifeCam VX-1000 to work either,and i have a feeling one has to go or neither will work. I've installed all kinds of v4l2 drivers and patches with no love.

let me know if i can send any screen dumps, i'm a old FreeBSD user trying to take advantage of linux drivers to make my computer more "user friendly" for everyone else in my household without resorting to windows, I'm running a dual boot FreeBSD 7.1 (amd64) and Ubuntu 8.10 (i386) system.

thanks.

---

### Post by azsarker on 2009-04-02
Sorry to inform you Kenn that I'm also new in Linux (Ubuntu) and could not get my tv card work with Ubuntu. I have absolutely no idea about how to tweak with "kernels". So, only for watching TV I still use Windows XP with a second hard disk. For all other work I'm satisfied with Ubuntu. I must also mention that if you go through my previous posts in this thread you'll find that someone tried to help me out. The result was good so far that I can watch tv, change channels but don't get the sound. As you understand without the sound the tv is not good enough. Hope that somebody will find a solution soon.
Best regards.

---

### Post by sufianmehdi on 2011-01-18
> **cariboo907 said:**
> In a terminal type:

```
lspci
```

Post the output in your next post. We should be able to tell what chipset your tv tuner card has.

Another thing is to look here:

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

to see if your card is listed and what driver it needs.

Jim

The command gave me the following result:
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Now How Can I Watch TV From Bangladesh (My Country-Where I Live)

---

