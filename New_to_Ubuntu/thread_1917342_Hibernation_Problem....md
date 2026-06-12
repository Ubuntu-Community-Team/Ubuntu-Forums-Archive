---
title: "Hibernation Problem..."
date: 2012-01-29
forum: New to Ubuntu
---

### Post by chughes27 on 2012-01-29
I'm having a problem with the hibernation feature in my Ubuntu 11.10 install. I hit the hibernate button and close the lid of my laptop, but even after ten minutes I can still hear the CPU fan going and the screen doesn't turn off. If I could get this solved that would be awesome becaus I would like to be able to let my computer hibernate.

---

### Post by dixonstalbert on 2012-01-29
this might be related to your low disk space problem.

you need several gig for the hibernate file. 

Things you can try is disconnect any peripherals, reboot then try hibernation with no programs running. this might tell where the problem is.

Search on your laptop model name to see if it is a known hardware problem.

(linux hibernation is getting very good except for ibm thinkpads which may require some extra work to function)

---

### Post by chughes27 on 2012-01-29
I don't think it could be a problem with my laptop itself, because I can do hibernation on my Windows XP just fine.

---

### Post by oscarivera9 on 2012-01-30
Windows XP and Ubuntu 11.10 are two completely different things.
I could never get my PC that came with Windows XP to hibernate with Ubuntu 10.04 or 10.10, and when I updated to 11.04, I had to revert back to 10.10 because my power supply couldn't handle the demands from 11.04.  Since then, I have built a new PC which is currently running Ubuntu 11.10 with no problem whatsoever (at least not with the Suspend)
As far as your problem: for now (until we figure out what the REAL problem is) you should try to set your computer to Suspend instead of Hibernate.
> 
dixonstalbert              **Re: Hibernation Problem...**
         this might be related to your low disk space problem.It's true that Hibernation requires a lot of disk space, but I believe that Suspend doesn't require as much.  I always put my computer on Suspend rather than Hibernate
It's not a fix to your problem but at least it's a temporary solution (if it works).  Post what kind of hardware you are using so that we can better help you with your problem.


:confused:

---

### Post by Toz on 2012-01-30
See: [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume") for debugging information.

At a bare minimum, please provide the make/model of your computer and the results of the following commands:
```

dmesg
cat /proc/cmdline
cat /etc/initramfs-tools/conf.d/resume

```

---

### Post by chughes27 on 2012-02-01
Entering "dmesg" produced this:

[    0.320595] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.320603] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.320764] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.320776] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.320786] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.320797] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.320807] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.320817] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.320827] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.320838] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.320850] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.321548] pnp 00:02: [io  0x0000-0x001f]
[    0.321557] pnp 00:02: [io  0x0081-0x0091]
[    0.321565] pnp 00:02: [io  0x0093-0x009f]
[    0.321573] pnp 00:02: [io  0x00c0-0x00df]
[    0.321581] pnp 00:02: [dma 4]
[    0.321725] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.321788] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.321936] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.322209] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.322413] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.322427] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.322475] pnp 00:05: [io  0x00f0]
[    0.322501] pnp 00:05: [irq 13]
[    0.322637] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322687] pnp 00:06: [io  0x002e-0x002f]
[    0.322696] pnp 00:06: [io  0x004e-0x004f]
[    0.322703] pnp 00:06: [io  0x0061]
[    0.322710] pnp 00:06: [io  0x0063]
[    0.322717] pnp 00:06: [io  0x0065]
[    0.322724] pnp 00:06: [io  0x0067]
[    0.322732] pnp 00:06: [io  0x0070]
[    0.322740] pnp 00:06: [io  0x0080]
[    0.322748] pnp 00:06: [io  0x0092]
[    0.322756] pnp 00:06: [io  0x00b2-0x00b3]
[    0.322766] pnp 00:06: [io  0x0680-0x069f]
[    0.322774] pnp 00:06: [io  0x0800-0x080f]
[    0.322782] pnp 00:06: [io  0x1000-0x107f]
[    0.322790] pnp 00:06: [io  0x1180-0x11bf]
[    0.322798] pnp 00:06: [io  0x1640-0x164f]
[    0.323017] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.323028] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.323038] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.323049] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.323058] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.323071] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.323198] pnp 00:07: [io  0x06a0-0x06af]
[    0.323208] pnp 00:07: [io  0x06b0-0x06ff]
[    0.323406] system 00:07: [io  0x06a0-0x06af] has been reserved
[    0.323419] system 00:07: [io  0x06b0-0x06ff] has been reserved
[    0.323432] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.323474] pnp 00:08: [io  0x0070-0x0077]
[    0.323496] pnp 00:08: [irq 8]
[    0.323643] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.323689] pnp 00:09: [io  0x0060]
[    0.323697] pnp 00:09: [io  0x0064]
[    0.323713] pnp 00:09: [irq 1]
[    0.323871] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323916] pnp 00:0a: [irq 12]
[    0.324104] pnp 00:0a: Plug and Play ACPI device, IDs SYN1302 PNP0f13 (active)
[    0.324193] pnp: PnP ACPI: found 11 devices
[    0.324200] ACPI: ACPI bus type pnp unregistered
[    0.324210] PnPBIOS: Disabled by ACPI PNP
[    0.365533] PCI: max bus depth: 1 pci_try_num: 2
[    0.365599] pci 0000:02:00.0: BAR 6: assigned [mem 0xf6020000-0xf603ffff pref]
[    0.365611] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.365622] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.365635] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.365648] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf9ffffff 64bit pref]
[    0.365664] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.365674] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.365688] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf3ffffff]
[    0.365701] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.365716] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.365723] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.365735] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.365746] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.365807] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.365821] pci 0000:00:1c.0: setting latency timer to 64
[    0.365865] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.365878] pci 0000:00:1c.2: setting latency timer to 64
[    0.365899] pci 0000:00:1e.0: setting latency timer to 64
[    0.365913] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.365923] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.365934] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.365944] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.365954] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.365963] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.365972] pci_bus 0000:00: resource 10 [mem 0x40000000-0xfebfffff]
[    0.365982] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.365991] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf1ffffff]
[    0.366000] pci_bus 0000:02: resource 2 [mem 0xf6000000-0xf9ffffff 64bit pref]
[    0.366010] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.366019] pci_bus 0000:03: resource 1 [mem 0xf2000000-0xf3ffffff]
[    0.366029] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.366039] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.366048] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.366056] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.366066] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.366075] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.366084] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.366093] pci_bus 0000:04: resource 10 [mem 0x40000000-0xfebfffff]
[    0.366213] NET: Registered protocol family 2
[    0.366412] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.367305] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.368503] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.369090] TCP: Hash tables configured (established 131072 bind 65536)
[    0.369106] TCP reno registered
[    0.369128] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.369159] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.369488] NET: Registered protocol family 1
[    0.369541] pci 0000:00:02.0: Boot video device
[    0.369727] PCI: CLS 64 bytes, default 64
[    0.369741] Simple Boot Flag at 0x38 set to 0x1
[    0.370837] audit: initializing netlink socket (disabled)
[    0.370866] type=2000 audit(1328048783.368:1): initialized
[    0.431372] highmem bounce pool size: 64 pages
[    0.431391] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.438543] VFS: Disk quotas dquot_6.5.2
[    0.438784] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.441454] fuse init (API version 7.16)
[    0.441827] msgmni has been set to 1703
[    0.443167] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.443309] io scheduler noop registered
[    0.443317] io scheduler deadline registered
[    0.443383] io scheduler cfq registered (default)
[    0.443734] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.443826] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.443980] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.444100] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.444366] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.444468] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.444668] intel_idle: MWAIT substates: 0x20220
[    0.444685] intel_idle: v0.4 model 0x1C
[    0.444691] intel_idle: lapic_timer_reliable_states 0x2
[    0.444710] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.445335] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.447192] ACPI: AC Adapter [AC] (off-line)
[    0.448366] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.448427] ACPI: Lid Switch [LID0]
[    0.448602] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.448618] ACPI: Power Button [PWRB]
[    0.448767] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.448781] ACPI: Sleep Button [SLPB]
[    0.448970] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.448984] ACPI: Power Button [PWRF]
[    0.449753] ACPI: Fan [FAN0] (off)
[    0.449797] ACPI: acpi_idle yielding to intel_idle
[    0.464361] thermal LNXTHERM:00: registered as thermal_zone0
[    0.464372] ACPI: Thermal Zone [TZ0] (52 C)
[    0.465868] thermal LNXTHERM:01: registered as thermal_zone1
[    0.465878] ACPI: Thermal Zone [TZ1] (45 C)
[    0.469161] thermal LNXTHERM:02: registered as thermal_zone2
[    0.469171] ACPI: Thermal Zone [TZ2] (40 C)
[    0.469255] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.469349] ERST: Table is not found!
[    0.469574] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.470587] isapnp: Scanning for PnP cards...
[    0.497382] ACPI: Battery Slot [CMB0] (battery present)
[    0.826484] isapnp: No Plug & Play device found
[    0.949036] Freeing initrd memory: 13320k freed
[    0.979843] Linux agpgart interface v0.103
[    0.980001] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    0.980209] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.980385] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.980601] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.983773] brd: module loaded
[    0.985409] loop: module loaded
[    0.986743] Fixed MDIO Bus: probed
[    0.986817] PPP generic driver version 2.4.2
[    0.986945] tun: Universal TUN/TAP device driver, 1.6
[    0.986950] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.987169] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.987241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.987279] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.987287] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.987394] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.987435] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.987453] ehci_hcd 0000:00:1d.7: debug port 1
[    0.991334] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.991370] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4344000
[    1.004073] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.004528] hub 1-0:1.0: USB hub found
[    1.004541] hub 1-0:1.0: 8 ports detected
[    1.004711] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.004749] uhci_hcd: USB Universal Host Controller Interface driver
[    1.004825] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.004841] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.004849] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.004952] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.004996] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.005313] hub 2-0:1.0: USB hub found
[    1.005325] hub 2-0:1.0: 2 ports detected
[    1.005477] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.005492] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.005500] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.005616] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.005674] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.005977] hub 3-0:1.0: USB hub found
[    1.005989] hub 3-0:1.0: 2 ports detected
[    1.006123] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.006138] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.006145] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.006238] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.006294] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.006599] hub 4-0:1.0: USB hub found
[    1.006611] hub 4-0:1.0: 2 ports detected
[    1.006762] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.006777] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.006785] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.006889] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.006950] uhci_hcd 0000:00:1d.3: irq 21, io base 0x00001880
[    1.007258] hub 5-0:1.0: USB hub found
[    1.007270] hub 5-0:1.0: 2 ports detected
[    1.007541] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.011587] i8042: Detected active multiplexing controller, rev 1.1
[    1.012941] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.012964] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.013049] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.013117] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.013183] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.013498] mousedev: PS/2 mouse device common for all mice
[    1.013978] rtc_cmos 00:08: RTC can wake from S4
[    1.014176] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.014219] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.014480] device-mapper: uevent: version 1.0.3
[    1.014695] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.014782] EISA: Probing bus 0 at eisa.0
[    1.014788] EISA: Cannot allocate resource for mainboard
[    1.014795] Cannot allocate resource for EISA slot 1
[    1.014800] Cannot allocate resource for EISA slot 2
[    1.014806] Cannot allocate resource for EISA slot 3
[    1.014811] Cannot allocate resource for EISA slot 4
[    1.014817] Cannot allocate resource for EISA slot 5
[    1.014822] Cannot allocate resource for EISA slot 6
[    1.014828] Cannot allocate resource for EISA slot 7
[    1.014833] Cannot allocate resource for EISA slot 8
[    1.014838] EISA: Detected 0 cards.
[    1.014857] cpufreq-nforce2: No nForce2 chipset.
[    1.015027] cpuidle: using governor ladder
[    1.015309] cpuidle: using governor menu
[    1.015314] EFI Variables Facility v0.08 2004-May-17
[    1.016031] TCP cubic registered
[    1.016447] NET: Registered protocol family 10
[    1.017827] NET: Registered protocol family 17
[    1.017876] Registering the dns_resolver key type
[    1.017929] Using IPI No-Shortcut mode
[    1.018186] PM: Hibernation image not present or could not be loaded.
[    1.018217] registered taskstats version 1
[    1.022401] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.036635]   Magic number: 12:9:453
[    1.036795] rtc_cmos 00:08: setting system clock to 2012-01-31 22:26:24 UTC (1328048784)
[    1.037636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.037641] EDD information not available.
[    1.037913] Freeing unused kernel memory: 696k freed
[    1.038521] Write protecting the kernel text: 5340k
[    1.038617] Write protecting the kernel read-only data: 2192k
[    1.082553] udevd[80]: starting version 173
[    1.316140] usb 1-5: new high speed USB device number 2 using ehci_hcd
[    1.365391] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.365475] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.365640] r8169 0000:02:00.0: setting latency timer to 64
[    1.374150] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.375958] r8169 0000:02:00.0: eth0: RTL8102e at 0xf801e000, 00:e0:91:3c:a7:b8, XID 04c00000 IRQ 42
[    1.400558] ahci 0000:00:1f.2: version 3.0
[    1.400597] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.400704] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.400846] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.400860] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.400873] ahci 0000:00:1f.2: setting latency timer to 64
[    1.404203] scsi0 : ahci
[    1.411743] scsi1 : ahci
[    1.415806] scsi2 : ahci
[    1.420117] scsi3 : ahci
[    1.420640] ata1: SATA max UDMA/133 abar m1024@0xf4344400 port 0xf4344500 irq 43
[    1.420651] ata2: DUMMY
[    1.420660] ata3: SATA max UDMA/133 abar m1024@0xf4344400 port 0xf4344600 irq 43
[    1.420669] ata4: DUMMY
[    1.740159] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.740233] ata3: SATA link down (SStatus 0 SControl 300)
[    1.741325] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.741533] ata1.00: ATA-8: FUJITSU MHZ2160BH, 00000009, max UDMA/100
[    1.741550] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.742420] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.742596] ata1.00: configured for UDMA/100
[    1.743101] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2160B 0000 PQ: 0 ANSI: 5
[    1.743757] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.744119] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.744390] sd 0:0:0:0: [sda] Write Protect is off
[    1.744399] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.744503] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.773733]  sda: sda1 sda2 sda3
[    1.774687] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.880145] usb 5-1: new full speed USB device number 2 using uhci_hcd
[    2.897485] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[   38.437969] udevd[334]: starting version 173
[   38.573071] lp: driver loaded but no devices found
[   39.131041] acpi device:06: registered as cooling_device3
[   39.133361] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   39.133556] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   39.182376] wmi: Mapper loaded
[   39.319493] type=1400 audit(1328074022.776:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
[   39.321132] type=1400 audit(1328074022.780:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 comm="apparmor_parser"
[   39.322115] type=1400 audit(1328074022.780:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="apparmor_parser"
[   39.461292] [drm] Initialized drm 1.1.0 20060810
[   39.640906] intel_rng: FWH not detected
[   39.987249] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   40.014561] leds_ss4200: no LED devices found
[   40.086991] ieee80211_crypt: registered algorithm 'NULL'
[   40.087002] ieee80211_crypt: registered algorithm 'TKIP'
[   40.087010] ieee80211_crypt: registered algorithm 'CCMP'
[   40.087016] ieee80211_crypt: registered algorithm 'WEP'
[   40.087023] 
[   40.087025] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   40.087031] Copyright (c) 2004-2005, Andrea Merello
[   40.087036] r8180: Initializing module
[   40.087041] r8180: Wireless extensions version 22
[   40.087047] r8180: Initializing proc filesystem
[   40.087122] r8180: Configuring chip resources
[   40.087157] r8180 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   40.087174] r8180 0000:03:00.0: setting latency timer to 64
[   40.096000] rtl8180_init:Error channel plan! Set to default.
[   40.096036] r8180: Channel plan is 0
[   40.096040] 
[   40.096046] Dot11d_Init()
[   40.096054] r8180: MAC controller is a RTL8187SE b/g
[   40.098208] r8180: usValue is 0x100
[   40.098211] 
[   40.141669] r8180: EEPROM version 104
[   40.146047] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   40.163472] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.163491] i915 0000:00:02.0: setting latency timer to 64
[   40.164259] r8180: IRQ 18
[   40.165984] r8180: Driver probe completed
[   40.165989] 
[   40.232802] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   40.232813] [drm] Driver supports precise vblank timestamp query.
[   40.279580] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   40.511083] Bluetooth: Core ver 2.16
[   40.511168] NET: Registered protocol family 31
[   40.511175] Bluetooth: HCI device and connection manager initialized
[   40.511183] Bluetooth: HCI socket layer initialized
[   40.511189] Bluetooth: L2CAP socket layer initialized
[   40.516384] Bluetooth: SCO socket layer initialized
[   40.517483] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   40.522140] usbcore: registered new interface driver btusb
[   40.538062] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   40.585973] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   40.596679] [drm] initialized overlay support
[   40.618353] fbcon: inteldrmfb (fb0) is primary device
[   40.619144] Console: switching to colour frame buffer device 128x36
[   40.619229] fb0: inteldrmfb frame buffer device
[   40.619235] drm: registered panic notifier
[   40.619451] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   40.719634] Linux video capture interface: v2.00
[   40.967793] uvcvideo: Found UVC 1.00 device FS13FF-183 (05c8:0303)
[   40.970334] input: FS13FF-183 as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input7
[   40.970581] usbcore: registered new interface driver uvcvideo
[   40.970590] USB Video Class driver (v1.1.0)
[   41.652562] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   41.652583] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   41.652628] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   41.652747] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   41.652818] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   41.940594] hda_codec: ALC269: BIOS auto-probing.
[   41.952693] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   41.953452] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   46.742945] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:2 across:292488k 
[   46.875638] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   47.319698] type=1400 audit(1328074030.776:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=894 comm="apparmor_parser"
[   47.329879] type=1400 audit(1328074030.788:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=893 comm="apparmor_parser"
[   47.335588] type=1400 audit(1328074030.792:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=894 comm="apparmor_parser"
[   47.336659] type=1400 audit(1328074030.796:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=894 comm="apparmor_parser"
[   47.391464] ppdev: user-space parallel port driver
[   47.408689] type=1400 audit(1328074030.868:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=905 comm="apparmor_parser"
[   47.410368] type=1400 audit(1328074030.868:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=905 comm="apparmor_parser"
[   47.438192] type=1400 audit(1328074030.896:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=901 comm="apparmor_parser"
[   47.478317] type=1400 audit(1328074030.936:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=919 comm="apparmor_parser"
[   47.493166] type=1400 audit(1328074030.952:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=919 comm="apparmor_parser"
[   47.517154] type=1400 audit(1328074030.976:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=918 comm="apparmor_parser"
[   47.832827] init: failsafe main process (841) killed by TERM signal
[   47.851327] init: apport pre-start process (960) terminated with status 1
[   47.933450] init: apport post-stop process (986) terminated with status 1
[   48.354427] r8169 0000:02:00.0: eth0: link down
[   48.354953] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.362913] r8180: Bringing up iface
[   48.561471] r8180: Card successfully reset
[   48.991648] vboxdrv: Found 2 processor cores.
[   48.994859] vboxdrv: fAsync=0 offMin=0x1e0 offMax=0x2bbc
[   48.997666] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   48.997675] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
[   49.167054] vboxpci: IOMMU not found (not registered)
[   49.302459] r8180: WIRELESS_MODE_G
[   49.302468] 
[   49.333646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.423618] Bluetooth: RFCOMM TTY layer initialized
[   49.423636] Bluetooth: RFCOMM socket layer initialized
[   49.423643] Bluetooth: RFCOMM ver 1.11
[   49.520374] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.520383] Bluetooth: BNEP filters: protocol multicast
[   50.532118] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[   52.489030] =>>>>>>>>>>=============================>set power:0, 0!
[   52.489041] Timeout 1
[   53.140764] init: plymouth-stop pre-start process (1335) terminated with status 1
[   54.520122] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
[   54.699031] =>>>>>>>>>>=============================>set power:0, 8960!
[   54.699044] Timeout 1
[   64.059770] Linking with TELUS5055: channel is 1
[   64.077782] Associated successfully
[   64.077792] Using G rates
[   64.092162] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.135645] Linking with TELUS5055: channel is 1
[   64.154279] Associated successfully
[   64.154289] Using G rates
[   72.275931] Associated successfully
[   72.275941] Using G rates
[   83.184056] wlan0: no IPv6 routers present
[   83.956210] usb 1-6: new high speed USB device number 4 using ehci_hcd
[   84.455475] usbcore: registered new interface driver uas
[   84.487287] Initializing USB Mass Storage driver...
[   84.487839] scsi4 : usb-storage 1-6:1.0
[   84.489447] usbcore: registered new interface driver usb-storage
[   84.489459] USB Mass Storage support registered.
[   85.489952] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9809 PQ: 0 ANSI: 0
[   85.624797] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   85.668274] sd 4:0:0:0: [sdb] 29120 512-byte logical blocks: (14.9 MB/14.2 MiB)
[   85.672166] sd 4:0:0:0: [sdb] Write Protect is off
[   85.672181] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   85.673420] sd 4:0:0:0: [sdb] No Caching mode page present
[   85.673436] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   85.688160] sd 4:0:0:0: [sdb] No Caching mode page present
[   85.688174] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   85.690128]  sdb: sdb1
[   85.695288] sd 4:0:0:0: [sdb] No Caching mode page present
[   85.695305] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   85.695316] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  123.601457] WARNING! power/level is deprecated; use power/control instead
[  123.680563] usb 1-6: USB disconnect, device number 4

Entering "cat /proc/cmdline" produced this:

BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=523EF5FB3EF5D7C5 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7

And entering "cat /etc/initramfs-tools/conf.d/resume" gave me this, which is useless...

cat: /etc/initramfs-tools/conf.d/resume: No such file or directory


And my computer is an LG X120, running XP and Ubuntu 11.10 dual boot. One gig of RAM, 160 gb hdd. Pretty basic netbook.

---

### Post by Toz on 2012-02-01
Can you please use code blocks when posting back logs? See the "Code" section at: [http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode").

Can you post back the results of a few more commands:
```
lsmod
cat /etc/fstab

```

And, can you please complete the following procedure to get a more detailed hibernate log file:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate

```
...this will now try to hibernate the machine - which should fail. When you recover the system, please post back the contents of the **/var/log/pm-suspend.log** file.

> [ 39.987249] r8187se: module is from the staging directory, the quality is unknown, you have been warned.This may be relevant: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/667138]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/667138")

---

### Post by chughes27 on 2012-02-01
[code]Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  8 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
joydev                 17393  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  1 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509487  3 
r8187se               157152  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
eeprom_93cx6           12653  1 r8187se
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
wmi                    18744  0 
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 [code]

[code]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
[code]

I am doing the hibernate thing now...

---

### Post by Toz on 2012-02-01
You're close with the code tags. The trailing code tag should be **[COLOR="Red"]/[/COLOR]code**

Also try this:
```
gksudo /etc/pm/config.d/unload_module
```
...and copy/paste the following line:
```

SUSPEND_MODULES="r8187se"
```
...then save the file.

Try hibernate again.

Also, is this a wubi install?

---

### Post by chughes27 on 2012-02-01
And here's the log file...it's over three thousand lines of text...

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Tue Jan 31 23:20:29 MST 2012: Running hooks for hibernate.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Tue Jan 31 23:20:29 MST 2012: Running hooks for hibernate. = -n ]
+ printf %s\n Tue Jan 31 23:20:29 MST 2012: Running hooks for hibernate.
Tue Jan 31 23:20:29 MST 2012: Running hooks for hibernate.
+ run_hooks sleep hibernate hibernate
+ _run_hooks sleep hibernate hibernate
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs=     

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS=     

+ sort
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS=     

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux ubuntu 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux
+ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  8 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
joydev                 17393  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  1 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509487  3 
r8187se               157152  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
eeprom_93cx6           12653  1 r8187se
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
wmi                    18744  0 
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       1015572    1000600      14972          0     260064     453044
-/+ buffers/cache:     287492     728080
Swap:       262136      40188     221948
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ awk -F: {print $3}
+ getent passwd pulse
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=calebhughes
+ save_pulse_state sink calebhughes
+ su calebhughes -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:calebhughes:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ save_pulse_state source calebhughes
+ index=
+ read field value
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ su calebhughes -c -- pacmd list-sources
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:calebhughes:source0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:calebhughes:source1 no
+ [ -n no ]
+ echo no
+ read field value
+ su calebhughes -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ sed s/109//
+ ps -C pulseaudio -o uid=
+ tr -d  
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=calebhughes
+ su calebhughes -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink calebhughes
+ su calebhughes -c -- pacmd list-sinks
+ index=
+ + readsed field -n value s/^[[:space:]*]*//; /\(index\|mute\)/p

+ [ index = index ]
+ index=0
+ su calebhughes -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source calebhughes
+ index=
+ read field value
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ su calebhughes -c -- pacmd list-sources
+ [ index = index ]
+ index=0
+ su calebhughes -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su calebhughes -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ _run_hook /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ log Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common hibernate hibernate: 
/etc/pm/sleep.d/10_grub-common hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate
Selected interface 'wlan0'
OK
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
       --quirk-dpms-suspend
       --quirk-s3-mode
       --quirk-s3-bios
       --quirk-vbe-post
       --quirk-vbe-post
       --quirk-vga-mode-3
       --quirk-vbemode-restore
       --quirk-vbestate-restore
       --quirk-reset-brightness
       --quirk-radeon-off
       --quirk-no-fb
       --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PUMASF10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PUMASF10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Phoenix Technologies LTD'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Phoenix Technologies LTD'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=06/25/2009
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=06/25/2009
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='LG Electronics'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='LG Electronics'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=X120-L.C76TA9
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=X120-L.C76TA9
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Not Applicable'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Not Applicable'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=Xenia2
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=Xenia2
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Not Applicable'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Not Applicable'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='LG Electronics'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='LG Electronics'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:00:02.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:00:02.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x27ae
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x27ae
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x27ae
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:00:02.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:00:02.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../bus/pci/drivers/i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@85(videoget): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@239(has_parameter): get_parameters
//usr/lib/pm-utils/functions@234(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@243(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@360(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@361(): add_parameters --quirk-no-chvt
/usr/lib/pm-utils/functions@226(add_parameters): remove_parameters --quirk-no-chvt
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-no-chvt = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-chvt
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@227(add_parameters): for x in '"$@"'
/usr/lib/pm-utils/functions@228(add_parameters): echo --quirk-no-chvt
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@362(): echo 'Kernel modesetting video driver detected, not using quirks.'
Kernel modesetting video driver detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=--quirk-no-chvt
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ QUIRK_NO_CHVT=true
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set true
+ return 0
+ return
+ is_set no
+ return 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: 
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: 
/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS=     

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Tue Jan 31 23:20:38 MST 2012: performing hibernate
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Tue Jan 31 23:20:38 MST 2012: performing hibernate = -n ]
+ printf %s\n Tue Jan 31 23:20:38 MST 2012: performing hibernate
Tue Jan 31 23:20:38 MST 2012: performing hibernate
+ sync
+ do_hibernate
+ [ -n  ]
+ echo -n disk
+ r=128
+ date
+ log Tue Jan 31 23:20:57 MST 2012: Awake.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Tue Jan 31 23:20:57 MST 2012: Awake. = -n ]
+ printf %s\n Tue Jan 31 23:20:57 MST 2012: Awake.
Tue Jan 31 23:20:57 MST 2012: Awake.
+ date
+ log Tue Jan 31 23:20:58 MST 2012: Running hooks for thaw
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Tue Jan 31 23:20:58 MST 2012: Running hooks for thaw = -n ]
+ printf %s\n Tue Jan 31 23:20:58 MST 2012: Running hooks for thaw
Tue Jan 31 23:20:58 MST 2012: Running hooks for thaw
+ run_hooks sleep thaw hibernate reverse
+ _run_hooks sleep thaw hibernate reverse
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs=     

+ local nifs=

+ IFS=

+ [ reverse = reverse ]
+ sort=sort -r
+ IFS=     

+ sort -r
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS=     

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ novatel_3g_suspend > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: 
/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ 99video > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ QUIRK_NO_CHVT=true
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ is_set no
+ return 1
+ maybe_deallocvt
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ return 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video thaw hibernate: 
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 99video ]
+ [ 98video-quirk-db-handler > 99video ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
       --quirk-dpms-suspend
       --quirk-s3-mode
       --quirk-s3-bios
       --quirk-vbe-post
       --quirk-vbe-post
       --quirk-vga-mode-3
       --quirk-vbemode-restore
       --quirk-vbestate-restore
       --quirk-reset-brightness
       --quirk-radeon-off
       --quirk-no-fb
       --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@436(): state_exists video_quirks
/usr/lib/pm-utils/functions@184(state_exists): '[' -O /var/run/pm-utils/pm-suspend/storage/state:video_quirks ']'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@440(): has_parameter --store-quirks-as-lkw
//usr/lib/pm-utils/functions@239(has_parameter): get_parameters
//usr/lib/pm-utils/functions@234(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@240(has_parameter): for p in '$(get_parameters)'
/usr/lib/pm-utils/functions@241(has_parameter): '[' --quirk-no-chvt = --store-quirks-as-lkw ']'
/usr/lib/pm-utils/functions@243(has_parameter): return 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 98video-quirk-db-handler ]
+ [ 95led > 98video-quirk-db-handler ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led thaw hibernate: 
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 95led ]
+ [ 95hdparm-apm > 95led ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 95hdparm-apm ]
+ [ 95anacron > 95hdparm-apm ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: 
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 95anacron ]
+ [ 94cpufreq > 95anacron ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ [ -d /sys/devices/system/cpu/ ]
+ thaw_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -f cpu0/cpufreq/scaling_governor ]
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ restorestate cpu0_governor
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ restorestate cpu1_governor
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: 
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 94cpufreq ]
+ [ 90clock > 94cpufreq ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock thaw hibernate: 
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 90clock ]
+ [ 75modules > 90clock ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ resume_modules
+ modreload
+ [ -O /var/run/pm-utils/pm-suspend/storage/module:* ]
+ continue
+ echo Reloaded unloaded modules.
Reloaded unloaded modules.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules thaw hibernate: 
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=75modules
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 75modules ]
+ [ 60_wpa_supplicant > 75modules ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate
Selected interface 'wlan0'
OK
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 60_wpa_supplicant ]
+ [ 55NetworkManager > 60_wpa_supplicant ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ resume_nm
+ printf Having NetworkManager wake interfaces back up...
Having NetworkManager wake interfaces back up...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: 
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 55NetworkManager ]
+ [ 49bluetooth > 55NetworkManager ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: 
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 49bluetooth ]
+ [ 10_unattended-upgrades-hibernate > 49bluetooth ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 10_unattended-upgrades-hibernate ]
+ [ 10_grub-common > 10_unattended-upgrades-hibernate ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common thaw hibernate
+ _run_hook /etc/pm/sleep.d/10_grub-common thaw hibernate
+ log Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common thaw hibernate: 
/etc/pm/sleep.d/10_grub-common thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 10_grub-common ]
+ [ 01PulseAudio > 10_grub-common ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ resume_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ + sed s/109//
tr -d  
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=calebhughes
+ restore_pulse_state sink calebhughes
+ read index
+ sed -n s/^[[:space:]*]*index: //p
+ su calebhughes -c -- pacmd list-sinks
+ state_exists pulse:calebhughes:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:sink0 ]
+ restorestate pulse:calebhughes:sink0
+ state_exists pulse:calebhughes:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:sink0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:sink0
+ su calebhughes -c -- pacmd                     set-sink-mute                     0                     no
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read index
+ restore_pulse_state source calebhughes
+ read index
+ sed -n s/^[[:space:]*]*index: //p
+ su calebhughes -c -- pacmd list-sources
+ state_exists pulse:calebhughes:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source0 ]
+ restorestate pulse:calebhughes:source0
+ state_exists pulse:calebhughes:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source0
+ su calebhughes -c -- pacmd                     set-source-mute                     0                     no
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read index
+ state_exists pulse:calebhughes:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source1 ]
+ restorestate pulse:calebhughes:source1
+ state_exists pulse:calebhughes:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source1 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:calebhughes:source1
+ su calebhughes -c -- pacmd                     set-source-mute                     1                     no
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read index
+ su calebhughes -c -- pacmd suspend false
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 01PulseAudio ]
+ [ 00powersave > 01PulseAudio ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: 
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 00powersave ]
+ [ 00logging > 00powersave ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging thaw hibernate: 
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS=     

+ [ reverse -a reverse = reverse -a 00logging ]
+ [ 000kernel-change > 00logging ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: 
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS=     

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Tue Jan 31 23:21:13 MST 2012: Finished.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Tue Jan 31 23:21:13 MST 2012: Finished. = -n ]
+ printf %s\n Tue Jan 31 23:21:13 MST 2012: Finished.
Tue Jan 31 23:21:13 MST 2012: Finished.
+ exit 128
+ remove_suspend_lock
+ release_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ rm -f /var/run/pm-utils/locks/pm-suspend.lock
+ return 0
```

---

### Post by Toz on 2012-02-01
That's interesting. The log file shows that the system hibernated:
> 
+ log Tue Jan 31 23:20:29 MST 2012: Running hooks for hibernate.
...
Tue Jan 31 23:20:38 MST 2012: performing hibernate

...and re-awoke:
> 
+ log Tue Jan 31 23:20:57 MST 2012: Awake.
...
Tue Jan 31 23:21:13 MST 2012: Finished.


In your initial post you noted that system didn't turn off, but rather the fan continued to run. Did the same happen this time?

Can you please try the unload_module workaround from post #9?

---

### Post by chughes27 on 2012-02-01
That is weird, because the system did not hibernate. The screen went dark for a few seconds, cpu fan continued to run, and a few errors with numbers beside them came up saying "not enough free swap" then the system came back on.

Did the same thing when I tried method from post #9, only there were two more of the "not enough free swap" errors

---

### Post by Toz on 2012-02-01
> **chughes27 said:**
> Did the same thing when I tried method from post #9, only there were two more of the "not enough free swap" errors

You need to have as much free swap space as you have RAM to hibernate (the hibernate image is saved to the swap space). What do the following commands return:
```

free -m
df -h
cat /etc/fstab

```

---

### Post by chughes27 on 2012-02-01
Can't do that now... My Ubuntu will no longer boot. I'm making a thread to try and find a solution if you want to check that out and possibly help. 

Thanks for all the help so far!

Heres the link for the thread: [http://ubuntuforums.org/showthread.php?t=1918896](http://ubuntuforums.org/showthread.php?t=1918896)

---

