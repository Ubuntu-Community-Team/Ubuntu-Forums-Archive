---
title: "SD Card"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-08-14
I have Hardy Heron running on my laptop. This evening, Iput the SD card from my camera in the slot in the laptop (first time since installing HH) but it's not being seen. The slot worked fine the last time I used it, using XP. Any ideas?

---

### Post by Crafty Kisses on 2008-08-14
Try the following
```
sudo gedit /etc/fstab
```
Then, add this line
```
/dev/mmcblk0p1 /media/sdcard vfat umasak=0000 0 0
```
After you added that line
```
sudo mkdir /media/sdcard
```
Then the last thing
```
sudo mount /media/sdcard
```

That's what worked for me and I had the same problem as you, after I did that my SD card worked, so try that and if that doesn't work post back, also one more question, have you tried manually mounting it?

---

### Post by Cuttysark on 2008-08-15
I followed your advice but after entering the last command in Terminal it came back with "special device /dev/mmcblk0p1 does not exist" Regarding mounting manually, I'm so new to Ubuntu I wouldn't have a clue. I have Hardy installed on an old laptop and still with XP on my desktop. I have nothing on the laptop I can't afford to lose and for the moment, it's purely a learn linux machine, but if I can get up to speed enough to be confident, then I'd like to dump XP on my desktop also.

Regarding the SD card, it was from my camera. I had tried just plugging it in with the cable and using F-Spot but it never showed up, that's why the SD card in the laptop slot. However, later I found another post here where the guy discovered that you just had to put the camera in review mode, so I got my photos. It also picks up my Sandisk Sansa which is great.

Anyways, regarding the SD card in the slot, any other suggestions would be great as I'd still like to have that facility if the need arises.

ps, my aplogies for going on a bit, I just get excited when I'm learning new stuff.

---

### Post by coffeecat on 2008-08-15
You don't mention which laptop you're using. Ubuntu will automount SD cards in almost all generic USB card readers, but I've seen posts where people have difficulty reading from some laptop card slots. Presumably that's because they need special drivers which will have been preinstalled in the OEM version of Windows on the laptop.

Suggestions: Post details of your laptop - someone with the same make/model may be able to help. Also, search the forum for your model of laptop - you might find a relevant thread.

If you can't get the slot to work, you can buy USB SD card devices very cheaply. I don't mean those multi-card readers. I mean something about the size of a USB flash drive dongle. I got one free with an SD card I bought once. These work with Ubuntu.

I'm afraid that if it is down to a lack of a suitable driver, no amount of editing fstab is going to help.

**Edit**: with regard to /dev/mmcblk0p1 not existing, plug the card in, then open a terminal and type the command 'dmesg' (no quotes) and then return. Post the last dozen lines of the output and we can see whether the system is detecting the card and which /dev it is. You can highlight, copy and paste from a terminal, but in the terminal add the shift key to each standard keyboard shortcut. Ie, shift+ctrl+C for copy.

---

### Post by Kuzja on 2008-08-21
Hey, Im having the same problem, here is my "dmesg":

```
[ 1015.650518] ACPI: setting ELCR to 0200 (from 0a00)
[ 1015.651186] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
[ 1015.651195] SMP motherboard not detected.
[ 1015.651199] Local APIC not detected. Using dummy APIC emulation.
[ 1015.651274] Brought up 1 CPUs
[ 1015.651308] CPU0 attaching sched-domain:
[ 1015.651312]  domain 0: span 01
[ 1015.651315]   groups: 01
[ 1015.651636] net_namespace: 64 bytes
[ 1015.651649] Booting paravirtualized kernel on bare hardware
[ 1015.652902] Time: 18:19:33  Date: 08/21/08
[ 1015.652962] NET: Registered protocol family 16
[ 1015.653496] EISA bus registered
[ 1015.653516] ACPI: bus type pci registered
[ 1015.653816] PCI: PCI BIOS revision 2.10 entry at 0xf9798, last bus=4
[ 1015.653824] PCI: Using configuration type 1
[ 1015.653846] Setting up standard PCI resources
[ 1015.658496] ACPI: EC: Look up EC in DSDT
[ 1015.664210] ACPI: Interpreter enabled
[ 1015.664219] ACPI: (supports S0 S3 S4 S5)
[ 1015.664260] ACPI: Using PIC for interrupt routing
[ 1015.672022] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 1015.672396] PCI quirk: region d800-d83f claimed by ali7101 ACPI
[ 1015.672407] PCI quirk: region d860-d87f claimed by ali7101 SMB
[ 1015.673383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 1015.673480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 1015.676048] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11)
[ 1015.676206] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11)
[ 1015.676354] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11)
[ 1015.676500] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11)
[ 1015.676602] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 1015.676789] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[ 1015.677170] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[ 1015.677547] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 10 *11)
[ 1015.677843] ACPI: Power Resource [PFAN] (off)
[ 1015.677902] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 1015.677943] pnp: PnP ACPI init
[ 1015.677957] ACPI: bus type pnp registered
[ 1015.683331] pnp: PnP ACPI: found 10 devices
[ 1015.683336] ACPI: ACPI bus type pnp unregistered
[ 1015.683342] PnPBIOS: Disabled by ACPI PNP
[ 1015.683668] PCI: Using ACPI for IRQ routing
[ 1015.683673] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[ 1015.710298] NET: Registered protocol family 8
[ 1015.710300] NET: Registered protocol family 20
[ 1015.710404] AppArmor: AppArmor Filesystem Enabled
[ 1015.714280] Time: tsc clocksource has been installed.
[ 1015.722326] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 1015.722329] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[ 1015.722332] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[ 1015.722335] system 00:00: iomem range 0x100000-0x1dfeffff could not be reserved
[ 1015.722338] system 00:00: iomem range 0x1dff0000-0x1dffffff could not be reserved
[ 1015.722341] system 00:00: iomem range 0x1e000000-0x1fffffff could not be reserved
[ 1015.722345] system 00:00: iomem range 0xffe00000-0xffffffff could not be reserved
[ 1015.722360] system 00:08: ioport range 0x1e0-0x1e7 has been reserved
[ 1015.722363] system 00:08: ioport range 0x370-0x371 has been reserved
[ 1015.722366] system 00:08: ioport range 0x40b-0x40b has been reserved
[ 1015.722369] system 00:08: ioport range 0x480-0x48f has been reserved
[ 1015.722371] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[ 1015.722374] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[ 1015.722376] system 00:08: ioport range 0x6c0-0x6ff has been reserved
[ 1015.722379] system 00:08: ioport range 0xd800-0xd841 could not be reserved
[ 1015.722382] system 00:08: ioport range 0xd860-0xd89f could not be reserved
[ 1015.722384] system 00:08: ioport range 0xd8a0-0xd8bf has been reserved
[ 1015.722387] system 00:08: ioport range 0xe000-0xe07f has been reserved
[ 1015.722390] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[ 1015.722392] system 00:08: ioport range 0xe400-0xe47f has been reserved
[ 1015.722395] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[ 1015.722397] system 00:08: ioport range 0xe800-0xe87f has been reserved
[ 1015.722400] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[ 1015.722402] system 00:08: ioport range 0xec00-0xec7f has been reserved
[ 1015.722405] system 00:08: ioport range 0xec80-0xecff has been reserved
[ 1015.722408] system 00:08: ioport range 0xee90-0xee9f has been reserved
[ 1015.722410] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[ 1015.752953] PCI: Bridge: 0000:00:01.0
[ 1015.752956]   IO window: disabled.
[ 1015.752962]   MEM window: f7f00000-fdffffff
[ 1015.752967]   PREFETCH window: 38000000-380fffff
[ 1015.752973] PCI: Bus 2, cardbus bridge: 0000:00:11.0
[ 1015.752975]   IO window: 00001000-000010ff
[ 1015.752979]   IO window: 00001400-000014ff
[ 1015.752983]   PREFETCH window: 30000000-33ffffff
[ 1015.752987]   MEM window: 34000000-37ffffff
[ 1015.753002] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 1015.753027] PCI: Enabling device 0000:00:11.0 (0000 -> 0003)
[ 1015.753357] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[ 1015.753362] PCI: setting IRQ 11 as level-triggered
[ 1015.753366] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1015.753387] NET: Registered protocol family 2
[ 1015.790331] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 1015.790649] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 1015.790821] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 1015.790984] TCP: Hash tables configured (established 16384 bind 16384)
[ 1015.790987] TCP reno registered
[ 1015.802412] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[ 1016.292195]  it is
[ 1016.874955] Freeing initrd memory: 7739k freed
[ 1016.875302] Simple Boot Flag at 0x7c set to 0x1
[ 1016.875771] audit: initializing netlink socket (disabled)
[ 1016.875801] audit(1219342773.872:1): initialized
[ 1016.878372] VFS: Disk quotas dquot_6.5.1
[ 1016.878487] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1016.878682] io scheduler noop registered
[ 1016.878685] io scheduler anticipatory registered
[ 1016.878687] io scheduler deadline registered
[ 1016.878702] io scheduler cfq registered (default)
[ 1016.878720] Activating ISA DMA hang workarounds.
[ 1016.892943] Boot video device is 0000:01:00.0
[ 1016.893339] isapnp: Scanning for PnP cards...
[ 1017.247445] isapnp: No Plug & Play device found
[ 1017.291039] Real Time Clock Driver v1.12ac
[ 1017.291203] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 1017.292958] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 11
[ 1017.292964] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKI] -> GSI 11 (level, low) -> IRQ 11
[ 1017.292975] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[ 1017.293814] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 1017.293910] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 1017.294050] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 1017.299283] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1017.299291] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1017.300763] mice: PS/2 mouse device common for all mice
[ 1017.301152] EISA: Probing bus 0 at eisa.0
[ 1017.301162] Cannot allocate resource for EISA slot 1
[ 1017.301192] EISA: Detected 0 cards.
[ 1017.301197] cpuidle: using governor ladder
[ 1017.301199] cpuidle: using governor menu
[ 1017.301339] NET: Registered protocol family 1
[ 1017.301382] Using IPI No-Shortcut mode
[ 1017.301438] registered taskstats version 1
[ 1017.301668]   Magic number: 4:770:342
[ 1017.301871] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1017.301873] EDD information not available.
[ 1017.302804] Freeing unused kernel memory: 368k freed
[ 1017.332620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 1018.649242] fuse init (API version 7.9)
[ 1018.671601] ACPI: Transitioning device [FAN] to D3
[ 1018.671607] ACPI: Transitioning device [FAN] to D3
[ 1018.671612] ACPI: Fan [FAN] (off)
[ 1018.679439] ACPI: CPU0 (power states: C1[C1] C2[C2])
[ 1018.681205] ACPI: Thermal Zone [THRM] (87 C)
[ 1019.665830] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1019.665857] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1019.685822] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:04.0
[ 1019.685863] ACPI: Unable to derive IRQ for device 0000:00:04.0
[ 1019.685876] ALI15X3: not 100% native mode: will probe irqs later
[ 1019.685899]     ide0: BM-DMA at 0xeff0-0xeff7, BIOS settings: hda:DMA, hdb:pio
[ 1019.685917]     ide1: BM-DMA at 0xeff8-0xefff, BIOS settings: hdc:DMA, hdd:pio
[ 1019.685931] Probing IDE interface ide0...
[ 1019.753658] 8139too Fast Ethernet driver 0.9.28
[ 1019.841844] usbcore: registered new interface driver usbfs
[ 1019.841937] usbcore: registered new interface driver hub
[ 1019.858641] usbcore: registered new device driver usb
[ 1019.873699] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1020.648752] hda: IC25N060ATMR04-0, ATA DISK drive
[ 1020.648813] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[ 1020.649053] hda: host side 80-wire cable detection failed, limiting max speed to UDMA33
[ 1020.649061] hda: UDMA/33 mode selected
[ 1020.649395] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 1020.671927] Probing IDE interface ide1...
[ 1022.079010] hdc: TOSHIBA DVD-ROM SD-R2412, ATAPI CD/DVD-ROM drive
[ 1022.079068] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[ 1022.079103] hdc: UDMA/33 mode selected
[ 1022.079599] ide1 at 0x170-0x177,0x376 on irq 15
[ 1022.098454] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[ 1022.098462] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 1022.099148] eth0: RealTek RTL8139 at 0xe900, 00:08:0d:74:ec:d1, IRQ 11
[ 1022.099152] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[ 1022.099468] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[ 1022.099471] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1022.099487] ohci_hcd 0000:00:0c.0: OHCI Host Controller
[ 1022.100047] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 1
[ 1022.100078] ohci_hcd 0000:00:0c.0: irq 11, io mem 0xf7efc000
[ 1022.103187] SCSI subsystem initialized
[ 1022.119396] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 1022.121902] libata version 3.00 loaded.
[ 1022.156975] usb usb1: configuration #1 chosen from 1 choice
[ 1022.157016] hub 1-0:1.0: USB hub found
[ 1022.157027] hub 1-0:1.0: 3 ports detected
[ 1022.259176] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[ 1022.259185] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1022.259207] ohci_hcd 0000:00:0c.1: OHCI Host Controller
[ 1022.259248] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 2
[ 1022.259268] ohci_hcd 0000:00:0c.1: irq 11, io mem 0xf7efb000
[ 1022.316719] usb usb2: configuration #1 chosen from 1 choice
[ 1022.316757] hub 2-0:1.0: USB hub found
[ 1022.316766] hub 2-0:1.0: 2 ports detected
[ 1022.419144] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 1022.419170] ehci_hcd 0000:00:0c.2: EHCI Host Controller
[ 1022.419217] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 3
[ 1022.419271] ehci_hcd 0000:00:0c.2: irq 11, io mem 0xf7efaf00
[ 1022.562311] usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 1022.575090] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 1022.575273] usb usb3: configuration #1 chosen from 1 choice
[ 1022.575305] hub 3-0:1.0: USB hub found
[ 1022.575314] hub 3-0:1.0: 5 ports detected
[ 1022.706338] hda: max request size: 128KiB
[ 1022.706716] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63
[ 1022.707236] hda: cache flushes supported

[ 1022.707301]  hda: hda1 hda2 hda3 hda4 < hda5 >
[ 1022.793194] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[ 1022.793206] Uniform CD-ROM driver Revision: 3.20
[ 1023.125647] usb 3-3: new high speed USB device using ehci_hcd and address 2
[ 1023.259422] usb 3-3: configuration #1 chosen from 1 choice
[ 1023.441403] usbcore: registered new interface driver libusual
[ 1023.449944] Initializing USB Mass Storage driver...
[ 1023.709983] Attempting manual resume
[ 1023.709989] swsusp: Resume From Partition 3:5
[ 1023.709991] PM: Checking swsusp image.
[ 1023.712547] PM: Resume from disk failed.
[ 1023.744949] usb 1-3: new low speed USB device using ohci_hcd and address 3
[ 1023.785355] kjournald starting.  Commit interval 5 seconds
[ 1023.785372] EXT3-fs: mounted filesystem with ordered data mode.
[ 1023.958927] usb 1-3: configuration #1 chosen from 1 choice
[ 1023.962040] scsi0 : SCSI emulation for USB Mass Storage devices
[ 1023.962122] usbcore: registered new interface driver usb-storage
[ 1023.962126] USB Mass Storage support registered.
[ 1023.962395] usb-storage: device found at 2
[ 1023.962397] usb-storage: waiting for device to settle before scanning
[ 1028.956022] usb-storage: device scan complete
[ 1028.956603] scsi 0:0:0:0: Direct-Access     WD       600BEVSExternal  1.02 PQ: 0 ANSI: 0
[ 1037.616144] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 1037.702225] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[ 1039.191028] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1039.350861] Linux agpgart interface v0.102
[ 1039.550922] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 1039.778299] agpgart: Unsupported ALi chipset (device id: 1672)
[ 1039.846473] ali15x3_smbus 0000:00:08.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[ 1039.846484] ali15x3_smbus 0000:00:08.0: ALI15X3 not detected, module not inserted.
[ 1039.986455] ACPI: AC Adapter [ADP1] (on-line)
[ 1040.053674] input: Power Button (FF) as /devices/virtual/input/input2
[ 1040.061883] ACPI: Power Button (FF) [PWRF]
[ 1040.062262] input: Power Button (CM) as /devices/virtual/input/input3
[ 1040.077828] ACPI: Power Button (CM) [PWRB]
[ 1040.077946] input: Lid Switch as /devices/virtual/input/input4
[ 1040.078038] ACPI: Lid Switch [LID]
[ 1040.119294] ACPI: Battery Slot [BAT1] (battery present)
[ 1040.707306] Yenta: CardBus bridge found at 0000:00:11.0 [1179:0001]
[ 1040.747736] ath_hal: module license 'Proprietary' taints kernel.
[ 1040.775312] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1040.833744] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[ 1040.833751] Socket status: 30000007
[ 1041.124846] wlan: 0.9.4
[ 1041.272180] ath_pci: 0.9.4
[ 1041.272299] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1042.271578] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/LNXVIDEO:00/input/input5
[ 1042.287302] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[ 1042.407354] input: PC Speaker as /devices/platform/pcspkr/input/input6
[ 1043.636667] ath_rate_sample: 1.2 (0.9.4)
[ 1043.638159] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 1043.638168] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1043.638178] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 1043.638183] wifi0: mac 5.6 phy 4.1 radio 1.7
[ 1043.638189] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 1043.638191] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 1043.638193] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 1043.638195] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 1043.638197] wifi0: Use hw queue 8 for CAB traffic
[ 1043.638199] wifi0: Use hw queue 9 for beacons
[ 1043.670777] input: PS/2 Mouse as /devices/virtual/input/input7
[ 1043.702969] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[ 1043.739071] usbcore: registered new interface driver hiddev
[ 1043.749930] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:0c.0/usb1/1-3/1-3:1.0/input/input9
[ 1043.765867] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:0c.0-3
[ 1043.765940] usbcore: registered new interface driver usbhid
[ 1043.765953] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 1043.828917] wifi0: Atheros 5212: mem=0xf7ee0000, irq=11
[ 1043.829539] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[ 1043.829544] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[ 1043.868588] Driver 'sd' needs updating - please use bus_type methods
[ 1043.875747] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[ 1043.876499] sd 0:0:0:0: [sda] Write Protect is off
[ 1043.876504] sd 0:0:0:0: [sda] Mode Sense: 00 00 00 00
[ 1043.876507] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 1043.877608] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[ 1043.878346] sd 0:0:0:0: [sda] Write Protect is off
[ 1043.878349] sd 0:0:0:0: [sda] Mode Sense: 00 00 00 00
[ 1043.878352] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 1043.878360]  sda:<6>parport_pc 00:09: reported by Plug and Play ACPI
[ 1043.914441] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 1046.268336]  sda1
[ 1046.268652] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1046.354168] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1046.371972] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[ 1046.375447] cs: IO port probe 0x3e0-0x4ff: clean.
[ 1046.376767] cs: IO port probe 0x820-0x8ff: clean.
[ 1046.377898] cs: IO port probe 0xc00-0xcf7: clean.
[ 1046.379403] cs: IO port probe 0xa00-0xaff: clean.
[ 1048.408042] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
[ 1048.424023] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0xffffffff], removing mixer.
[ 1048.424035] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ali5451/ali5451.c:1927: ali mixer 1 creating error.
[ 1049.094963] loop: module loaded
[ 1049.133820] lp0: using parport0 (interrupt-driven).
[ 1049.256254] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[ 1049.817456] EXT3 FS on hda1, internal journal
[ 1051.271021] kjournald starting.  Commit interval 5 seconds
[ 1051.271260] EXT3 FS on hda2, internal journal
[ 1051.271267] EXT3-fs: mounted filesystem with ordered data mode.
[ 1052.929685] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[ 1052.929692] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[ 1052.930189] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[ 1052.930192] toshiba_acpi: ktoshkeyd will check 2 times per second
[ 1052.930628] toshiba_acpi: Dropped 0 keys from the queue on startup
[ 1053.163088] No dock devices found.
[ 1054.238289] ppdev: user-space parallel port driver
[ 1054.742318] audit(1219342812.769:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5079 profile="/usr/sbin/cupsd" namespace="default"
[ 1055.763189] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1055.763198] vboxdrv: Successfully done.
[ 1055.763299] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 1055.763302] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[ 1057.576097] eth0: link down
[ 1079.213054] NET: Registered protocol family 10
[ 1079.213891] lo: Disabled Privacy Extensions
[ 1079.214892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1090.127232] ath0: no IPv6 routers present
[ 1100.929287] NET: Registered protocol family 17
[ 1119.469583] ath0: no IPv6 routers present
[ 1129.453844] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1144.554612] Inbound IN=ath0 OUT= MAC= SRC=192.168.0.101 DST=239.255.255.250 LEN=162 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=142 
[ 1177.586413] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:30:27:5e:40:00:73:06:de:43:4c:44:f4:d4:c0:a8:00:65:0a:cd:97:4f:74:d8:17:1f:00:00:00:00:70:02:ff:ff:52:f9:00:00:02:04:05:a0:01:01:04:02:30:ef:22:f4:e7:aa:fc:72:aa:be:d4:d4:03:88:dd:d2:8f:d6:4f:ca:cd:d9:04:f8:34:fd SRC=76.68.244.212 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=10078 DF PROTO=TCP SPT=2765 DPT=38735 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1177.587997] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2f:27:5f:00:00:73:11:1e:39:4c:44:f4:d4:c0:a8:00:65:d5:7f:97:4f:00:1b:1c:ef:ee:38:02:61:ca:b4:ed:a3:d4:8d:12:63:a7:d4:bf:c1:12:59:6a:d4:55:3f:08:01:fa:25:51:51:a9:d0:64:64:00:00:00:00:00:10:00:05:93:1a:d4:b6:f1:5d SRC=76.68.244.212 DST=192.168.0.101 LEN=47 TOS=0x00 PREC=0x00 TTL=115 ID=10079 PROTO=UDP SPT=54655 DPT=38735 LEN=27 
vitaly@ToshibaLaptop:~$ dmesg | tail -25
[ 1054.742318] audit(1219342812.769:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5079 profile="/usr/sbin/cupsd" namespace="default"
[ 1055.763189] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1055.763198] vboxdrv: Successfully done.
[ 1055.763299] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 1055.763302] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[ 1057.576097] eth0: link down
[ 1079.213054] NET: Registered protocol family 10
[ 1079.213891] lo: Disabled Privacy Extensions
[ 1079.214892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1090.127232] ath0: no IPv6 routers present
[ 1100.929287] NET: Registered protocol family 17
[ 1119.469583] ath0: no IPv6 routers present
[ 1129.453844] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1144.554612] Inbound IN=ath0 OUT= MAC= SRC=192.168.0.101 DST=239.255.255.250 LEN=162 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=142 
[ 1177.586413] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:30:27:5e:40:00:73:06:de:43:4c:44:f4:d4:c0:a8:00:65:0a:cd:97:4f:74:d8:17:1f:00:00:00:00:70:02:ff:ff:52:f9:00:00:02:04:05:a0:01:01:04:02:30:ef:22:f4:e7:aa:fc:72:aa:be:d4:d4:03:88:dd:d2:8f:d6:4f:ca:cd:d9:04:f8:34:fd SRC=76.68.244.212 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=10078 DF PROTO=TCP SPT=2765 DPT=38735 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1177.587997] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2f:27:5f:00:00:73:11:1e:39:4c:44:f4:d4:c0:a8:00:65:d5:7f:97:4f:00:1b:1c:ef:ee:38:02:61:ca:b4:ed:a3:d4:8d:12:63:a7:d4:bf:c1:12:59:6a:d4:55:3f:08:01:fa:25:51:51:a9:d0:64:64:00:00:00:00:00:10:00:05:93:1a:d4:b6:f1:5d SRC=76.68.244.212 DST=192.168.0.101 LEN=47 TOS=0x00 PREC=0x00 TTL=115 ID=10079 PROTO=UDP SPT=54655 DPT=38735 LEN=27 
[ 1401.048650] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:28:23:09:40:00:6a:06:42:b6:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:10:fd:dd:14:fe:00:00:00:25:ae:8f:37:16:f6:d9:18:bc:1b:d6:c0:99:c0:dc:00:00:00:00:00:60:06:d6:20:5f:12:c0:00:01:10:00:00:02 SRC=79.182.154.77 DST=192.168.0.101 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=8969 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK URGP=0 
[ 1463.479951] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:2a:49:40:00:6a:06:3b:72:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:eb:ef:79:73:09:6e:85:f7:48:60:6c:bd:2e:8f:60:60:32:35:35:2e:32:35:30:3a:31:39:30:30:0d:0a SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=10825 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1467.183644] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:2a:c2:40:00:6a:06:3a:f9:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:45:b9:60:94:0f:a5:0a:af:65:64:31:38:3a:c1:8c:35:cd:01:bb:ca:66:fd:8b:00:50:7c:b0:18:c3:5e SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=10946 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1474.614450] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:2b:b8:40:00:6a:06:3a:03:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:8e:84:e3:3c:36:c3:50:78:48:60:6c:f9:14:5c:cf:cf:00:60:06:d6:20:5f:12:c0:00:01:10:00:00:02 SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=11192 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1489.358608] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:2d:c5:40:00:6a:06:37:f6:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:13:97:43:f9:bf:e2:be:cf:48:60:6c:55:8b:a8:e2:e2:00:60:06:d6:20:5f:12:c0:00:01:10:00:00:02 SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=11717 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1518.967012] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:31:55:40:00:6a:06:34:66:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:17:75:84:1e:bb:5e:1b:d3:00:03:72:dd:00:00:00:00:00:60:06:d6:20:5f:12:c0:00:01:10:00:00:02 SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=12629 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1578.074988] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:2c:39:0a:40:00:6a:06:2c:b1:4f:b6:9a:4d:c0:a8:00:65:1f:91:92:37:d0:a0:b0:61:57:f9:67:23:50:18:fd:dd:14:f2:00:00:00:00:00:00:95:e3:6e:98:32:61:5e:e3:48:60:6c:70:90:eb:cc:cc:00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=79.182.154.77 DST=192.168.0.101 LEN=44 TOS=0x00 PREC=0x00 TTL=106 ID=14602 DF PROTO=TCP SPT=8081 DPT=37431 WINDOW=64989 RES=0x00 ACK PSH URGP=0 
[ 1645.092741] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:28:03:5b:98:da:40:00:6f:06:30:72:4e:80:2f:9b:c0:a8:00:65:d9:79:ba:ee:a3:62:7b:61:a5:c2:6d:fb:50:18:fe:c4:45:ff:00:00:5f:6f:6e:6c:79:69:33:65:31:31:3a:75:74:5f:6d:65:74:61:64:61:74:61:69:32:65:36:3a:75:74:5f:70:65:78:69 SRC=78.128.47.155 DST=192.168.0.101 LEN=859 TOS=0x08 PREC=0x20 TTL=111 ID=39130 DF PROTO=TCP SPT=55673 DPT=47854 WINDOW=65220 RES=0x00 ACK PSH URGP=0 
[ 1858.543212] Inbound IN=ath0 OUT= MAC=00:90:96:85:3c:29:00:13:46:a5:13:6c:08:00:45:00:00:28:5d:93:40:00:6a:06:08:2c:4f:b6:9a:4d:c0:a8:00:65:1f:91:d8:db:3e:a2:34:dc:02:0e:6c:35:50:10:fd:dd:2c:b7:00:00:c8:5c:c8:7f:17:79:89:85:18:86:07:d6:40:ce:6c:dd:00:00:00:00:00:60:06:d6:20:5f:12:c0:00:01:10:00:00:02 SRC=79.182.154.77 DST=192.168.0.101 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=23955 DF PROTO=TCP SPT=8081 DPT=55515 WINDOW=64989 RES=0x00 ACK URGP=0 

```

---

### Post by Kuzja on 2008-08-24
bump

---

### Post by moore.bryan on 2008-08-24
how about the output of ```
lspci
```...

---

### Post by Kuzja on 2008-08-27
Sorry, I'm moving right now so i cant check this forum every day. Anyways here is my lspci:

> 00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


---

### Post by egalvan on 2008-08-27
I've installed Hardy on six machines in the last three months, 
and I've noticed that clicking on "PLACES" shows ALL drives attached...
USB, NTFS, etc...

Clicking on them will auto-mount them, a browser window  will open,
 and an icon will (usually, almost always)  pop up on the desktop.

It's never failed for me.
 And I've never messed with fstab or dev or anything like that.

The only thing that "fails" is ownership, but that's for another post.

ErnestG

---

### Post by linuxguymarshall on 2008-08-27
What version of Ubuntu are you using. on 7.10 I had to reboot for it to show.

On 8.04 I have no problems with just placing it in. Make sure you are completely updated

---

### Post by moore.bryan on 2008-08-28
no worries... we all have things which keep us away from the forums, even though many of us get sucked right back in. ;-)

a little more info, please:
which flavor of ubuntu, which kernel, and as much info as you can give about the type of lappie you have.

---

### Post by Kuzja on 2008-08-28
I have Ubuntu Hardy, 2.6.24.19-generic on my old Toshiba Satellite A20. Here is more info on it [http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1912&part=1992#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1912&part=1992#spectop), and if you need any other specific info just let me now. Thanks for your help

---

### Post by moore.bryan on 2008-08-31
not a problem... when you go into the /dev dir, are there any "strange" entries; i.e., your hard drive(s) should be sd(a/b/c)# depending on how many partitions/disks you have. is there anything in there about mmc?

---

### Post by Kuzja on 2008-09-05
Thats what I have in my /dev when card is in the slot: 

> audio	   ptybc  ptyqa  ptyv8	ram14	    tty56  ttye2  ttysc  ttyxa
audio1	   ptybd  ptyqb  ptyv9	ram15	    tty57  ttye3  ttysd  ttyxb
bus	   ptybe  ptyqc  ptyva	ram2	    tty58  ttye4  ttyse  ttyxc
cdrom	   ptybf  ptyqd  ptyvb	ram3	    tty59  ttye5  ttysf  ttyxd
cdrw	   ptyc0  ptyqe  ptyvc	ram4	    tty6   ttye6  ttyt0  ttyxe
console    ptyc1  ptyqf  ptyvd	ram5	    tty60  ttye7  ttyt1  ttyxf
core	   ptyc2  ptyr0  ptyve	ram6	    tty61  ttye8  ttyt2  ttyy0
disk	   ptyc3  ptyr1  ptyvf	ram7	    tty62  ttye9  ttyt3  ttyy1
dsp	   ptyc4  ptyr2  ptyw0	ram8	    tty63  ttyea  ttyt4  ttyy2
dsp1	   ptyc5  ptyr3  ptyw1	ram9	    tty7   ttyeb  ttyt5  ttyy3
dvd	   ptyc6  ptyr4  ptyw2	random	    tty8   ttyec  ttyt6  ttyy4
fd	   ptyc7  ptyr5  ptyw3	rtc	    tty9   ttyed  ttyt7  ttyy5
full	   ptyc8  ptyr6  ptyw4	sda	    ttya0  ttyee  ttyt8  ttyy6
fuse	   ptyc9  ptyr7  ptyw5	sda1	    ttya1  ttyef  ttyt9  ttyy7
hda	   ptyca  ptyr8  ptyw6	sequencer   ttya2  ttyp0  ttyta  ttyy8
hda1	   ptycb  ptyr9  ptyw7	sequencer2  ttya3  ttyp1  ttytb  ttyy9
hda2	   ptycc  ptyra  ptyw8	sg0	    ttya4  ttyp2  ttytc  ttyya
hda3	   ptycd  ptyrb  ptyw9	shm	    ttya5  ttyp3  ttytd  ttyyb
hda4	   ptyce  ptyrc  ptywa	snapshot    ttya6  ttyp4  ttyte  ttyyc
hda5	   ptycf  ptyrd  ptywb	snd	    ttya7  ttyp5  ttytf  ttyyd
hdc	   ptyd0  ptyre  ptywc	sndstat     ttya8  ttyp6  ttyu0  ttyye
hidraw0    ptyd1  ptyrf  ptywd	stderr	    ttya9  ttyp7  ttyu1  ttyyf
hpet	   ptyd2  ptys0  ptywe	stdin	    ttyaa  ttyp8  ttyu2  ttyz0
initctl    ptyd3  ptys1  ptywf	stdout	    ttyab  ttyp9  ttyu3  ttyz1
input	   ptyd4  ptys2  ptyx0	toshiba     ttyac  ttypa  ttyu4  ttyz2
kmem	   ptyd5  ptys3  ptyx1	tty	    ttyad  ttypb  ttyu5  ttyz3
kmsg	   ptyd6  ptys4  ptyx2	tty0	    ttyae  ttypc  ttyu6  ttyz4
log	   ptyd7  ptys5  ptyx3	tty1	    ttyaf  ttypd  ttyu7  ttyz5
loop0	   ptyd8  ptys6  ptyx4	tty10	    ttyb0  ttype  ttyu8  ttyz6
loop1	   ptyd9  ptys7  ptyx5	tty11	    ttyb1  ttypf  ttyu9  ttyz7
loop2	   ptyda  ptys8  ptyx6	tty12	    ttyb2  ttyq0  ttyua  ttyz8
loop3	   ptydb  ptys9  ptyx7	tty13	    ttyb3  ttyq1  ttyub  ttyz9
loop4	   ptydc  ptysa  ptyx8	tty14	    ttyb4  ttyq2  ttyuc  ttyza
loop5	   ptydd  ptysb  ptyx9	tty15	    ttyb5  ttyq3  ttyud  ttyzb
loop6	   ptyde  ptysc  ptyxa	tty16	    ttyb6  ttyq4  ttyue  ttyzc
loop7	   ptydf  ptysd  ptyxb	tty17	    ttyb7  ttyq5  ttyuf  ttyzd
MAKEDEV    ptye0  ptyse  ptyxc	tty18	    ttyb8  ttyq6  ttyv0  ttyze
mem	   ptye1  ptysf  ptyxd	tty19	    ttyb9  ttyq7  ttyv1  ttyzf
mixer	   ptye2  ptyt0  ptyxe	tty2	    ttyba  ttyq8  ttyv2  urandom
mixer1	   ptye3  ptyt1  ptyxf	tty20	    ttybb  ttyq9  ttyv3  usbdev1.1_ep00
net	   ptye4  ptyt2  ptyy0	tty21	    ttybc  ttyqa  ttyv4  usbdev1.1_ep81
null	   ptye5  ptyt3  ptyy1	tty22	    ttybd  ttyqb  ttyv5  usbdev1.2_ep00
nvidia0    ptye6  ptyt4  ptyy2	tty23	    ttybe  ttyqc  ttyv6  usbdev1.2_ep81
nvidiactl  ptye7  ptyt5  ptyy3	tty24	    ttybf  ttyqd  ttyv7  usbdev2.1_ep00
oldmem	   ptye8  ptyt6  ptyy4	tty25	    ttyc0  ttyqe  ttyv8  usbdev2.1_ep81
port	   ptye9  ptyt7  ptyy5	tty26	    ttyc1  ttyqf  ttyv9  usbdev3.1_ep00
ppp	   ptyea  ptyt8  ptyy6	tty27	    ttyc2  ttyr0  ttyva  usbdev3.1_ep81
psaux	   ptyeb  ptyt9  ptyy7	tty28	    ttyc3  ttyr1  ttyvb  usbdev3.3_ep00
ptmx	   ptyec  ptyta  ptyy8	tty29	    ttyc4  ttyr2  ttyvc  usbdev3.3_ep81
pts	   ptyed  ptytb  ptyy9	tty3	    ttyc5  ttyr3  ttyvd  usbdev3.3_ep82
ptya0	   ptyee  ptytc  ptyya	tty30	    ttyc6  ttyr4  ttyve  usbdev3.3_ep83
ptya1	   ptyef  ptytd  ptyyb	tty31	    ttyc7  ttyr5  ttyvf  usbdev3.4_ep00
ptya2	   ptyp0  ptyte  ptyyc	tty32	    ttyc8  ttyr6  ttyw0  usbdev3.4_ep02
ptya3	   ptyp1  ptytf  ptyyd	tty33	    ttyc9  ttyr7  ttyw1  usbdev3.4_ep81
ptya4	   ptyp2  ptyu0  ptyye	tty34	    ttyca  ttyr8  ttyw2  vboxdrv
ptya5	   ptyp3  ptyu1  ptyyf	tty35	    ttycb  ttyr9  ttyw3  vcs
ptya6	   ptyp4  ptyu2  ptyz0	tty36	    ttycc  ttyra  ttyw4  vcs1
ptya7	   ptyp5  ptyu3  ptyz1	tty37	    ttycd  ttyrb  ttyw5  vcs2
ptya8	   ptyp6  ptyu4  ptyz2	tty38	    ttyce  ttyrc  ttyw6  vcs3
ptya9	   ptyp7  ptyu5  ptyz3	tty39	    ttycf  ttyrd  ttyw7  vcs4
ptyaa	   ptyp8  ptyu6  ptyz4	tty4	    ttyd0  ttyre  ttyw8  vcs5
ptyab	   ptyp9  ptyu7  ptyz5	tty40	    ttyd1  ttyrf  ttyw9  vcs6
ptyac	   ptypa  ptyu8  ptyz6	tty41	    ttyd2  ttyS0  ttywa  vcs7
ptyad	   ptypb  ptyu9  ptyz7	tty42	    ttyd3  ttys0  ttywb  vcs8
ptyae	   ptypc  ptyua  ptyz8	tty43	    ttyd4  ttyS1  ttywc  vcsa
ptyaf	   ptypd  ptyub  ptyz9	tty44	    ttyd5  ttys1  ttywd  vcsa1
ptyb0	   ptype  ptyuc  ptyza	tty45	    ttyd6  ttyS2  ttywe  vcsa2
ptyb1	   ptypf  ptyud  ptyzb	tty46	    ttyd7  ttys2  ttywf  vcsa3
ptyb2	   ptyq0  ptyue  ptyzc	tty47	    ttyd8  ttyS3  ttyx0  vcsa4
ptyb3	   ptyq1  ptyuf  ptyzd	tty48	    ttyd9  ttys3  ttyx1  vcsa5
ptyb4	   ptyq2  ptyv0  ptyze	tty49	    ttyda  ttys4  ttyx2  vcsa6
ptyb5	   ptyq3  ptyv1  ptyzf	tty5	    ttydb  ttys5  ttyx3  vcsa7
ptyb6	   ptyq4  ptyv2  ram0	tty50	    ttydc  ttys6  ttyx4  vcsa8
ptyb7	   ptyq5  ptyv3  ram1	tty51	    ttydd  ttys7  ttyx5  video0
ptyb8	   ptyq6  ptyv4  ram10	tty52	    ttyde  ttys8  ttyx6  xconsole
ptyb9	   ptyq7  ptyv5  ram11	tty53	    ttydf  ttys9  ttyx7  zero
ptyba	   ptyq8  ptyv6  ram12	tty54	    ttye0  ttysa  ttyx8
ptybb	   ptyq9  ptyv7  ram13	tty55	    ttye1  ttysb  ttyx9


---

### Post by moore.bryan on 2008-09-06
that confirms what i thought... the toshiba's sd reader is "proprietary" and unsupported by linux (right now). there *seems* to be *some* hope for the 2.6.27 kernel, as per [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/88863") thread, but it doesn't look pretty.

---

### Post by Kuzja on 2008-09-07
Let's hope fot the better then. Thanks for your help anyways.

---

### Post by moore.bryan on 2008-09-07
no worries... best of luck.

---

