---
title: "System Crashing - (New User)"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by signal_ on 2008-11-13
Hi.  I am new to Ubuntu and have been using it for approximately two weeks.  I am using it on an older laptop: Dell Inspiron 9300: 120 Gb hardrive, 2Gb RAM, 1.6 GHz CPU, ATI Mobility Radeon X300 GPU.

I have the system setup for dual boot Windows XP and Ubuntu 8.10.

For the past two days Ubuntu has been crashing when I open up the System Monitor.  As soon as it opens it crashes.  Also, it crashed one other time when I was using Firefox.  Usually, I have Firefox and Code::Blocks IDE running.  That is it.  The one constant is that it crashes when I open the System Monitor.

It goes to a blank screen and spits out:

```

*Starting System Tools Backends system-tools-backends  [ OK ]
*Starting anac(h)ronistic cron anacron                 [ OK ]
*Starting deferred execution scheduler atd             [ OK ]
*Starting periodic command scheduler crond             [ OK ]
*Enabling additional executable binary formats binfmt-support [ OK ]
*Checking battery state ...                            [ OK ]

```

Then there is usually just a blob of garbled graphics below.

Sometimes there is only one message:

```
*Starting anac(h)ronistic cron anacron                 [ OK ]
```

So what gives?  How can I fix this?  Is Ubuntu 8.10 or Ubuntu in general stable enough or am I better off just using Windows since I am coding and testing and not looking forward to system crashes when doing so?

Please assist.  I will offer any more information needed.  And, to reiterate, I am new to Ubuntu so I am sorry if there's an easy solution that I am unaware of, but I cannot find the solution googling.

Thank you all in advance.

---

### Post by Crafty Kisses on 2008-11-13
Try opening up the terminal and running this command:
```
top
```

---

### Post by ITAndrew on 2008-11-13
Does this "hard" lock your system? I would like to see if you could make this reoccur, when it does hold ctrl and alt and press F1. Log in as a normal user then type

dmesg > test.txt

This will redirect the output to the test text file. If you could post the contents of this file I would be able to get some insight into the problem that is occuring.

Although if your system is hard locking you will be unable to do this, let me know the outcome.

Regards

---

### Post by signal_ on 2008-11-13
I ran the 'top' command.  Its output was:

```
top - 19:58:10 up 2 min,  2 users,  load average: 0.77, 0.61, 0.25
Tasks: 111 total,   2 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.0%us,  0.7%sy,  0.0%ni, 92.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2072772k total,   542108k used,  1530664k free,    18220k buffers
Swap:  3076408k total,        0k used,  3076408k free,   216284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5514 root      20   0  158m  56m  19m S  3.3  2.8   0:08.78 Xorg               
 6116 d         20   0 99904  24m  12m R  0.7  1.2   0:00.52 gnome-terminal     
 6496 d         20   0  2416 1144  884 R  0.7  0.1   0:00.06 top                
 6048 d         20   0  193m  59m  23m S  0.3  2.9   0:07.97 firefox            
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.46 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  124 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
  128 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod 
```


And the output after running dmesg > test.txt, is the test.txt file:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffda000 (usable)
[    0.000000]  BIOS-e820: 000000007ffda000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7ffda max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37827000 - 37fefed9
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 7FFDA7D3, 0040 (r1 DELL    CPi R   27D50913 ASL        61)
[    0.000000] ACPI: FACP 7FFDB400, 0074 (r1 DELL    CPi R   27D50913 ASL        61)
[    0.000000] ACPI: DSDT 7FFDC000, 2A1A (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFEA800, 0040
[    0.000000] ACPI: APIC 7FFDBC00, 0068 (r1 DELL    CPi R   27D50913 ASL        47)
[    0.000000] ACPI: MCFG 7FFDBBC0, 003E (r16 DELL    CPi R   27D50913 ASL        61)
[    0.000000] ACPI: BOOT 7FFDB7C0, 0028 (r1 DELL    CPi R   27D50913 ASL        61)
[    0.000000] ACPI: SSDT 7FFDABE6, 023E (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 7FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: SSDT 7FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037827000 - 0037fefed9]          RAMDISK ==> [0037827000 - 0037fefed9]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ffda
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffda
[    0.000000] On node 0 totalpages: 524153
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292282 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519545
[    0.000000] Kernel command line: root=UUID=5ac63167-8488-4c20-bbbe-49cb3c847301 ro xforcevesa quiet splash rootflags=data=writeback 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1595.997 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063548k/2097000k available (2572k kernel code, 32232k reserved, 1160k data, 424k init, 1179496k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.99 BogoMIPS (lpj=6383988)
[    0.004044] Security Framework initialized
[    0.004056] SELinux:  Disabled at boot.
[    0.004087] AppArmor: AppArmor initialized
[    0.004098] Mount-cache hash table entries: 512
[    0.004330] Initializing cgroup subsys ns
[    0.004337] Initializing cgroup subsys cpuacct
[    0.004341] Initializing cgroup subsys memory
[    0.004362] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004365] CPU: L2 cache: 2048K
[    0.004380] Checking 'hlt' instruction... OK.
[    0.020551] SMP alternatives: switching to UP code
[    0.026903] ACPI: Core revision 20080609
[    0.028114] ACPI: Checking initramfs for custom DSDT
[    0.447697] ENABLING IO-APIC IRQs
[    0.447896] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.487595] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    0.488030] Brought up 1 CPUs
[    0.488030] Total of 1 processors activated (3191.99 BogoMIPS).
[    0.488030] CPU0 attaching sched-domain:
[    0.488030]  domain 0: span 0 level CPU
[    0.488030]   groups: 0
[    0.488030] net_namespace: 840 bytes
[    0.488030] Booting paravirtualized kernel on bare hardware
[    0.488030] Time: 16:55:20  Date: 11/13/08
[    0.488030] NET: Registered protocol family 16
[    0.488030] EISA bus registered
[    0.488030] ACPI: bus type pci registered
[    0.488030] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.488030] PCI: MCFG area at e0000000 reserved in E820
[    0.488030] PCI: Using MMCONFIG for extended config space
[    0.488030] PCI: Using configuration type 1 for base access
[    0.488030] ACPI: EC: Look up EC in DSDT
[    0.502429] ACPI: Interpreter enabled
[    0.502432] ACPI: (supports S0 S3 S4 S5)
[    0.502449] ACPI: Using IOAPIC for interrupt routing
[    0.533394] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.533521] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.533526] pci 0000:00:01.0: PME# disabled
[    0.533606] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
[    0.533666] PCI: 0000:00:1d.1 reg 20 io port: [bf60, bf7f]
[    0.533727] PCI: 0000:00:1d.2 reg 20 io port: [bf40, bf5f]
[    0.533787] PCI: 0000:00:1d.3 reg 20 io port: [bf20, bf3f]
[    0.533851] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80800, ffa80bff]
[    0.533906] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.533912] pci 0000:00:1d.7: PME# disabled
[    0.533996] PCI: 0000:00:1e.2 reg 10 io port: [ed00, edff]
[    0.534005] PCI: 0000:00:1e.2 reg 14 io port: [ec40, ec7f]
[    0.534013] PCI: 0000:00:1e.2 reg 18 32bit mmio: [dffffe00, dfffffff]
[    0.534021] PCI: 0000:00:1e.2 reg 1c 32bit mmio: [dffffd00, dffffdff]
[    0.534056] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.534061] pci 0000:00:1e.2: PME# disabled
[    0.534093] PCI: 0000:00:1e.3 reg 10 io port: [ee00, eeff]
[    0.534101] PCI: 0000:00:1e.3 reg 14 io port: [ec80, ecff]
[    0.534147] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.534152] pci 0000:00:1e.3: PME# disabled
[    0.534237] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.534247] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.534252] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.534289] PCI: 0000:00:1f.2 reg 10 io port: [1f0, 1f7]
[    0.534297] PCI: 0000:00:1f.2 reg 14 io port: [3f4, 3f7]
[    0.534305] PCI: 0000:00:1f.2 reg 18 io port: [170, 177]
[    0.534313] PCI: 0000:00:1f.2 reg 1c io port: [374, 377]
[    0.534322] PCI: 0000:00:1f.2 reg 20 io port: [bfa0, bfaf]
[    0.534352] pci 0000:00:1f.2: PME# supported from D3hot
[    0.534357] pci 0000:00:1f.2: PME# disabled
[    0.534411] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.534465] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
[    0.534471] PCI: 0000:01:00.0 reg 14 io port: [de00, deff]
[    0.534477] PCI: 0000:01:00.0 reg 18 32bit mmio: [dfdf0000, dfdfffff]
[    0.534494] PCI: 0000:01:00.0 reg 30 32bit mmio: [dfe00000, dfe1ffff]
[    0.534509] pci 0000:01:00.0: supports D1
[    0.534511] pci 0000:01:00.0: supports D2
[    0.534557] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.534561] PCI: bridge 0000:00:01.0 32bit mmio: [dfd00000, dfefffff]
[    0.534565] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, d7ffffff]
[    0.534606] PCI: 0000:03:00.0 reg 10 32bit mmio: [dfcfe000, dfcfffff]
[    0.534658] pci 0000:03:00.0: supports D1
[    0.534660] pci 0000:03:00.0: supports D2
[    0.534662] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.534668] pci 0000:03:00.0: PME# disabled
[    0.534705] PCI: 0000:03:01.0 reg 10 32bit mmio: [0, fff]
[    0.534725] pci 0000:03:01.0: supports D1
[    0.534727] pci 0000:03:01.0: supports D2
[    0.534730] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.534736] pci 0000:03:01.0: PME# disabled
[    0.534774] PCI: 0000:03:01.1 reg 10 32bit mmio: [dfcfc800, dfcfcfff]
[    0.534831] pci 0000:03:01.1: supports D1
[    0.534833] pci 0000:03:01.1: supports D2
[    0.534836] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.534841] pci 0000:03:01.1: PME# disabled
[    0.534878] PCI: 0000:03:01.2 reg 10 32bit mmio: [dfcfc700, dfcfc7ff]
[    0.534934] pci 0000:03:01.2: supports D1
[    0.534936] pci 0000:03:01.2: supports D2
[    0.534939] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.534945] pci 0000:03:01.2: PME# disabled
[    0.534996] PCI: 0000:03:03.0 reg 10 32bit mmio: [dfcfd000, dfcfdfff]
[    0.535059] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[    0.535065] pci 0000:03:03.0: PME# disabled
[    0.535116] pci 0000:00:1e.0: transparent bridge
[    0.535124] PCI: bridge 0000:00:1e.0 32bit mmio: [dfc00000, dfcfffff]
[    0.535161] bus 00 -> node 0
[    0.535168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.535754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.535878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.544378] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.544534] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.544686] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.544838] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.544969] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.545105] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.545240] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.545523] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.545565] pnp: PnP ACPI init
[    0.545573] ACPI: bus type pnp registered
[    0.583183] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.583188] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.583310] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.583314] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.583319] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.584613] pnp: PnP ACPI: found 11 devices
[    0.584616] ACPI: ACPI bus type pnp unregistered
[    0.584620] PnPBIOS: Disabled by ACPI PNP
[    0.585015] PCI: Using ACPI for IRQ routing
[    0.585156] NET: Registered protocol family 8
[    0.585156] NET: Registered protocol family 20
[    0.585156] NetLabel: Initializing
[    0.585156] NetLabel:  domain hash size = 128
[    0.585156] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.585156] NetLabel:  unlabeled traffic allowed by default
[    0.585156] hpet clockevent registered
[    0.585156] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.585156] hpet0: 3 64-bit timers, 14318180 Hz
[    0.585880] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.585883]    actual entries 65620
[    0.585981] AppArmor: AppArmor Filesystem Enabled
[    0.586007] ACPI: RTC can wake from S4
[    0.586016] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.586016] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.586016] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.586016] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.586016] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
[    0.586016] system 00:00: iomem range 0x7ffda000-0x7fffffff could not be reserved
[    0.586016] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[    0.586016] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    0.586016] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.586016] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.586016] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    0.586016] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
[    0.586016] system 00:00: iomem range 0xf0004000-0xf0004fff could not be reserved
[    0.586016] system 00:00: iomem range 0xf0005000-0xf0005fff could not be reserved
[    0.586016] system 00:00: iomem range 0xf0006000-0xf0006fff could not be reserved
[    0.586016] system 00:00: iomem range 0xf0008000-0xf000bfff could not be reserved
[    0.586016] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.586016] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.586016] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.586016] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.586016] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.586016] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.586016] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.586016] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.586016] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.586016] system 00:08: ioport range 0x930-0x93f has been reserved
[    0.586016] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.622436] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.622440] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.622444] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.622449] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.622461] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.622464] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.622470] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.622476] pci 0000:03:01.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.622482] pci 0000:03:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.622487] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.622491] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.622498] pci 0000:00:1e.0:   MEM window: 0xdfc00000-0xdfcfffff
[    0.622504] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.622521] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.622526] pci 0000:00:01.0: setting latency timer to 64
[    0.622534] pci 0000:00:1e.0: setting latency timer to 64
[    0.622544] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.622550] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.622558] bus: 00 index 0 io port: [0, ffff]
[    0.622560] bus: 00 index 1 mmio: [0, ffffffff]
[    0.622563] bus: 01 index 0 io port: [d000, dfff]
[    0.622566] bus: 01 index 1 mmio: [dfd00000, dfefffff]
[    0.622569] bus: 01 index 2 mmio: [d0000000, d7ffffff]
[    0.622571] bus: 01 index 3 mmio: [0, 0]
[    0.622574] bus: 03 index 0 io port: [2000, 2fff]
[    0.622577] bus: 03 index 1 mmio: [dfc00000, dfcfffff]
[    0.622580] bus: 03 index 2 mmio: [88000000, 8bffffff]
[    0.622583] bus: 03 index 3 io port: [0, ffff]
[    0.622585] bus: 03 index 4 mmio: [0, ffffffff]
[    0.622588] bus: 04 index 0 io port: [2000, 20ff]
[    0.622590] bus: 04 index 1 io port: [2400, 24ff]
[    0.622593] bus: 04 index 2 mmio: [88000000, 8bffffff]
[    0.622596] bus: 04 index 3 mmio: [8c000000, 8fffffff]
[    0.622606] NET: Registered protocol family 2
[    0.622753] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.623021] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.623713] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.624177] TCP: Hash tables configured (established 131072 bind 65536)
[    0.624182] TCP reno registered
[    0.624333] NET: Registered protocol family 1
[    0.624480] checking if image is initramfs... it is
[    1.088074] Switched to high resolution mode on CPU 0
[    1.480603] Freeing initrd memory: 7971k freed
[    1.480844] Simple Boot Flag at 0x79 set to 0x1
[    1.481434] audit: initializing netlink socket (disabled)
[    1.481455] type=2000 audit(1226595320.480:1): initialized
[    1.489249] highmem bounce pool size: 64 pages
[    1.489258] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.492071] VFS: Disk quotas dquot_6.5.1
[    1.492184] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.492317] msgmni has been set to 1743
[    1.492465] io scheduler noop registered
[    1.492469] io scheduler anticipatory registered
[    1.492472] io scheduler deadline registered
[    1.492486] io scheduler cfq registered (default)
[    1.492602] pci 0000:01:00.0: Boot video device
[    1.492724] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.492757] pcieport-driver 0000:00:01.0: found MSI capability
[    1.492788] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.492843] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.493202] isapnp: Scanning for PnP cards...
[    1.846960] isapnp: No Plug & Play device found
[    1.887996] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.888725] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.888733] serial 0000:00:1e.3: PCI INT B disabled
[    1.890598] brd: module loaded
[    1.890682] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.890818] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.895727] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.895734] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.896074] mice: PS/2 mouse device common for all mice
[    1.896233] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.896265] rtc0: alarms up to one month, y3k, hpet irqs
[    1.896410] EISA: Probing bus 0 at eisa.0
[    1.896418] Cannot allocate resource for EISA slot 1
[    1.896421] Cannot allocate resource for EISA slot 2
[    1.896447] EISA: Detected 0 cards.
[    1.896451] cpuidle: using governor ladder
[    1.896454] cpuidle: using governor menu
[    1.897050] TCP cubic registered
[    1.897082] Using IPI No-Shortcut mode
[    1.897300] registered taskstats version 1
[    1.897441]   Magic number: 0:595:944
[    1.897508] tty ptyyf: hash matches
[    1.897554] tty tty1: hash matches
[    1.897606] rtc_cmos 00:06: setting system clock to 2008-11-13 16:55:22 UTC (1226595322)
[    1.897611] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.897613] EDD information not available.
[    1.897869] Freeing unused kernel memory: 424k freed
[    1.897926] Write protecting the kernel text: 2576k
[    1.897960] Write protecting the kernel read-only data: 936k
[    1.901449] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.120449] fuse init (API version 7.9)
[    2.366592] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    2.366661] processor ACPI0007:00: registered as cooling_device0
[    2.366666] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.371235] thermal LNXTHERM:01: registered as thermal_zone0
[    2.374595] ACPI: Thermal Zone [THM] (58 C)
[    3.049386] usbcore: registered new interface driver usbfs
[    3.049415] usbcore: registered new interface driver hub
[    3.049463] usbcore: registered new device driver usb
[    3.067128] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.067145] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.067150] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.067209] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.071129] ehci_hcd 0000:00:1d.7: debug port 1
[    3.071136] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.071154] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    3.083117] USB Universal Host Controller Interface driver v3.0
[    3.112839] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.113051] usb usb1: configuration #1 chosen from 1 choice
[    3.113085] hub 1-0:1.0: USB hub found
[    3.113095] hub 1-0:1.0: 8 ports detected
[    3.192769] No dock devices found.
[    3.250057] SCSI subsystem initialized
[    3.319695] libata version 3.00 loaded.
[    3.320372] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.320384] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.320388] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.320420] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.320456] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    3.320566] usb usb2: configuration #1 chosen from 1 choice
[    3.320598] hub 2-0:1.0: USB hub found
[    3.320607] hub 2-0:1.0: 2 ports detected
[    3.424307] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.424320] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.424324] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.424352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.424391] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    3.424496] usb usb3: configuration #1 chosen from 1 choice
[    3.424531] hub 3-0:1.0: USB hub found
[    3.424539] hub 3-0:1.0: 2 ports detected
[    3.528290] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.528301] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.528306] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.528343] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.528380] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    3.528490] usb usb4: configuration #1 chosen from 1 choice
[    3.528522] hub 4-0:1.0: USB hub found
[    3.528530] hub 4-0:1.0: 2 ports detected
[    3.632366] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.632378] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.632383] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.632411] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.632448] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    3.632559] usb usb5: configuration #1 chosen from 1 choice
[    3.632592] hub 5-0:1.0: USB hub found
[    3.632600] hub 5-0:1.0: 2 ports detected
[    3.709766] Marking TSC unstable due to TSC halts in idle
[    3.844253] ohci1394 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.896985] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.903990] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.904036] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.904052] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.908089] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.968079] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.972208] b44.c:v2.0
[    3.992587] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:de:a5:e4
[    3.998018] ata_piix 0000:00:1f.2: version 2.12
[    3.998032] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.998038] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.016045] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    4.084159] Clocksource tsc unstable (delta = -493090229 ns)
[    4.152181] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.152352] scsi0 : ata_piix
[    4.152708] scsi1 : ata_piix
[    4.153782] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    4.153786] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    4.192657] usb 5-2: configuration #1 chosen from 1 choice
[    4.216954] usbcore: registered new interface driver hiddev
[    4.230993] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
[    4.231287] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-2
[    4.231307] usbcore: registered new interface driver usbhid
[    4.231310] usbhid: v2.6:USB HID core driver
[    4.317138] ata1.00: ATA-6: ST9120822A,  3.ALE, max UDMA/100
[    4.317143] ata1.00: 234441648 sectors, multi 8: LBA48 
[    4.317145] ata1.00: applying bridge limits
[    4.333630] ata1.00: configured for UDMA/100
[    4.496603] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS7, max UDMA/33
[    4.512539] ata2.00: configured for UDMA/33
[    4.512671] scsi 0:0:0:0: Direct-Access     ATA      ST9120822A       n/a  PQ: 0 ANSI: 5
[    4.513590] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS7 PQ: 0 ANSI: 5
[    4.532950] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.532999] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.553380] Driver 'sd' needs updating - please use bus_type methods
[    4.555679] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.555705] sd 0:0:0:0: [sda] Write Protect is off
[    4.555708] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.555750] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.555837] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.555859] sd 0:0:0:0: [sda] Write Protect is off
[    4.555863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.555905] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.555910]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.612793]  sda1 sda2 < sda5 sda6 >
[    4.647801] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.654415] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.654420] Uniform CD-ROM driver Revision: 3.20
[    4.654513] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.028181] PM: Starting manual resume from disk
[    5.028185] PM: Resume from partition 8:6
[    5.028188] PM: Checking hibernation image.
[    5.028378] PM: Resume from disk failed.
[    5.054397] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.054401] EXT3-fs: write access will be enabled during recovery.
[    5.184185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00027329101]
[    5.429748] kjournald starting.  Commit interval 5 seconds
[    5.429765] EXT3-fs: recovery complete.
[    5.430451] EXT3-fs: mounted filesystem with writeback data mode.
[   11.974218] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.066426] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.066594] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   12.066597] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.066600] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.353814] udevd version 124 started
[   13.178063] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.247769] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.324637] Linux agpgart interface v0.103
[   13.837971] ACPI: AC Adapter [AC] (on-line)
[   14.126248] iTCO_vendor_support: vendor-support=0
[   14.128746] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.129416] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   14.129575] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.253158] ACPI: Battery Slot [BAT0] (battery present)
[   14.253373] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   14.253896] ACPI: Lid Switch [LID]
[   14.253997] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   14.264047] ACPI: Power Button (CM) [PBTN]
[   14.264230] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   14.280030] ACPI: Sleep Button (CM) [SBTN]
[   14.336607] intel_rng: FWH not detected
[   14.425786] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   14.742008] [fglrx] Maximum main memory to use for locked dma buffers: 1897 MBytes.
[   14.742339] [fglrx]   vendor: 1002 device: 5460 count: 1
[   14.742844] [fglrx] ioport: bar 1, base 0xde00, size: 0x100
[   14.742864] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.742869] pci 0000:01:00.0: setting latency timer to 64
[   14.743566] [fglrx] PAT is enabled successfully!
[   14.743605] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   14.989172] ieee80211_crypt: registered algorithm 'NULL'
[   15.033053] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.033057] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.213969] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.213974] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.214056] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.214667] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.214715] firmware: requesting ipw2200-bss.fw
[   15.356817] sdhci: Secure Digital Host Controller Interface driver
[   15.356822] sdhci: Copyright(c) Pierre Ossman
[   15.941905] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input6
[   15.952029] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.909441] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   17.291422] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   17.333419] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   17.351985] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.492319] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   18.492576] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
[   18.620815] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   18.620821] Socket status: 30000006
[   18.620825] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   18.620833] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   18.620836] cs: IO port probe 0x2000-0x2fff: clean.
[   18.621092] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
[   18.621096] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   18.637455] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.637488] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   19.150954] cs: IO port probe 0x100-0x3af: clean.
[   19.152685] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.153411] cs: IO port probe 0x820-0x8ff: clean.
[   19.154013] cs: IO port probe 0xc00-0xcf7: clean.
[   19.154795] cs: IO port probe 0xa00-0xaff: clean.
[   19.464032] intel8x0_measure_ac97_clock: measured 55336 usecs
[   19.464036] intel8x0: clocking to 48000
[   19.466771] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[   19.466791] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[   19.469867] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[   20.753652] lp: driver loaded but no devices found
[   21.014805] Adding 3076408k swap on /dev/sda6.  Priority:-1 extents:1 across:3076408k
[   21.556468] EXT3 FS on sda5, internal journal
[   22.480352] type=1505 audit(1226613342.893:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4155
[   22.715707] type=1505 audit(1226613343.125:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4160
[   22.715982] type=1505 audit(1226613343.125:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4160
[   23.385134] ACPI: WMI: Mapper loaded
[   24.348224] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   24.432320] apm: BIOS not found.
[   24.713169] ppdev: user-space parallel port driver
[   27.200790] Bluetooth: Core ver 2.13
[   27.202875] NET: Registered protocol family 31
[   27.202882] Bluetooth: HCI device and connection manager initialized
[   27.202886] Bluetooth: HCI socket layer initialized
[   27.221339] Bluetooth: L2CAP ver 2.11
[   27.221347] Bluetooth: L2CAP socket layer initialized
[   27.249010] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.249018] Bluetooth: BNEP filters: protocol multicast
[   27.295347] Bridge firewalling registered
[   27.324207] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   27.344383] Bluetooth: SCO (Voice Link) ver 0.6
[   27.344391] Bluetooth: SCO socket layer initialized
[   27.380261] Bluetooth: RFCOMM socket layer initialized
[   27.380534] Bluetooth: RFCOMM TTY layer initialized
[   27.380543] Bluetooth: RFCOMM ver 1.10
[   31.487339] NET: Registered protocol family 17
[   32.300464] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   32.300476] [fglrx] Reserved FB block: Unshared offset:3faa000, size:44000 
[   32.300480] [fglrx] Reserved FB block: Unshared offset:3fee000, size:1000 
[   32.300484] [fglrx] Reserved FB block: Unshared offset:3fef000, size:1000 
[   32.300487] [fglrx] Reserved FB block: Unshared offset:3ff0000, size:10000 
[   65.654525] NET: Registered protocol family 10
[   65.656953] lo: Disabled Privacy Extensions
[   65.659379] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   75.984018] eth1: no IPv6 routers present
[   87.083754] ieee80211_crypt: registered algorithm 'TKIP'
```

Thanks for the responses so far.

---

### Post by ITAndrew on 2008-11-13
Was the dmesg output after the crash? I don't see anything out of the ordinary on either the output of top or dmesg. FYI Top just shows your top running processes of processor use, I don't believe it would be too helpful troubleshooting a sys crash.

---

### Post by signal_ on 2008-11-13
> Was the dmesg output after the crash?

Yes, the dmesg output was directly following the crash.  [when I opened the System Monitor.]

>  FYI Top just shows your top running processes my processor use, I don't believe it would be too helpful troubleshooting a sys crash.

Noted.

>  I don't see anything out of the ordinary on either the output of top or dmesg.

Okay...  I am pretty sure that I've done nothing out of the ordinary when this whole mess started.  I did not make any modifications via terminal and the only thing out of the ordinary was approximately 2 days ago there were some system updates that were downloaded and installed.

Last evening I also ran memtest and it said I passed.  Am I screwed here and need to reinstall?

---

### Post by ITAndrew on 2008-11-13
Your system is still running so you are not screwed. You can try reinstalling gnome-system-monitor by running:

sudo apt-get purge gnome-system-monitor

This will purge all gnome-system-monitor settings and remove the application. After run

sudo apt-get install gnome-system-monitor

Just to confirm, this only happens with system monitor? And, was the top output after the crash as well? It true, it shows that your x server is still running.

How have you been recovering from your system crash?

---

### Post by signal_ on 2008-11-13
Hi, ITAndrew, yr help is greatly appreciated.

> Your system is still running so you are not screwed. You can try reinstalling gnome-system-monitor by running:

sudo apt-get purge gnome-system-monitor

This will purge all gnome-system-monitor settings and remove the application. After run

sudo apt-get install gnome-system-monitor

Okay.  I will try this.

> Just to confirm, this only happens with system monitor?

It only happens with system monitor in a very deterministic manner: i.e. open system monitor = crash. 

>  And, was the top output after the crash as well? It true, it shows that your x server is still running.

No, I ran top when it booted up after the crash.

> 
How have you been recovering from your system crash? 

Well, I did not know about the ctrl + alt + F1 (extreme ubuntu neophyte), so I have just been holding power off, then rebooting.  Hopefully, that action is not causing more damage.


EDIT: I reinstalled gnome-system-monitor and rebooted.  Then I tried to open system monitor and it crashed once again....

---

### Post by emobrad on 2008-11-13
> 
Well, I did not know about the ctrl + alt + F1 (extreme ubuntu neophyte), so I have just been holding power off, then rebooting.  Hopefully, that action is not causing more damage.

Just holding power = BAD. If your system ever gets to the point where the above command doesn't work, don't hard reset it without trying this command. 

```
CTRL + ALT (and in rapid succession press these buttons in order) Sys Rq, R, E, S, U, I, B
```

Hopefully I didn't miss something in that command, but yeah, that's the safe way of reseting your system after a crash. Just so you don't corrupt your filesystem and whatnot.

---

### Post by theamber on 2008-11-13
> **emobrad said:**
> Just holding power = BAD. If your system ever gets to the point where the above command doesn't work, don't hard reset it without trying this command. 

```
CTRL + ALT (and in rapid succession press these buttons in order) Sys Rq, R, E, S, U, I, B
```

Hopefully I didn't miss something in that command, but yeah, that's the safe way of reseting your system after a crash. Just so you don't corrupt your filesystem and whatnot.

I have a similar problem I did hold the power button too many times I may have corrupted some files, how can I fix this.

---

### Post by ITAndrew on 2008-11-13
Are you able to get to another terminal when it crashes? (CTRL & ALT + F1 through F6)

If so you may want to try to restart the Xorg server by typing:

sudo gdm start
or
sudo startx

You may recieve a message about x is already running or GDM is already running. If it is you will want to kill the running Xorg server.

To kill X, run top, record the PID for the Xorg process.

Run: 
sudo kill 'PID'
without single quotes but the PID you recorded.

to restart it again using the above commands. (startx or gdm start) You should be at your desktop again. To avoid restarting hard restarting.

> EDIT: I reinstalled gnome-system-monitor and rebooted. Then I tried to open system monitor and it crashed once again....

Well, i definately would not recommend using the System Monitor Applet, which starts at boot.

If your xorg server crashes (Ie.. didnt have to kill it to restart it) please output your /var/log/Xorg.0.log log file.

---

### Post by theamber on 2008-11-13
At this point I am in a similar situation would it be better just reinstalling the CD again?

---

### Post by ITAndrew on 2008-11-13
> **theamber said:**
> I have a similar problem I did hold the power button too many times I may have corrupted some files, how can I fix this.

Are you still able to boot the PC? Which files are corrupted?

---

### Post by theamber on 2008-11-13
> **ITAndrew said:**
> Are you still able to boot the PC? Which files are corrupted?

Yes it boots but if I try to open a menu sometimes works other crash.
Also I cannot get enable the 3D accelerator driver that is privative.

---

### Post by theamber on 2008-11-13
Also when I installed the first time it gave me errors with the wireless. I am going to disable it from the Bios and Install it like that to see if it works better.

---

### Post by ITAndrew on 2008-11-13
Well at least its quick to reinstall (I prefer not to, although i like to play with many OSs) using the System > Administration > Create a USB Startup Disk ~ if you have a Pen Drive.

Just keep a backup of your personal files.

---

### Post by theamber on 2008-11-13
> **ITAndrew said:**
> Well at least its quick to reinstall (I prefer not to, although i like to play with many OSs) using the System > Administration > Create a USB Startup Disk ~ if you have a Pen Drive.

Just keep a backup of your personal files.
I am installing now I did see a quick message that said ignoring 4 gigabytes in the initial screen some other errors firmware and I see video corruption then a message firmware error then I got the installation window.

---

### Post by theamber on 2008-11-13
I get an error window the X server graphic interface. I think is because of the video card is not supported and the driver are privative I will continue. Well  I get the checking battery window The X server is not available said. Said restart GDM when is configured.

---

### Post by ITAndrew on 2008-11-13
> **theamber said:**
> I get an error window the X server graphic interface. I think is because of the video card is not supported and the driver are privative I will continue. Well  I get the checking battery window The X server is not available said.

What are your hardware specs?

---

### Post by theamber on 2008-11-13
> **ITAndrew said:**
> What are your hardware specs?
AMD Turion 64 I am using the 64 bit version of the 8.10. 768 RAM Laptop compaq V5000
I am trying again.

---

### Post by theamber on 2008-11-13
I can't install it anymore I get the same x sever and the checking battery window not even the 8.04. I will try last time with the 8.04

---

### Post by theamber on 2008-11-13
I can't install it if eject the 8.04 disk.

---

### Post by signal_ on 2008-11-14
I found the solution to the system crashing problem.  I am putting it here so that if anyone else experiences this crash they can search for the solution and maybe end up here:

Solution:

Read this link: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/274988]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/274988")

It basically says that if you disable backingstore from the xorg.conf then it will stop crashing.

Apparently, it is noted as a bug; however, it is a low priority since it affects a small portion of the total Ubuntu user base.

---

