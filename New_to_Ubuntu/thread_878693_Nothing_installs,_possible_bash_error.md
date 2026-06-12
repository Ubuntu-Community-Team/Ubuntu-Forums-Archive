---
title: "Nothing installs, possible bash error"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by lastredoubt on 2008-08-03
Hi, 

I don't even know how to begin talking about this problem, hence why I haven't been able to find any information to help me thus far. Firstly, a few days ago my beloved ubuntu, gutsy gibbon, malfunctioned on me and ultimately fixed itself through several reboots and several manual root fsck. Something about bad inodes...

Since then, many things have changed. My desktop no longer looks the way I had customized it, nor were things like Evolution set up with my preferences and email accounts any longer. Other things, however, were still there, like all my files, all my music, firefox bookmarks, history, and so on. So I assumed that everything had worked itself out and somehow my desktop had been changed back to its so-called factory settings. But I've been experiencing some serious errors.

Nothing installs. Software updates download but then don't install. Software manager closes its popup too quickly to even click the view details arrow. apt-get won't install. Synaptic manager will download but won't install. I download packages or source code from a website -- it won't install in terminal or out of it. The thing is -- I get bash errors on everything. bash can't do this or that, find this or that. 

I can't relate anything but symptoms at the moment, in hopes that somebody out there knows what is going on or can help me diagnose the problem more accurately.

---

### Post by ajmorris on 2008-08-03
> **lastredoubt said:**
> Hi, 

I don't even know how to begin talking about this problem, hence why I haven't been able to find any information to help me thus far. Firstly, a few days ago my beloved ubuntu, gutsy gibbon, malfunctioned on me and ultimately fixed itself through several reboots and several manual root fsck. Something about bad inodes...

Since then, many things have changed. My desktop no longer looks the way I had customized it, nor were things like Evolution set up with my preferences and email accounts any longer. Other things, however, were still there, like all my files, all my music, firefox bookmarks, history, and so on. So I assumed that everything had worked itself out and somehow my desktop had been changed back to its so-called factory settings. But I've been experiencing some serious errors.

Nothing installs. Software updates download but then don't install. Software manager closes its popup too quickly to even click the view details arrow. apt-get won't install. Synaptic manager will download but won't install. I download packages or source code from a website -- it won't install in terminal or out of it. The thing is -- I get bash errors on everything. bash can't do this or that, find this or that. 

I can't relate anything but symptoms at the moment, in hopes that somebody out there knows what is going on or can help me diagnose the problem more accurately.

Hi there,
Can you please paste your /var/log/syslog /var/log/messages and sudo dmesg outputs. These will make your post quite long, so please use the [code] tags.

AJ

---

### Post by northern lights on 2008-08-03
It might also be useful to post the output of the very error message you're getting when running 'apt'.

---

### Post by Sef on 2008-08-03
Applications > Accessories > Terminal

What errors do you get with 

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

Please paste them here.

---

### Post by lastredoubt on 2008-08-03
Thanks for your quick replies -- I thoroughly appreciate your help. Apologies for the length of this...

Here's the error output from apt-get upgrade (note that apt-get update returned no errors):

```

arthur@dromosphere:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  wine
The following packages will be upgraded:
  acroread acroread-escript acroread-plugins bind9-host dnsutils evolution
  evolution-common evolution-plugins firefox firefox-gnome-support irb1.8
  language-pack-en language-pack-gnome-en libavcodec1d libavformat1d
  libavutil1d libbind9-30 libdbm-ruby1.8 libdns32 libgdbm-ruby1.8 libisc32
  libisccc30 libisccfg30 liblwres30 libopenssl-ruby1.8 libpcre3 libpcrecpp0
  libpoppler-glib2 libpoppler2 libpostproc1d libpurple0 libreadline-ruby1.8
  libruby1.8 libsmbclient libxslt1.1 linux-generic linux-libc-dev
  linux-restricted-modules-common linux-ubuntu-modules-2.6.22-14-generic
  mozilla-acroread openssl-blacklist pidgin pidgin-data poppler-utils
  python2.5 python2.5-minimal rdoc1.8 ri1.8 ruby1.8 ruby1.8-dev samba-common
  smbclient tzdata xserver-xorg-core xsltproc
55 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 4470kB/112MB of archives.
After unpacking 4391kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://security.ubuntu.com gutsy-security/main python2.5 2.5.1-5ubuntu5.2 [2871kB]
Get: 2 http://gb.archive.ubuntu.com gutsy-updates/main language-pack-en 1:7.10+20080704 [52.0kB]
Get: 3 http://gb.archive.ubuntu.com gutsy-updates/main language-pack-gnome-en 1:7.10+20080704 [46.4kB]
Get: 4 http://security.ubuntu.com gutsy-security/main python2.5-minimal 2.5.1-5ubuntu5.2 [1171kB]
Get: 5 http://security.ubuntu.com gutsy-security/main libxslt1.1 1.1.21-2ubuntu2.2 [220kB]
Get: 6 http://security.ubuntu.com gutsy-security/main xsltproc 1.1.21-2ubuntu2.2 [109kB]
Fetched 4470kB in 8s (550kB/s)                                                 
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by lastredoubt on 2008-08-03
Okay, so the message log seems to be too large to get posted even in Code tabs -- I'm not sure why, but it just won't post. So, here is the output from sudo dmesg -- and if none of this is enough then I will keep trying for the message log. Thanks again!

```
arthur@dromosphere:~$ sudo dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ef40000 (usable)
[    0.000000]  BIOS-e820: 000000001ef40000 - 000000001ef50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ef50000 - 000000001f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126784
[    0.000000]   HighMem    126784 ->   126784
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126784
[    0.000000] On node 0 totalpages: 126784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 958 pages used for memmap
[    0.000000]   Normal zone: 121730 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
[    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 1EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 1EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DSDT 1EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: DBGP 1EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: BOOT 1EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfc10000)
[    0.000000] Built 1 zonelists.  Total pages: 125794
[    0.000000] Kernel command line: root=UUID=2fbc8ac0-1ed5-42e4-8580-86999e0d0276 ro quiet splash vga=791
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (013ed000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2394.080 MHz processor.
[ 3012.434431] Console: colour dummy device 80x25
[ 3012.434803] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 3012.435141] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 3012.447584] Memory: 491276k/507136k available (2015k kernel code, 15312k reserved, 915k data, 364k init, 0k highmem)
[ 3012.447596] virtual kernel memory layout:
[ 3012.447598]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[ 3012.447599]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 3012.447600]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[ 3012.447601]     lowmem  : 0xc0000000 - 0xdef40000   ( 495 MB)
[ 3012.447603]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[ 3012.447604]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[ 3012.447605]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[ 3012.447609] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 3012.447653] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 3012.527544] Calibrating delay using timer specific routine.. 4792.23 BogoMIPS (lpj=9584469)
[ 3012.527575] Security Framework v1.0.0 initialized
[ 3012.527585] SELinux:  Disabled at boot.
[ 3012.527599] Mount-cache hash table entries: 512
[ 3012.527759] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[ 3012.527773] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 3012.527777] CPU: L2 cache: 512K
[ 3012.527779] CPU: Hyper-Threading is disabled
[ 3012.527782] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000
[ 3012.527795] Compat vDSO mapped to ffffe000.
[ 3012.527810] Checking 'hlt' instruction... OK.
[ 3012.543644] SMP alternatives: switching to UP code
[ 3012.543875] Freeing SMP alternatives: 11k freed
[ 3012.544205] Early unpacking initramfs... done
[ 3012.880128] ACPI: Core revision 20070126
[ 3012.880200] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 3012.881943] ACPI: setting ELCR to 0200 (from 0e00)
[ 3012.882101] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.40GHz stepping 09
[ 3012.882109] SMP motherboard not detected.
[ 3012.882112] Local APIC not detected. Using dummy APIC emulation.
[ 3012.882158] Brought up 1 CPUs
[ 3012.882318] Booting paravirtualized kernel on bare hardware
[ 3012.882394] Time: 10:53:36  Date: 07/03/108
[ 3012.882423] NET: Registered protocol family 16
[ 3012.882540] EISA bus registered
[ 3012.882554] ACPI: bus type pci registered
[ 3012.882671] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
[ 3012.882674] PCI: Using configuration type 1
[ 3012.882676] Setting up standard PCI resources
[ 3012.885262] ACPI: EC: Look up EC in DSDT
[ 3012.887888] ACPI: Interpreter enabled
[ 3012.887893] ACPI: (supports S0 S3 S4 S5)
[ 3012.887913] ACPI: Using PIC for interrupt routing
[ 3012.893910] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 3012.893921] PCI: Probing PCI hardware (bus 00)
[ 3012.894406] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[ 3012.894410] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[ 3012.894704] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[ 3012.894830] PCI: Transparent bridge - 0000:00:1e.0
[ 3012.894988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 3012.895029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 3012.896580] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[ 3012.896699] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[ 3012.896819] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[ 3012.896937] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[ 3012.897055] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[ 3012.897174] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[ 3012.897292] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[ 3012.897411] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[ 3012.897661] ACPI: Power Resource [PFAN] (off)
[ 3012.897675] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 3012.897694] pnp: PnP ACPI init
[ 3012.897707] ACPI: bus type pnp registered
[ 3012.899996] pnp: PnP ACPI: found 9 devices
[ 3012.899999] ACPI: ACPI bus type pnp unregistered
[ 3012.900004] PnPBIOS: Disabled by ACPI PNP
[ 3012.900072] PCI: Using ACPI for IRQ routing
[ 3012.900076] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[ 3012.900096] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[ 3012.904955] NET: Registered protocol family 8
[ 3012.904958] NET: Registered protocol family 20
[ 3012.905051] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 3012.905055] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
[ 3012.905058] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[ 3012.905062] pnp: 00:00: iomem range 0x100000-0x1ef3ffff could not be reserved
[ 3012.906912] Time: tsc clocksource has been installed.
[ 3012.935457] PCI: Bus 2, cardbus bridge: 0000:01:0a.0
[ 3012.935460]   IO window: 0000c000-0000c0ff
[ 3012.935465]   IO window: 0000c400-0000c4ff
[ 3012.935469]   PREFETCH window: 28000000-2bffffff
[ 3012.935474]   MEM window: 34000000-37ffffff
[ 3012.935479] PCI: Bus 3, cardbus bridge: 0000:01:0b.0
[ 3012.935481]   IO window: 0000c800-0000c8ff
[ 3012.935486]   IO window: 0000cc00-0000ccff
[ 3012.935491]   PREFETCH window: 2c000000-2fffffff
[ 3012.935496]   MEM window: 38000000-3bffffff
[ 3012.935500] PCI: Bridge: 0000:00:1e.0
[ 3012.935504]   IO window: c000-cfff
[ 3012.935510]   MEM window: cff00000-cfffffff
[ 3012.935515]   PREFETCH window: 28000000-2fffffff
[ 3012.935529] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 3012.935546] PCI: Enabling device 0000:01:0a.0 (0000 -> 0003)
[ 3012.935777] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[ 3012.935781] PCI: setting IRQ 11 as level-triggered
[ 3012.935785] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 3012.935804] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[ 3012.935809] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 3012.935831] NET: Registered protocol family 2
[ 3012.974862] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 3012.974923] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[ 3012.975076] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 3012.975182] TCP: Hash tables configured (established 16384 bind 16384)
[ 3012.975185] TCP reno registered
[ 3012.986936] checking if image is initramfs... it is
[ 3013.438054] Switched to high resolution mode on CPU 0
[ 3013.647568] Freeing initrd memory: 7061k freed
[ 3013.647766] Simple Boot Flag at 0x7c set to 0x1
[ 3013.648000] audit: initializing netlink socket (disabled)
[ 3013.648019] audit(1217760815.964:1): initialized
[ 3013.650460] VFS: Disk quotas dquot_6.5.1
[ 3013.650527] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 3013.650644] io scheduler noop registered
[ 3013.650646] io scheduler anticipatory registered
[ 3013.650649] io scheduler deadline registered
[ 3013.650666] io scheduler cfq registered (default)
[ 3013.650687] Boot video device is 0000:00:02.0
[ 3013.650904] isapnp: Scanning for PnP cards...
[ 3014.003362] isapnp: No Plug & Play device found
[ 3014.037522] Real Time Clock Driver v1.12ac
[ 3014.037640] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 3014.038625] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[ 3014.038838] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[ 3014.038842] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 3014.038851] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[ 3014.039546] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 3014.039839] input: Macintosh mouse button emulation as /class/input/input0
[ 3014.039941] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 3014.055491] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 3014.055499] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 3014.055751] mice: PS/2 mouse device common for all mice
[ 3014.055893] EISA: Probing bus 0 at eisa.0
[ 3014.055901] Cannot allocate resource for EISA slot 1
[ 3014.055918] EISA: Detected 0 cards.
[ 3014.056045] TCP cubic registered
[ 3014.056057] NET: Registered protocol family 1
[ 3014.056084] Using IPI No-Shortcut mode
[ 3014.056333]   Magic number: 4:634:880
[ 3014.056478]   hash matches device ptyx4
[ 3014.057067] Freeing unused kernel memory: 364k freed
[ 3014.088964] input: AT Translated Set 2 keyboard as /class/input/input1
[ 3015.300421] AppArmor: AppArmor initialized<5>audit(1217760817.464:2):  type=1505 info="AppArmor initialized" pid=1185
[ 3015.308376] fuse init (API version 7.8)
[ 3015.314166] Failure registering capabilities with primary security module.
[ 3015.324250] ACPI: Transitioning device [FAN] to D3
[ 3015.324255] ACPI: Transitioning device [FAN] to D3
[ 3015.324259] ACPI: Fan [FAN] (off)
[ 3015.330783] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 3015.332058] ACPI: Thermal Zone [THRM] (60 C)
[ 3016.001914] usbcore: registered new interface driver usbfs
[ 3016.001946] usbcore: registered new interface driver hub
[ 3016.001973] usbcore: registered new device driver usb
[ 3016.003097] USB Universal Host Controller Interface driver v3.0
[ 3016.003434] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[ 3016.003438] PCI: setting IRQ 10 as level-triggered
[ 3016.003442] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[ 3016.003454] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 3016.003458] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 3016.003684] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 3016.003713] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[ 3016.003859] usb usb1: configuration #1 chosen from 1 choice
[ 3016.003890] hub 1-0:1.0: USB hub found
[ 3016.003900] hub 1-0:1.0: 2 ports detected
[ 3016.052156] SCSI subsystem initialized
[ 3016.058592] libata version 2.21 loaded.
[ 3016.088555] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[ 3016.088560] e100: Copyright(c) 1999-2006 Intel Corporation
[ 3016.115074] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[ 3016.115342] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[ 3016.115347] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[ 3016.115365] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 3016.115370] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3016.115428] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[ 3016.115475] ehci_hcd 0000:00:1d.7: debug port 1
[ 3016.115483] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[ 3016.115495] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x30080000
[ 3016.119380] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 3016.119494] usb usb2: configuration #1 chosen from 1 choice
[ 3016.119526] hub 2-0:1.0: USB hub found
[ 3016.119538] hub 2-0:1.0: 6 ports detected
[ 3016.221638] ata_piix 0000:00:1f.1: version 2.11
[ 3016.221919] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[ 3016.221924] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 3016.221979] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 3016.222106] scsi0 : ata_piix
[ 3016.222171] scsi1 : ata_piix
[ 3016.222316] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[ 3016.222320] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.940000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.944000] Time: acpi_pm clocksource has been installed.
[    3.948000] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD0A, max UDMA/100
[    3.948000] ata1.00: 117210240 sectors, multi 0: LBA48 
[    3.964000] ata1.00: configured for UDMA/100
[    4.348000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1431, max UDMA/33
[    4.584000] ata2.00: configured for UDMA/33
[    4.584000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    4.588000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1431 PQ: 0 ANSI: 5
[    4.592000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    4.592000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    4.616000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:EE:67:5E
[    4.636000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    4.636000] sd 0:0:0:0: [sda] Write Protect is off
[    4.636000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.636000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.636000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    4.640000] sd 0:0:0:0: [sda] Write Protect is off
[    4.640000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.640000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.640000]  sda: sda1 sda2 < sda5 >
[    4.696000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.700000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.700000] Uniform CD-ROM driver Revision: 3.20
[    4.700000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.704000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.704000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.972000] Attempting manual resume
[    4.972000] swsusp: Resume From Partition 8:5
[    4.972000] PM: Checking swsusp image.
[    4.976000] PM: Resume from disk failed.
[    5.028000] kjournald starting.  Commit interval 5 seconds
[    5.028000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.992000] Clocksource tsc unstable (delta = -282675780 ns)
[   15.576000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.612000] Netfilter messages via NETLINK v0.30.
[   15.624000] nf_conntrack version 0.5.0 (3962 buckets, 31696 max)
[   17.812000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.860000] agpgart: Detected an Intel 855GM Chipset.
[   17.860000] agpgart: Detected 16252K stolen memory.
[   17.868000] agpgart: AGP aperture is 128M @ 0xd8000000
[   17.984000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.992000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.116000] intel_rng: FWH not detected
[   18.600000] iTCO_vendor_support: vendor-support=0
[   18.600000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   18.600000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
[   18.600000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.688000] Yenta: CardBus bridge found at 0000:01:0a.0 [12a3:ab01]
[   18.688000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.688000] Yenta: Routing CardBus interrupts to PCI
[   18.688000] Yenta TI: socket 0000:01:0a.0, mfunc 0x01000002, devctl 0x60
[   18.704000] input: PC Speaker as /class/input/input2
[   18.920000] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[   18.920000] Socket status: 30000059
[   18.920000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   18.920000] cs: IO port probe 0xc000-0xcfff: clean.
[   18.920000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[   18.920000] pcmcia: parent PCI bridge Memory window: 0x28000000 - 0x2fffffff
[   18.920000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[   19.072000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   19.072000] Socket status: 30000007
[   19.072000] Yenta: Raising subordinate bus# of parent bus (#01) from #03 to #06
[   19.072000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   19.072000] cs: IO port probe 0xc000-0xcfff: clean.
[   19.072000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[   19.072000] pcmcia: parent PCI bridge Memory window: 0x28000000 - 0x2fffffff
[   19.220000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[   19.220000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   19.220000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.420000] input: PS/2 Mouse as /class/input/input3
[   19.464000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   19.556000] pccard: PCMCIA card inserted into slot 0
[   19.556000] cs: memory probe 0xcff00000-0xcfffffff: excluding 0xcff00000-0xcff0ffff 0xcfff0000-0xcfffffff
[   19.560000] pcmcia: registering new device pcmcia0.0
[   19.728000] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.860000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   19.860000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.860000] cs: IO port probe 0x820-0x8ff: clean.
[   19.860000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.860000] cs: IO port probe 0xa00-0xaff: clean.
[   19.860000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   19.864000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.864000] cs: IO port probe 0x820-0x8ff: clean.
[   19.864000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.864000] cs: IO port probe 0xa00-0xaff: clean.
[   19.868000] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.868000] pcmcia: request for exclusive IRQ could not be fulfilled.
[   19.868000] pcmcia: the driver needs updating to supported shared IRQ lines.
[   19.948000] eth1: Hardware identity 0005:0004:0005:0000
[   19.948000] eth1: Station identity  001f:0001:0008:000a
[   19.948000] eth1: Firmware determined as Lucent/Agere 8.10
[   19.948000] eth1: Ad-hoc demo mode supported
[   19.948000] eth1: IEEE standard IBSS ad-hoc mode supported
[   19.948000] eth1: WEP supported, 104-bit key
[   19.948000] eth1: MAC address 00:02:2D:B2:71:99
[   19.948000] eth1: Station name "HERMES I"
[   19.952000] eth1: ready
[   19.952000] eth1: orinoco_cs at 0.0, irq 11, io 0xc100-0xc13f
[   20.144000] intel8x0_measure_ac97_clock: measured 55213 usecs
[   20.144000] intel8x0: clocking to 48000
[   21.352000] lp: driver loaded but no devices found
[   21.404000] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[   21.748000] EXT3 FS on sda1, internal journal
[   23.304000] ACPI: Battery Slot [BAT1] (battery present)
[   24.068000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   24.068000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   24.072000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   24.072000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   24.076000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   24.136000] input: Power Button (FF) as /class/input/input5
[   24.140000] ACPI: Power Button (FF) [PWRF]
[   24.188000] input: Lid Switch as /class/input/input6
[   24.192000] ACPI: Lid Switch [LID]
[   24.236000] input: Power Button (CM) as /class/input/input7
[   24.240000] ACPI: Power Button (CM) [PWRB]
[   24.256000] No dock devices found.
[   24.288000] ACPI: AC Adapter [ADP1] (on-line)
[   24.324000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   26.088000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   26.088000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   26.244000] MC'97 1 converters and GPIO not ready (0xf000)
[   26.420000] eth1: New link status: Disconnected (0002)
[   26.616000] eth1: New link status: Connected (0001)
[   26.844000] Failure registering capabilities with primary security module.
[   27.264000] ppdev: user-space parallel port driver
[   27.980000] audit(1217760843.772:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4810 profile="/usr/sbin/cupsd"
[   28.048000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   28.048000] apm: overridden by ACPI.
[   33.388000] [drm] Initialized drm 1.1.0 20060810
[   33.456000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   33.456000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.456000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   33.460000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   35.216000] eth1: New link status: Disconnected (0002)
[   35.524000] eth1: New link status: Connected (0001)
[   36.408000] NET: Registered protocol family 17
[   52.760000] UDF-fs: No VRS found
[   52.816000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   53.064000] ISO 9660 Extensions: RRIP_1991A
[   71.124000] eth1: New link status: Disconnected (0002)
[   71.468000] eth1: New link status: Connected (0001)
[   89.060000] NET: Registered protocol family 10
[   89.060000] lo: Disabled Privacy Extensions
[   89.060000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.208000] eth1: no IPv6 routers present
[ 1143.672000] eth1: New link status: AP Out of Range (0004)
[ 1151.844000] eth1: New link status: AP In Range (0005)
[ 1157.700000] eth1: New link status: AP Out of Range (0004)
[ 1178.456000] eth1: New link status: AP In Range (0005)
[ 1180.644000] eth1: New link status: AP Out of Range (0004)
[ 1201.512000] eth1: New link status: AP In Range (0005)
[ 1216.688000] eth1: New link status: AP Out of Range (0004)
[ 2446.980000] eth1: New link status: AP In Range (0005)
[ 2447.044000] eth1: New link status: Disconnected (0002)
[ 2549.492000] eth1: New link status: Connected (0001)
[ 2551.628000] eth1: New link status: AP Out of Range (0004)
[ 2826.076000] eth1: New link status: AP In Range (0005)

```

---

### Post by Sef on 2008-08-03
From an [old thread]("http://ubuntuforums.org/archive/index.php/t-365933.html"):

> Rui Pais
February 21st, 2007, 02:03 AM
hi,
you seems to have a corrupted /var/lib/dpkg/available.
Check if the file exist, his a non-zero file and if it's a legible text file. A simple
cat /var/lib/dpkg/available should print on the terminal a list of available packages.

If you have a problem with that you can either, go back to the auto backup file:
/var/lib/dpkg/available-old

(copy that over the broken /var/lib/dpkg/available) and then do a sudo apt-get update

or try:
sudo dpkg --clear-avail
sudo apt-get update

hope one of those help.

---

### Post by lastredoubt on 2008-08-03
Thanks for the quick solutions Sef -- I'm not sure, however, whether I still have the problem. Here's what happened:

```
arthur@dromosphere:~$ cat /var/lib/dpkg/available
cat: /var/lib/dpkg/available: No such file or directory
arthur@dromosphere:~$  /var/lib/dpkg/available-old
bash: /var/lib/dpkg/available-old: Permission denied
arthur@dromosphere:~$ sudo /var/lib/dpkg/available-old
[sudo] password for arthur:
sudo: /var/lib/dpkg/available-old: command not found

```

and then I tried the last option and it seemed to get the job done, meaning it upgraded -- but I kept getting these warnings:

```
55 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/112MB of archives.
After unpacking 4391kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `libgsf0.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `firestarter' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gedit-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpt-1.10.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gedit' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `powertop' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpurple0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgimp2.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pidgin-data' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `deskbar-applet' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwv-1.2-3' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gimp-python' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpt-plugins-alsa' missing, assuming package has no files currently installed.

```

Regardless of these warnings, it seemed the upgrade worked, yet after the fact, I ran the update software tool from my taskbar and in the details of its business it gave the same warnings before doing its thing. Is this a problem?

Thanks

---

### Post by Bodsda on 2008-08-03
To replace the currupt file, run this in a terminal

```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

The cp (copy) command takes a file (the first path after 'cp') and puts it wherever you specify (second path) if the specified path already exists it overwrites it.

-- Just some basic terminal must-knows -- 

Hope this helps

Bodsda

---

### Post by ajmorris on 2008-08-03
> **Bodsda said:**
> To replace the currupt file, run this in a terminal
 
```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```
 
The cp (copy) command takes a file (the first path after 'cp') and puts it wherever you specify (second path) if the specified path already exists it overwrites it.
 
-- Just some basic terminal must-knows -- 
 
Hope this helps
 
Bodsda
 
After running this command it is also a good idea to run ```
sudo dpkg-reconfigure -a
```
 
AJ

---

