---
title: "Kernel taint due to fglrx details"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by su:bhatta on 2013-08-28
Hi, I am using the Fglrx Drivers( Installed through 'Softwares & Updates', hence I didn't have to put no Certificate) for my AMD Radeon 6480 card and getting this kernel taint :
Here are some outputs:
dmesg: gives results more than 1024 lines, so couldn't get the whole, hers the last part:

```
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 14680064 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.001000] tsc: Detected 1896.635 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3793.27 BogoMIPS (lpj=1896635)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000049] AppArmor: AppArmor initialized
[    0.000051] Yama: becoming mindful.
[    0.000403] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001737] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002365] Mount-cache hash table entries: 256
[    0.002625] Initializing cgroup subsys memory
[    0.002643] Initializing cgroup subsys devices
[    0.002644] Initializing cgroup subsys freezer
[    0.002646] Initializing cgroup subsys blkio
[    0.002648] Initializing cgroup subsys perf_event
[    0.002651] Initializing cgroup subsys hugetlb
[    0.002675] tseg: 007ff00000
[    0.002677] CPU: Physical Processor ID: 0
[    0.002678] CPU: Processor Core ID: 0
[    0.002680] mce: CPU supports 6 MCE banks
[    0.002690] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.002690] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64
[    0.002690] tlb_flushall_shift: 5
[    0.002820] Freeing SMP alternatives memory: 24K (ffffffff81e59000 - ffffffff81e5f000)
[    0.004124] ACPI: Core revision 20130517
[    0.009272] ACPI: All ACPI Tables successfully acquired
[    0.041668] ftrace: allocating 27863 entries in 109 pages
[    0.062409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072416] smpboot: CPU0: AMD A4-3305M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
[    0.173960] Performance Events: AMD PMU driver.
[    0.173965] ... version:                0
[    0.173967] ... bit width:              48
[    0.173968] ... generic registers:      4
[    0.173970] ... value mask:             0000ffffffffffff
[    0.173971] ... max period:             00007fffffffffff
[    0.173973] ... fixed-purpose events:   0
[    0.173974] ... event mask:             000000000000000f
[    0.179409] NMI watchdog: Disabled lockup detectors by default for full dynticks
[    0.179415] NMI watchdog: You can reactivate it with 'sysctl -w kernel.watchdog=1'
[    0.181110] smpboot: Booting Node   0, Processors  #1
[    0.194356] Brought up 2 CPUs
[    0.194359] smpboot: Total of 2 processors activated (7586.54 BogoMIPS)
[    0.195115] devtmpfs: initialized
[    0.196670] EVM: security.selinux
[    0.196672] EVM: security.SMACK64
[    0.196673] EVM: security.capability
[    0.196777] PM: Registering ACPI NVS region [mem 0x7faba000-0x7fafcfff] (274432 bytes)
[    0.196784] PM: Registering ACPI NVS region [mem 0x7fb0c000-0x7fb1bfff] (65536 bytes)
[    0.196786] PM: Registering ACPI NVS region [mem 0x7fb3f000-0x7fb40fff] (8192 bytes)
[    0.196788] PM: Registering ACPI NVS region [mem 0x7fb42000-0x7fb4ffff] (57344 bytes)
[    0.196791] PM: Registering ACPI NVS region [mem 0x7fb77000-0x7fd79fff] (2109440 bytes)
[    0.198196] regulator-dummy: no parameters
[    0.198274] RTC time: 10:17:00, date: 08/28/13
[    0.198330] NET: Registered protocol family 16
[    0.198657] ACPI: bus type PCI registered
[    0.198661] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.198778] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.198781] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.219167] PCI: Using configuration type 1 for base access
[    0.220474] bio: create slab <bio-0> at 0
[    0.220792] ACPI: Added _OSI(Module Device)
[    0.220795] ACPI: Added _OSI(Processor Device)
[    0.220797] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.220799] ACPI: Added _OSI(Processor Aggregator Device)
[    0.222458] ACPI: EC: Look up EC in DSDT
[    0.224193] ACPI: Executed 2 blocks of module-level executable AML code
[    0.244109] ACPI: Interpreter enabled
[    0.244132] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.244147] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.244190] ACPI: (supports S0 S3 S4 S5)
[    0.244193] ACPI: Using IOAPIC for interrupt routing
[    0.244428] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.244599] ACPI: No dock devices found.
[    0.245580] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.245604] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.245837] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.245852] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.307058] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.307462] PCI host bridge to bus 0000:00
[    0.307467] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.307470] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.307473] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.307476] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.307478] pci_bus 0000:00: root bus resource [io  0x1778-0xffff]
[    0.307481] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.307483] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.307486] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xffffffff]
[    0.307496] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
[    0.307620] pci 0000:00:01.0: [1002:9649] type 00 class 0x030000
[    0.307631] pci 0000:00:01.0: reg 0x10: [mem 0xa0000000-0xafffffff pref]
[    0.307639] pci 0000:00:01.0: reg 0x14: [io  0xf000-0xf0ff]
[    0.307647] pci 0000:00:01.0: reg 0x18: [mem 0xfeb00000-0xfeb3ffff]
[    0.307697] pci 0000:00:01.0: supports D1 D2
[    0.307785] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
[    0.307795] pci 0000:00:01.1: reg 0x10: [mem 0xfeb44000-0xfeb47fff]
[    0.307854] pci 0000:00:01.1: supports D1 D2
[    0.307942] pci 0000:00:02.0: [1022:1707] type 01 class 0x060400
[    0.308007] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.308102] pci 0000:00:03.0: [1022:1708] type 01 class 0x060400
[    0.308165] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.308260] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
[    0.308322] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.308399] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.308504] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
[    0.308527] pci 0000:00:11.0: reg 0x10: [io  0xf140-0xf147]
[    0.308539] pci 0000:00:11.0: reg 0x14: [io  0xf130-0xf133]
[    0.308550] pci 0000:00:11.0: reg 0x18: [io  0xf120-0xf127]
[    0.308562] pci 0000:00:11.0: reg 0x1c: [io  0xf110-0xf113]
[    0.308573] pci 0000:00:11.0: reg 0x20: [io  0xf100-0xf10f]
[    0.308585] pci 0000:00:11.0: reg 0x24: [mem 0xfeb50000-0xfeb507ff]
[    0.308768] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
[    0.308784] pci 0000:00:12.0: reg 0x10: [mem 0xfeb4f000-0xfeb4ffff]
[    0.308981] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
[    0.309003] pci 0000:00:12.2: reg 0x10: [mem 0xfeb4e000-0xfeb4e0ff]
[    0.309099] pci 0000:00:12.2: supports D1 D2
[    0.309102] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.309245] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
[    0.309261] pci 0000:00:13.0: reg 0x10: [mem 0xfeb4d000-0xfeb4dfff]
[    0.309465] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
[    0.309488] pci 0000:00:13.2: reg 0x10: [mem 0xfeb4c000-0xfeb4c0ff]
[    0.309584] pci 0000:00:13.2: supports D1 D2
[    0.309586] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.309729] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    0.309931] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    0.309956] pci 0000:00:14.2: reg 0x10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    0.310033] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.310092] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.310174] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    0.310385] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
[    0.310477] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.310559] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
[    0.310576] pci 0000:00:14.5: reg 0x10: [mem 0xfeb4b000-0xfeb4bfff]
[    0.310770] pci 0000:00:14.7: [1022:7806] type 00 class 0x080501
[    0.310795] pci 0000:00:14.7: reg 0x10: [mem 0xfeb4a000-0xfeb4a0ff 64bit]
[    0.311004] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
[    0.311096] pci 0000:00:15.0: supports D1 D2
[    0.311162] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.311250] pci 0000:00:15.2: [1022:43a2] type 01 class 0x060400
[    0.311349] pci 0000:00:15.2: supports D1 D2
[    0.311415] pci 0000:00:15.2: System wakeup disabled by ACPI
[    0.311506] pci 0000:00:16.0: [1022:7807] type 00 class 0x0c0310
[    0.311522] pci 0000:00:16.0: reg 0x10: [mem 0xfeb49000-0xfeb49fff]
[    0.311719] pci 0000:00:16.2: [1022:7808] type 00 class 0x0c0320
[    0.311741] pci 0000:00:16.2: reg 0x10: [mem 0xfeb48000-0xfeb480ff]
[    0.311837] pci 0000:00:16.2: supports D1 D2
[    0.311839] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.311983] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    0.312087] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    0.312188] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    0.312289] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    0.312405] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    0.312504] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    0.312610] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    0.312707] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    0.312914] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.313002] pci 0000:02:00.0: [1002:6760] type 00 class 0x030000
[    0.313021] pci 0000:02:00.0: reg 0x10: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.313037] pci 0000:02:00.0: reg 0x18: [mem 0xfea20000-0xfea3ffff 64bit]
[    0.313048] pci 0000:02:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.313066] pci 0000:02:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.313113] pci 0000:02:00.0: supports D1 D2
[    0.315377] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.315398] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    0.315408] pci 0000:00:03.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.315419] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.315547] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.315567] pci 0000:03:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.315594] pci 0000:03:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.315611] pci 0000:03:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.315685] pci 0000:03:00.0: supports D1 D2
[    0.315687] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.316995] pci 0000:00:04.0: PCI bridge to [bus 03]
[    0.317016] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.317031] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.317254] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.317266] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.317268] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.317270] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.317273] pci 0000:00:14.4:   bridge window [io  0x1778-0xffff] (subtractive decode)
[    0.317276] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.317278] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.317281] pci 0000:00:14.4:   bridge window [mem 0xa0000000-0xffffffff] (subtractive decode)
[    0.317393] pci 0000:05:00.0: [168c:0032] type 00 class 0x028000
[    0.317424] pci 0000:05:00.0: reg 0x10: [mem 0xfe900000-0xfe97ffff 64bit]
[    0.317488] pci 0000:05:00.0: reg 0x30: [mem 0xfe980000-0xfe98ffff pref]
[    0.317558] pci 0000:05:00.0: supports D1 D2
[    0.317560] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.319428] pci 0000:00:15.0: PCI bridge to [bus 05]
[    0.319454] pci 0000:00:15.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.319640] pci 0000:00:15.2: PCI bridge to [bus 06-08]
[    0.319647] pci 0000:00:15.2:   bridge window [io  0xc000-0xcfff]
[    0.319652] pci 0000:00:15.2:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.319660] pci 0000:00:15.2:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.319696] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.319699] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.320273] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.320316] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.320358] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.320399] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.320442] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.320482] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.320522] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.320563] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.320603] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.320642] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.320682] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.320722] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.320762] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.320801] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.320841] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.320881] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.320920] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.320969] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.321010] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.321049] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.321089] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.321129] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.321168] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.321208] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.321248] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.321288] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.321328] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.321368] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.321407] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.321447] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.321487] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.321526] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.335447] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    0.335532] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    0.335615] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    0.335695] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    0.335761] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.335816] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.335869] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.335923] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.336226] ACPI: Enabled 2 GPEs in block 00 to 1F
[    0.336236] ACPI: \_SB_.PCI0: notify handler is installed
[    0.336321] Found 1 acpi root devices
[    0.336379] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.336577] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.336590] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.336593] vgaarb: loaded
[    0.336594] vgaarb: bridge control possible 0000:02:00.0
[    0.336595] vgaarb: no bridge control possible 0000:00:01.0
[    0.336797] SCSI subsystem initialized
[    0.336800] ACPI: bus type ATA registered
[    0.336876] libata version 3.00 loaded.
[    0.336897] ACPI: bus type USB registered
[    0.336916] usbcore: registered new interface driver usbfs
[    0.336926] usbcore: registered new interface driver hub
[    0.337002] usbcore: registered new device driver usb
[    0.337253] PCI: Using ACPI for IRQ routing
[    0.346985] PCI: pci_cache_line_size set to 64 bytes
[    0.347082] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.347085] e820: reserve RAM buffer [mem 0x7faba000-0x7fffffff]
[    0.347088] e820: reserve RAM buffer [mem 0x7fb42000-0x7fffffff]
[    0.347090] e820: reserve RAM buffer [mem 0x7ff00000-0x7fffffff]
[    0.347092] e820: reserve RAM buffer [mem 0x15f000000-0x15fffffff]
[    0.347223] NetLabel: Initializing
[    0.347225] NetLabel:  domain hash size = 128
[    0.347227] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.347239] NetLabel:  unlabeled traffic allowed by default
[    0.347384] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.347390] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.349441] Switched to clocksource hpet
[    0.356420] AppArmor: AppArmor Filesystem Enabled
[    0.356535] pnp: PnP ACPI init
[    0.356554] ACPI: bus type PNP registered
[    0.356714] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.356720] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.357163] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357576] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.357579] system 00:02: [io  0x040b] has been reserved
[    0.357582] system 00:02: [io  0x04d6] has been reserved
[    0.357585] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.357587] system 00:02: [io  0x0c14] has been reserved
[    0.357590] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.357593] system 00:02: [io  0x0c52] has been reserved
[    0.357595] system 00:02: [io  0x0c6c] has been reserved
[    0.357598] system 00:02: [io  0x0c6f] has been reserved
[    0.357601] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.357603] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.357606] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.357609] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.357612] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.357614] system 00:02: [io  0x0800-0x089f] could not be reserved
[    0.357617] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.357620] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.357623] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.357626] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.357633] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.357637] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.357640] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.357643] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.357646] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.357649] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.357652] system 00:02: [mem 0xff000000-0xffffffff] has been reserved
[    0.357655] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357669] pnp 00:03: [dma 4]
[    0.357693] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.357779] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.357806] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.357872] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.357875] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357954] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.358028] system 00:08: [io  0x1770-0x1777] has been reserved
[    0.358031] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.358117] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.358243] pnp 00:0a: Plug and Play ACPI device, IDs ETD0b00 SYN0002 PNP0f13 (active)
[    0.370647] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.370657] pnp: PnP ACPI: found 12 devices
[    0.370659] ACPI: bus type PNP unregistered
[    0.379089] pci 0000:00:02.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.379097] pci 0000:00:02.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.379101] pci 0000:00:02.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    0.379184] pci 0000:00:02.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.379187] pci 0000:00:02.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.379190] pci 0000:00:02.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.379196] pci 0000:00:02.0: BAR 14: assigned [mem 0xd0100000-0xd02fffff]
[    0.379200] pci 0000:00:02.0: BAR 15: assigned [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.379205] pci 0000:00:02.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.379208] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.379212] pci 0000:00:02.0:   bridge window [io  0x2000-0x2fff]
[    0.379217] pci 0000:00:02.0:   bridge window [mem 0xd0100000-0xd02fffff]
[    0.379221] pci 0000:00:02.0:   bridge window [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.379227] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.379230] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    0.379234] pci 0000:00:03.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.379238] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.379243] pci 0000:00:04.0: PCI bridge to [bus 03]
[    0.379246] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.379252] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.379258] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.379319] pci 0000:00:15.0: PCI bridge to [bus 05]
[    0.379325] pci 0000:00:15.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.379334] pci 0000:00:15.2: PCI bridge to [bus 06-08]
[    0.379337] pci 0000:00:15.2:   bridge window [io  0xc000-0xcfff]
[    0.379343] pci 0000:00:15.2:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.379348] pci 0000:00:15.2:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.379981] pci 0000:00:15.2: enabling device (0006 -> 0007)
[    0.380131] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.380134] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.380136] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.380138] pci_bus 0000:00: resource 7 [io  0x1778-0xffff]
[    0.380141] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.380143] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.380146] pci_bus 0000:00: resource 10 [mem 0xa0000000-0xffffffff]
[    0.380149] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.380151] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd02fffff]
[    0.380154] pci_bus 0000:01: resource 2 [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.380157] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.380159] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.380162] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.380165] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.380168] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.380170] pci_bus 0000:04: resource 4 [io  0x0000-0x03af]
[    0.380173] pci_bus 0000:04: resource 5 [io  0x03e0-0x0cf7]
[    0.380175] pci_bus 0000:04: resource 6 [io  0x03b0-0x03df]
[    0.380178] pci_bus 0000:04: resource 7 [io  0x1778-0xffff]
[    0.380181] pci_bus 0000:04: resource 8 [mem 0x000a0000-0x000bffff]
[    0.380183] pci_bus 0000:04: resource 9 [mem 0x000c0000-0x000dffff]
[    0.380186] pci_bus 0000:04: resource 10 [mem 0xa0000000-0xffffffff]
[    0.380188] pci_bus 0000:05: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.380191] pci_bus 0000:06: resource 0 [io  0xc000-0xcfff]
[    0.380194] pci_bus 0000:06: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.380197] pci_bus 0000:06: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.380238] NET: Registered protocol family 2
[    0.380479] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.380690] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.380880] TCP: Hash tables configured (established 32768 bind 32768)
[    0.380941] TCP: reno registered
[    0.380951] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.380989] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.381119] NET: Registered protocol family 1
[    0.381139] pci 0000:00:01.0: Boot video device
[    0.383489] PCI: CLS 64 bytes, default 64
[    0.383546] Trying to unpack rootfs image as initramfs...
[    0.775629] Freeing initrd memory: 16908K (ffff880035eea000 - ffff880036f6d000)
[    0.775635] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.775638] software IO TLB [mem 0x7baba000-0x7faba000] (64MB) mapped at [ffff88007baba000-ffff88007fab9fff]
[    0.775835] LVT offset 0 assigned for vector 0x400
[    0.775941] perf: AMD IBS detected (0x000000ff)
[    0.775978] Scanning for low memory corruption every 60 seconds
[    0.776459] Initialise module verification
[    0.776585] audit: initializing netlink socket (disabled)
[    0.776597] type=2000 audit(1377685020.625:1): initialized
[    0.803770] bounce pool size: 64 pages
[    0.803782] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.805623] VFS: Disk quotas dquot_6.5.2
[    0.805684] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.806284] fuse init (API version 7.22)
[    0.806430] msgmni has been set to 6853
[    0.807136] Key type asymmetric registered
[    0.807138] Asymmetric key parser 'x509' registered
[    0.807184] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.807268] io scheduler noop registered
[    0.807270] io scheduler deadline registered (default)
[    0.807293] io scheduler cfq registered
[    0.807660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.807673] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.820032] ACPI: AC Adapter [ADP1] (on-line)
[    0.820233] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.830209] ACPI: Lid Switch [LID]
[    0.830296] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.830302] ACPI: Power Button [PWRB]
[    0.830341] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.830344] ACPI: Power Button [PWRF]
[    0.830545] ACPI: acpi_idle registered with cpuidle
[    0.870161] thermal LNXTHERM:00: registered as thermal_zone0
[    0.870173] ACPI: Thermal Zone [TZ00] (63 C)
[    0.870237] GHES: HEST is not enabled!
[    0.870358] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.872423] Linux agpgart interface v0.103
[    0.875034] brd: module loaded
[    0.876123] loop: module loaded
[    0.876619] libphy: Fixed MDIO Bus: probed
[    0.876721] tun: Universal TUN/TAP device driver, 1.6
[    0.876723] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.876832] PPP generic driver version 2.4.2
[    0.876883] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.876885] ehci-pci: EHCI PCI platform driver
[    0.877129] ehci-pci 0000:00:12.2: EHCI Host Controller
[    0.877136] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.877151] QUIRK: Enable AMD PLL fix
[    0.877153] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.877215] ehci-pci 0000:00:12.2: debug port 1
[    0.877351] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb4e000
[    0.882595] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.882683] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.882690] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.882696] usb usb1: Product: EHCI Host Controller
[    0.882701] usb usb1: Manufacturer: Linux 3.11.0-2-lowlatency ehci_hcd
[    0.882705] usb usb1: SerialNumber: 0000:00:12.2
[    0.882913] hub 1-0:1.0: USB hub found
[    0.882918] hub 1-0:1.0: 5 ports detected
[    0.883291] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.883300] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.883304] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.883317] ehci-pci 0000:00:13.2: debug port 1
[    0.883424] ehci-pci 0000:00:13.2: irq 17, io mem 0xfeb4c000
[    0.888598] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.888670] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.888677] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888682] usb usb2: Product: EHCI Host Controller
[    0.888688] usb usb2: Manufacturer: Linux 3.11.0-2-lowlatency ehci_hcd
[    0.888692] usb usb2: SerialNumber: 0000:00:13.2
[    0.888887] hub 2-0:1.0: USB hub found
[    0.888891] hub 2-0:1.0: 5 ports detected
[    0.889280] ehci-pci 0000:00:16.2: EHCI Host Controller
[    0.889287] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    0.889292] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.889305] ehci-pci 0000:00:16.2: debug port 1
[    0.889408] ehci-pci 0000:00:16.2: irq 17, io mem 0xfeb48000
[    0.894586] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    0.894640] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.894647] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.894652] usb usb3: Product: EHCI Host Controller
[    0.894657] usb usb3: Manufacturer: Linux 3.11.0-2-lowlatency ehci_hcd
[    0.894662] usb usb3: SerialNumber: 0000:00:16.2
[    0.894892] hub 3-0:1.0: USB hub found
[    0.894897] hub 3-0:1.0: 4 ports detected
[    0.895111] ehci-platform: EHCI generic platform driver
[    0.895127] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.895128] ohci-platform: OHCI generic platform driver
[    0.895136] uhci_hcd: USB Universal Host Controller Interface driver
[    0.895217] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 irq 1,12
[    0.899766] ACPI: Battery Slot [BAT1] (battery present)
[    0.901049] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.901072] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.901302] mousedev: PS/2 mouse device common for all mice
[    0.901629] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.901709] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.901807] device-mapper: uevent: version 1.0.3
[    0.901956] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.901992] cpuidle: using governor ladder
[    0.902072] cpuidle: using governor menu
[    0.902091] ledtrig-cpu: registered to indicate activity on CPUs
[    0.902289] ashmem: initialized
[    0.902596] TCP: cubic registered
[    0.902702] NET: Registered protocol family 10
[    0.902954] NET: Registered protocol family 17
[    0.902965] Key type dns_resolver registered
[    0.903288] PM: Hibernation image not present or could not be loaded.
[    0.903292] Loading module verification certificates
[    0.903907] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.904640] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 8421ae1fa09e5e7365a6aae463028e3302d2c51e'
[    0.904655] registered taskstats version 1
[    0.909325] Key type trusted registered
[    0.912769] Key type encrypted registered
[    0.916684]   Magic number: 9:894:275
[    0.916721] tty tty12: hash matches
[    0.916832] rtc_cmos 00:04: setting system clock to 2013-08-28 10:17:01 UTC (1377685021)
[    0.916976] acpi-cpufreq: overriding BIOS provided _PSD data
[    0.917142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.917143] EDD information not available.
[    0.919457] Freeing unused kernel memory: 1304K (ffffffff81d13000 - ffffffff81e59000)
[    0.919463] Write protecting the kernel read-only data: 12288k
[    0.922984] Freeing unused kernel memory: 900K (ffff88000171f000 - ffff880001800000)
[    0.925943] Freeing unused kernel memory: 828K (ffff880001b31000 - ffff880001c00000)
[    0.951166] systemd-udevd[111]: starting version 204
[    1.009988] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.010006] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.010088] ahci 0000:00:11.0: version 3.0
[    1.010308] r8169 0000:03:00.0: irq 40 for MSI/MSI-X
[    1.010414] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
[    1.010584] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000061a000, 50:b7:c3:95:a1:3e, XID 0c900800 IRQ 40
[    1.010588] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.010593] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    1.010598] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.012558] scsi0 : ahci
[    1.014556] scsi1 : ahci
[    1.016830] scsi2 : ahci
[    1.016877] sdhci: Secure Digital Host Controller Interface driver
[    1.016882] sdhci: Copyright(c) Pierre Ossman
[    1.018589] scsi3 : ahci
[    1.019689] scsi4 : ahci
[    1.019805] scsi5 : ahci
[    1.019858] ata1: SATA max UDMA/133 abar m2048@0xfeb50000 port 0xfeb50100 irq 41
[    1.019861] ata2: SATA max UDMA/133 abar m2048@0xfeb50000 port 0xfeb50180 irq 41
[    1.019863] ata3: DUMMY
[    1.019864] ata4: DUMMY
[    1.019866] ata5: DUMMY
[    1.019869] ata6: SATA max UDMA/133 abar m2048@0xfeb50000 port 0xfeb50380 irq 41
[    1.019913] sdhci-pci 0000:00:14.7: SDHCI controller found [1022:7806] (rev 0)
[    1.020105] mmc0: no vqmmc regulator found
[    1.020108] mmc0: no vmmc regulator found
[    1.023232] mmc0: SDHCI controller on PCI [0000:00:14.7] using ADMA
[    1.324908] ata6: SATA link down (SStatus 0 SControl 300)
[    1.479880] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.479946] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.483219] ata2.00: ATAPI: SlimtypeDVD A DS8A8SH, KS22, max UDMA/100
[    1.486639] ata1.00: ATA-8: ST500LM012 HN-M500MBB, 2AR10002, max UDMA/133
[    1.486644] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.489723] ata2.00: configured for UDMA/100
[    1.493166] ata1.00: configured for UDMA/133
[    1.493618] scsi 0:0:0:0: Direct-Access     ATA      ST500LM012 HN-M5 2AR1 PQ: 0 ANSI: 5
[    1.493799] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.493803] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.493807] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.493877] sd 0:0:0:0: [sda] Write Protect is off
[    1.493880] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.493900] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.503434] scsi 1:0:0:0: CD-ROM            Slimtype DVD A DS8A8SH    KS22 PQ: 0 ANSI: 5
[    1.518453] sr0: scsi3-mmc drive: 8x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.518464] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.518639] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.518702] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.591960] usb 2-2: new high-speed USB device number 3 using ehci-pci
[    1.604323]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    1.605443] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.710497] usb 2-2: New USB device found, idVendor=2232, idProduct=1028
[    1.710509] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.710516] usb 2-2: Product: WebCam SC-03FFL11939N
[    1.710521] usb 2-2: Manufacturer: Image Processor
[    1.778739] tsc: Refined TSC clocksource calibration: 1896.550 MHz
[    2.779257] Switched to clocksource tsc
[    8.244416] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[   20.304103] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.448354] systemd-udevd[291]: starting version 204
[   20.658731] lp: driver loaded but no devices found
[   20.714718] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   20.714723] AMD IOMMUv2 functionality not available on this system
[   20.729375] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.729382] Disabling lock debugging due to kernel taint
[   20.756297] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[   20.775929] wmi: Mapper loaded
[   20.781579] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   20.781600] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   20.782540] acpi device:0d: registered as cooling_device2
[   20.782579] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.783401] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   20.811082] <6>[fglrx] Maximum main memory to use for locked dma buffers: 3276 MBytes.
[   20.819227] <6>[fglrx]   vendor: 1002 device: 9649 count: 1
[   20.819527] <6>[fglrx]   vendor: 1002 device: 6760 count: 2
[   20.819768] <6>[fglrx] ioport: bar 1, base 0xf000, size: 0x100
[   20.840837] <6>[fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   20.840850] pci 0000:02:00.0: enabling device (0000 -> 0003)
[   20.841095] <6>[fglrx] Kernel PAT support is enabled
[   20.841133] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 2 minors
[   20.843911] acpi device:10: registered as cooling_device3
[   20.843949] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   20.844390] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/LNXVIDEO:01/input/input5
[   20.867069] ohci-pci: OHCI PCI platform driver
[   20.867385] ohci-pci 0000:00:12.0: OHCI PCI host controller
[   20.867394] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[   20.872304] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb4f000
[   20.927304] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[   20.927311] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[   20.927314] usb usb4: Product: OHCI PCI host controller
[   20.927317] usb usb4: Manufacturer: Linux 3.11.0-2-lowlatency ohci_hcd
[   20.927319] usb usb4: SerialNumber: 0000:00:12.0
[   20.928825] hub 4-0:1.0: USB hub found
[   20.928883] hub 4-0:1.0: 5 ports detected
[   20.929145] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   20.930775] ohci-pci 0000:00:13.0: OHCI PCI host controller
[   20.930787] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[   20.931231] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb4d000
[   20.952241] cfg80211: Calling CRDA to update world regulatory domain
[   20.986548] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[   20.986554] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[   20.986558] usb usb5: Product: OHCI PCI host controller
[   20.986560] usb usb5: Manufacturer: Linux 3.11.0-2-lowlatency ohci_hcd
[   20.986562] usb usb5: SerialNumber: 0000:00:13.0
[   20.986806] hub 5-0:1.0: USB hub found
[   20.986816] hub 5-0:1.0: 5 ports detected
[   20.990284] ohci-pci 0000:00:14.5: OHCI PCI host controller
[   20.990297] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[   20.991940] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb4b000
[   21.046285] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[   21.046290] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[   21.046292] usb usb6: Product: OHCI PCI host controller
[   21.046294] usb usb6: Manufacturer: Linux 3.11.0-2-lowlatency ohci_hcd
[   21.046299] usb usb6: SerialNumber: 0000:00:14.5
[   21.046533] hub 6-0:1.0: USB hub found
[   21.046585] hub 6-0:1.0: 2 ports detected
[   21.046854] hda-intel 0000:00:01.1: Using LPIB position fix
[   21.046905] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[   21.055288] hda-intel 0000:00:01.1: Enable sync_write for stable communication
[   21.068276] ath: phy0: ASPM enabled: 0x42
[   21.068280] ath: EEPROM regdomain: 0x65
[   21.068282] ath: EEPROM indicates we should expect a direct regpair map
[   21.068285] ath: Country alpha2 being used: 00
[   21.068286] ath: Regpair used: 0x65
[   21.071327] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input6
[   21.071873] hda-intel 0000:00:14.2: Using LPIB position fix
[   21.076353] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   21.076825] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90010880000, irq=16
[   21.080815] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   21.096584] SKU: Nid=0x1d sku_cfg=0x40059a05
[   21.096589] SKU: port_connectivity=0x1
[   21.096591] SKU: enable_pcbeep=0x0
[   21.096593] SKU: check_sum=0x00000005
[   21.096594] SKU: customization=0x0000009a
[   21.096596] SKU: external_amp=0x0
[   21.096597] SKU: platform_type=0x1
[   21.096598] SKU: swap=0x0
[   21.096599] SKU: override=0x1
[   21.100593] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   21.100595]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.100597]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   21.100599]    mono: mono_out=0x0
[   21.100600]    inputs:
[   21.100602]      Internal Mic=0x19
[   21.100604]      Mic=0x18
[   21.100606] realtek: No valid SSID, checking pincfg 0x40059a05 for NID 0x1d
[   21.100608] realtek: Enabling init ASM_ID=0x9a05 CODEC_ID=10ec0269
[   21.109272] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[   21.109418] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   21.110003] ohci-pci 0000:00:16.0: OHCI PCI host controller
[   21.110012] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[   21.110984] ohci-pci 0000:00:16.0: irq 18, io mem 0xfeb49000
[   21.113915] microcode: CPU0: patch_level=0x03000025
[   21.166076] type=1400 audit(1377665241.744:2): apparmor="STATUS" operation="profile_load" parent=340 profile="unconfined" name="/sbin/dhclient" pid=354 comm="apparmor_parser"
[   21.166087] type=1400 audit(1377665241.744:3): apparmor="STATUS" operation="profile_load" parent=340 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=354 comm="apparmor_parser"
[   21.166094] type=1400 audit(1377665241.744:4): apparmor="STATUS" operation="profile_load" parent=340 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=354 comm="apparmor_parser"
[   21.166779] type=1400 audit(1377665241.745:5): apparmor="STATUS" operation="profile_replace" parent=340 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=354 comm="apparmor_parser"
[   21.166787] type=1400 audit(1377665241.745:6): apparmor="STATUS" operation="profile_replace" parent=340 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=354 comm="apparmor_parser"
[   21.167143] type=1400 audit(1377665241.745:7): apparmor="STATUS" operation="profile_replace" parent=340 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=354 comm="apparmor_parser"
[   21.169212] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[   21.169218] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[   21.169221] usb usb7: Product: OHCI PCI host controller
[   21.169223] usb usb7: Manufacturer: Linux 3.11.0-2-lowlatency ohci_hcd
[   21.169256] usb usb7: SerialNumber: 0000:00:16.0
[   21.179560] hub 7-0:1.0: USB hub found
[   21.179618] hub 7-0:1.0: 4 ports detected
[   21.293795] microcode: CPU0: new patch_level=0x03000027
[   21.293844] microcode: CPU1: patch_level=0x03000025
[   21.293863] microcode: CPU1: new patch_level=0x03000027
[   21.294002] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   21.307865] kvm: Nested Virtualization enabled
[   21.307870] kvm: Nested Paging enabled
[   21.347634] samsung_laptop: detected SABI interface: SwSmi@
[   21.347635] samsung_laptop: Backlight controlled by ACPI video driver
[   23.033955] [sched_delayed] sched: RT throttling activated
[   24.162074] systemd-udevd[434]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.1': No such file or directory
[   24.182596] Linux video capture interface: v2.00
[   24.201673] usb 4-5: new low-speed USB device number 2 using ohci-pci
[   24.207339] uvcvideo: Found UVC 1.00 device WebCam SC-03FFL11939N (2232:1028)
[   24.210397] input: WebCam SC-03FFL11939N as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input9
[   24.210800] usbcore: registered new interface driver uvcvideo
[   24.210802] USB Video Class driver (1.1.1)
[   24.323161] systemd-udevd[469]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:14.5/usb6': No such file or directory
[   24.353903] systemd-udevd[477]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:14.5/usb6/6-0:1.0': No such file or directory
[   24.355952] systemd-udevd[479]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:16.0/usb7': No such file or directory
[   24.356791] usb 4-5: New USB device found, idVendor=093a, idProduct=2510
[   24.356798] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   24.356801] usb 4-5: Product: USB OPTICAL MOUSE
[   24.356803] usb 4-5: Manufacturer: PIXART
[   24.357869] systemd-udevd[474]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0': No such file or directory
[   24.366901] systemd-udevd[482]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:16.0/usb7/7-0:1.0': No such file or directory
[   24.368413] systemd-udevd[483]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4': No such file or directory
[   24.374017] systemd-udevd[485]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-5': No such file or directory
[   24.375794] systemd-udevd[484]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-0:1.0': No such file or directory
[   24.381364] systemd-udevd[489]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0': No such file or directory
[   24.389239] hidraw: raw HID events driver (C) Jiri Kosina
[   24.397314] usbcore: registered new interface driver usbhid
[   24.397319] usbhid: USB HID core driver
[   24.403076] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input10
[   24.405965] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:12.0-5/input0
[   24.525384] cfg80211: World regulatory domain updated:
[   24.525391] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.525394] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.525396] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.525398] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.525400] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.525402] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.590060] usb 5-1: new full-speed USB device number 2 using ohci-pci
[   24.739915] usb 5-1: New USB device found, idVendor=0cf3, idProduct=3004
[   24.739928] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   24.739935] usb 5-1: Product: Bluetooth USB Host Controller
[   24.739940] usb 5-1: Manufacturer: Atheros Communications
[   24.739945] usb 5-1: SerialNumber: Alaska Day 2006
[   24.742078] systemd-udevd[498]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-1': No such file or directory
[   24.745261] systemd-udevd[500]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0': No such file or directory
[   24.754608] Bluetooth: Core ver 2.16
[   24.754922] NET: Registered protocol family 31
[   24.754926] Bluetooth: HCI device and connection manager initialized
[   24.754937] Bluetooth: HCI socket layer initialized
[   24.754940] Bluetooth: L2CAP socket layer initialized
[   24.754948] Bluetooth: SCO socket layer initialized
[   24.759323] usbcore: registered new interface driver btusb
[   24.761752] usbcore: registered new interface driver ath3k
[   25.050410] input: PS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input11
[   26.730935] init: udev-fallback-graphics main process (529) terminated with status 1
[   26.877946] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro
[   27.269700] init: failsafe main process (613) killed by TERM signal
[   27.530976] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.530982] Bluetooth: BNEP filters: protocol multicast
[   27.530995] Bluetooth: BNEP socket layer initialized
[   27.555121] Bluetooth: RFCOMM TTY layer initialized
[   27.555139] Bluetooth: RFCOMM socket layer initialized
[   27.555141] Bluetooth: RFCOMM ver 1.11
[   27.818476] type=1400 audit(1377665248.396:8): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/sbin/dhclient" pid=754 comm="apparmor_parser"
[   27.818489] type=1400 audit(1377665248.396:9): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=754 comm="apparmor_parser"
[   27.818496] type=1400 audit(1377665248.396:10): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=754 comm="apparmor_parser"
[   27.819308] type=1400 audit(1377665248.397:11): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=754 comm="apparmor_parser"
[   27.819315] type=1400 audit(1377665248.397:12): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=754 comm="apparmor_parser"
[   27.819643] type=1400 audit(1377665248.397:13): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=754 comm="apparmor_parser"
[   27.824361] type=1400 audit(1377665248.402:14): apparmor="STATUS" operation="profile_load" parent=748 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=753 comm="apparmor_parser"
[   27.824373] type=1400 audit(1377665248.402:15): apparmor="STATUS" operation="profile_load" parent=748 profile="unconfined" name="chromium_browser" pid=753 comm="apparmor_parser"
[   27.824866] type=1400 audit(1377665248.402:16): apparmor="STATUS" operation="profile_replace" parent=748 profile="unconfined" name="chromium_browser" pid=753 comm="apparmor_parser"
[   27.832283] type=1400 audit(1377665248.410:17): apparmor="STATUS" operation="profile_load" parent=748 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=757 comm="apparmor_parser"
[   27.935116] init: avahi-cups-reload main process (762) terminated with status 1
[   27.975076] ppdev: user-space parallel port driver
[   29.174738] r8169 0000:03:00.0 eth0: link down
[   29.174980] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.177175] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.219628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.220854] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.513265] vgaarb: this pci device is not a vga device
[   29.513298] vgaarb: this pci device is not a vga device
[   29.513313] vgaarb: this pci device is not a vga device
[   29.513328] vgaarb: this pci device is not a vga device
[   29.513388] vgaarb: this pci device is not a vga device
[   29.513407] vgaarb: this pci device is not a vga device
[   29.513422] vgaarb: this pci device is not a vga device
[   29.513437] vgaarb: this pci device is not a vga device
[   29.513453] vgaarb: this pci device is not a vga device
[   29.513470] vgaarb: this pci device is not a vga device
[   29.513487] vgaarb: this pci device is not a vga device
[   29.513503] vgaarb: this pci device is not a vga device
[   29.513520] vgaarb: this pci device is not a vga device
[   29.513535] vgaarb: this pci device is not a vga device
[   29.513551] vgaarb: this pci device is not a vga device
[   29.513568] vgaarb: this pci device is not a vga device
[   29.513584] vgaarb: this pci device is not a vga device
[   29.513601] vgaarb: this pci device is not a vga device
[   29.513619] vgaarb: this pci device is not a vga device
[   29.513636] vgaarb: this pci device is not a vga device
[   29.513654] vgaarb: this pci device is not a vga device
[   29.513688] vgaarb: this pci device is not a vga device
[   29.513706] vgaarb: this pci device is not a vga device
[   29.513725] vgaarb: this pci device is not a vga device
[   29.513743] vgaarb: this pci device is not a vga device
[   29.513762] vgaarb: this pci device is not a vga device
[   29.513780] vgaarb: this pci device is not a vga device
[   29.513799] vgaarb: this pci device is not a vga device
[   29.513837] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   29.513871] vgaarb: this pci device is not a vga device
[   29.513891] vgaarb: this pci device is not a vga device
[   30.006670] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   30.007535] <6>[fglrx] Firegl kernel thread PID: 1188
[   30.007895] <6>[fglrx] Firegl kernel thread PID: 1189
[   30.008022] <6>[fglrx] Firegl kernel thread PID: 1190
[   30.008210] <6>[fglrx] IRQ 43 Enabled
[   30.011833] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   30.011836] <6>[fglrx] Reserved FB block: Unshared offset:fc38000, size:3c8000 
[   30.011838] <6>[fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
[   31.137396] wlan0: authenticate with 00:1b:da:49:66:7f
[   31.158690] wlan0: send auth to 00:1b:da:49:66:7f (try 1/3)
[   31.161068] wlan0: authenticated
[   31.161390] ath9k 0000:05:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   31.161398] ath9k 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.161400] ath9k 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.161910] wlan0: associate with 00:1b:da:49:66:7f (try 1/3)
[   31.164512] wlan0: RX AssocResp from 00:1b:da:49:66:7f (capab=0x411 status=0 aid=1)
[   31.164775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.164980] wlan0: associated
[   32.019049] fglrx_pci 0000:02:00.0: irq 44 for MSI/MSI-X
[   32.019959] <6>[fglrx] Firegl kernel thread PID: 1195
[   32.020090] <6>[fglrx] Firegl kernel thread PID: 1196
[   32.020195] <6>[fglrx] Firegl kernel thread PID: 1197
[   32.020514] <6>[fglrx] IRQ 44 Enabled
[   32.069593] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   32.069598] <6>[fglrx] Reserved FB block: Unshared offset:f938000, size:3c8000 
[   32.069600] <6>[fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   32.088416] <6>[fglrx] ATIF platform detected with notification ID: 0x81
```

sudo lshw:

 ```
description: Laptop
    product: 305E4Z/305E5Z/305E7Z (To be filled by O.E.M.)
    vendor: SAMSUNG ELECTRONICS CO., LTD.
    version: 01TK
    serial: J9TS91SD200962
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=laptop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=40A70ABA-2D6F-E211-AA28-A856048627F8
  *-core
       description: Motherboard
       product: 305E4Z/305E4Z
       vendor: SAMSUNG ELECTRONICS CO., LTD.
       physical id: 0
       version: 01TK
       serial: 123490EN400015
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 01TK.ME30.20121023.SKK
          date: 10/23/2012
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: AD73I1C1674EV
             vendor: A-DATA
             physical id: 1
             serial: FBE20000
             slot: A1_DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L2 cache
          physical id: 1c
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cache:1
          description: L1 cache
          physical id: 1d
          slot: L1 CACHE
          size: 256KiB
          capacity: 256KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cpu
          description: CPU
          product: AMD A4-3305M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1f
          bus info: cpu@0
          version: AMD A4-3305M APU with Radeon(tm) HD Graphics
          slot: P0
          size: 800MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 12h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: Sumo [Radeon HD 6480G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:43 memory:a0000000-afffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:d0100000-d02fffff ioport:d0300000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:fea00000-feafffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Seymour [Radeon HD 6400M/7400M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:44 memory:b0000000-bfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff
        *-pci:2
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 50:b7:c3:95:a1:3e
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:41 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb50000-feb507ff
        *-usb:0
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4f000-feb4ffff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4e000-feb4e0ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4d000-feb4dfff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4c000-feb4c0ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb40000-feb43fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4b000-feb4bfff
        *-generic
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 00
             width: 64 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:feb4a000-feb4a0ff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fe900000-fe9fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 50:b7:c3:f6:45:cb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.11.0-2-lowlatency firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fe900000-fe97ffff memory:fe980000-fe98ffff
        *-pci:5
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fe800000-fe8fffff ioport:c0000000(size=268435456)
        *-usb:5
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb49000-feb49fff
        *-usb:6
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb48000-feb480ff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LM012 HN-M5
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AR1
             serial: S2RSJ9ED135127
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=a33b6c03
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 82c5819d-4dae-8442-ae7b-c8923e512bb6
                size: 25GiB
                capacity: 25GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-06-08 00:30:08 filesystem=ntfs label=MicrosoftAte modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 440GiB
                capacity: 440GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 380GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 3909MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 9765MiB
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 9767MiB
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 14GiB
              *-logicalvolume:5
                   description: Linux filesystem partition
                   physical id: a
                   logical name: /dev/sda10
                   lo description: Laptop
    product: 305E4Z/305E5Z/305E7Z (To be filled by O.E.M.)
    vendor: SAMSUNG ELECTRONICS CO., LTD.
    version: 01TK
    serial: J9TS91SD200962
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=laptop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=40A70ABA-2D6F-E211-AA28-A856048627F8
  *-core
       description: Motherboard
       product: 305E4Z/305E4Z
       vendor: SAMSUNG ELECTRONICS CO., LTD.
       physical id: 0
       version: 01TK
       serial: 123490EN400015
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 01TK.ME30.20121023.SKK
          date: 10/23/2012
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: AD73I1C1674EV
             vendor: A-DATA
             physical id: 1
             serial: FBE20000
             slot: A1_DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L2 cache
          physical id: 1c
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cache:1
          description: L1 cache
          physical id: 1d
          slot: L1 CACHE
          size: 256KiB
          capacity: 256KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
     *-cpu
          description: CPU
          product: AMD A4-3305M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1f
          bus info: cpu@0
          version: AMD A4-3305M APU with Radeon(tm) HD Graphics
          slot: P0
          size: 800MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 12h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: Sumo [Radeon HD 6480G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:43 memory:a0000000-afffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:d0100000-d02fffff ioport:d0300000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:fea00000-feafffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Seymour [Radeon HD 6400M/7400M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:44 memory:b0000000-bfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff
        *-pci:2
             description: PCI bridge
             product: Family 12h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 50:b7:c3:95:a1:3e
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:41 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb50000-feb507ff
        *-usb:0
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4f000-feb4ffff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4e000-feb4e0ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4d000-feb4dfff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb4c000-feb4c0ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb40000-feb43fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb4b000-feb4bfff
        *-generic
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 00
             width: 64 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:feb4a000-feb4a0ff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fe900000-fe9fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 50:b7:c3:f6:45:cb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.11.0-2-lowlatency firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fe900000-fe97ffff memory:fe980000-fe98ffff
        *-pci:5
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fe800000-fe8fffff ioport:c0000000(size=268435456)
        *-usb:5
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb49000-feb49fff
        *-usb:6
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb48000-feb480ff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LM012 HN-M5
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AR1
             serial: S2RSJ9ED135127
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=a33b6c03
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 82c5819d-4dae-8442-ae7b-c8923e512bb6
                size: 25GiB
                capacity: 25GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-06-08 00:30:08 filesystem=ntfs label=MicrosoftAte modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 440GiB
                capacity: 440GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 380GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 3909MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 9765MiB
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 9767MiB
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 14GiB
              *-logicalvolume:5
                   description: Linux filesystem partition
                   physical id: a
                   logical name: /dev/sda10
                   logical name: /
                   capacity: 23GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A DS8A8SH
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KS22
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodiscgical name: /
                   capacity: 23GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A DS8A8SH
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KS22
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

output of: lspci -tvv 
```
-[0000:00]-+-00.0  Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
           +-01.0  Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G]
           +-01.1  Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
           +-02.0-[01]--
           +-03.0-[02]----00.0  Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
           +-04.0-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-11.0  Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
           +-12.0  Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller
           +-12.2  Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller
           +-13.0  Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller
           +-13.2  Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller
           +-14.0  Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller
           +-14.2  Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller
           +-14.3  Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge
           +-14.4-[04]--
           +-14.5  Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller
           +-14.7  Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
           +-15.0-[05]----00.0  Qualcomm Atheros AR9485 Wireless Network Adapter
           +-15.2-[06-08]--
           +-16.0  Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller
           +-16.2  Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller
           +-18.0  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0
           +-18.1  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
           +-18.2  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
           +-18.3  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
           +-18.4  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
           +-18.5  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
           +-18.6  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
           \-18.7  Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7

```

---

### Post by Crusty Old Fart on 2013-08-28
Here's a quick way to just see all the warnings, failures, taints, and disables in dmesg:
```

dmesg | grep -iE 'warn|fail|taint|disa'

```
Both of these look okay:
```

sudo lshw
lspci -tvv

```

---

### Post by su:bhatta on 2013-08-28
I've been getting this usb-db messages on each start up, no idea why( my usb optical mouse works ok though). Using UStudio, development release, kernel 3.11.0-2 lowlatency:

```
 dmesg | grep -iE 'warn|fail|taint|disa'
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20130517/tbfadt-603)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.179409] NMI watchdog: Disabled lockup detectors by default for full dynticks
[    0.308399] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.310092] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.310477] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.311162] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.311415] pci 0000:00:15.2: System wakeup disabled by ACPI
[    0.319696] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.776585] audit: initializing netlink socket (disabled)
[    1.010006] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.729375] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.729382] Disabling lock debugging due to kernel taint
[   20.756297] fglrx: module verification failed: signature and/or required key missing - tainting kernel
[   24.162074] systemd-udevd[434]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.1': No such file or directory
[   24.323161] systemd-udevd[469]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:14.5/usb6': No such file or directory
[   24.353903] systemd-udevd[477]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:14.5/usb6/6-0:1.0': No such file or directory
[   24.355952] systemd-udevd[479]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:16.0/usb7': No such file or directory
[   24.357869] systemd-udevd[474]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0': No such file or directory
[   24.366901] systemd-udevd[482]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:16.0/usb7/7-0:1.0': No such file or directory
[   24.368413] systemd-udevd[483]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4': No such file or directory
[   24.374017] systemd-udevd[485]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-5': No such file or directory
[   24.375794] systemd-udevd[484]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-0:1.0': No such file or directory
[   24.381364] systemd-udevd[489]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0': No such file or directory
[   24.742078] systemd-udevd[498]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-1': No such file or directory
[   24.745261] systemd-udevd[500]: failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0': No such file or directory
[   27.269700] init: failsafe main process (613) killed by TERM signal
[   31.161390] ath9k 0000:05:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   31.161398] ath9k 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.161400] ath9k 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP

```

---

### Post by Crusty Old Fart on 2013-08-28
I should tell you that I am no expert when it comes to fixing kernel problems. Some things may LOOK like problems, but don't end up having a detrimental effect.
For example, the output from the same command on my machine looks like this:
```

dmesg | grep -iE 'warn|fail|taint|disa'
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.005105] CPU: Hyper-Threading is disabled
[    0.107986] pci 0000:00:1d.7: PME# disabled
[    0.108069] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.109395] pci 0000:02:08.0: PME# disabled
[    0.117264] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.124001] pnp 00:05: io resource (0x10-0x1f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x22-0x3f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x44-0x5f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x62-0x63) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x65-0x6f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x72-0x7f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x80-0x80) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x84-0x86) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124001] pnp 00:05: io resource (0x88-0x88) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124067] pnp 00:05: io resource (0x8c-0x8e) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124136] pnp 00:05: io resource (0x90-0x9f) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124205] pnp 00:05: io resource (0xa2-0xbf) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.124274] pnp 00:05: io resource (0xe0-0xef) overlaps 0000:02:01.0 BAR 1 (0x0-0xff), disabling
[    0.127817] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:02:01.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.127889] pnp 00:0b: mem resource (0xc0000-0xdffff) overlaps 0000:02:01.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.127961] pnp 00:0b: mem resource (0xe0000-0xfffff) overlaps 0000:02:01.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.128032] pnp 00:0b: mem resource (0x100000-0x7fffffff) overlaps 0000:02:01.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.128758] PnPBIOS: Disabled by ACPI PNP
[    0.164281] pci 0000:00:01.0:   IO window: disabled
[    0.168117] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.168764] audit: initializing netlink socket (disabled)
[    0.311615] i8042: PNP detection disabled
[    0.325844] lo: Disabled Privacy Extensions
[    0.326693] PM: Resume from disk failed.
[    1.375241] e100 0000:02:08.0: PME# disabled
[   30.248763] intel_rng: don't want to disable this in firmware setup, and if

```
My machine has been running like this for about four years. Every once in a while, my mouse pointer gets trapped at the boundary between my dual monitors and moves back and forth at high frequency between the two screens. When that happens. the whole machine locks up and I have to physically power cycle it in order to reboot. It's one of those annoying, intermittent failures that happens about four or five times a month. I have no idea what causes it. Everything else works great.

You wrote that you aren't having any big problems. So, I wouldn't worry about too much about the dmesg output you're getting, especially considering that you're running alpha software. That's great.

As far as the usb-db messages are concerned: I have no idea. Perhaps the system is looking at a whole bunch of usb ports on your mother board that have nothing attached to them. If that's the case, then it's really no problem at all. But I can't say for sure.

In general, as far as I can tell, things look pretty good.

Nice meeting you, Bhatta.

Have fun,

Crusty

---

### Post by su:bhatta on 2013-08-28
Hey! Thanks for the time Crusty! 

Yeah, I am also not that bothered, in fact my system is doing fine, just wanted to make sure there is nothing major! 

See you around.

Am closing the thread!

---

### Post by deadflowr on 2013-08-28
You'll see kernel taint anytime you have closed source drivers/modules on your system.
It basically means the kernel developers won't do anything about it if a problem occurs, since they don't have access to the code.

---

### Post by su:bhatta on 2013-08-28
Thanks for the revert! 

Didn't get time today, was meaning to read up about this 'Kernel taint' thing.

Also would like to add that, unfortunately with my current laptop i've no choice but to run AMD Fglrx drivers as the open-source drivers cannot give right screen resolution, refresh rate, colors etc!

---

### Post by Crusty Old Fart on 2013-08-28
> **deadflowr said:**
> You'll see kernel taint anytime you have closed source drivers/modules on your system.
It basically means the kernel developers won't do anything about it if a problem occurs, since they don't have access to the code.
I was beginning to suspect that to be the case, after seeing kernel taints associated with proprietary driver installations a few times.
Thanks for taking the time to confirm my suspicions here.

---

