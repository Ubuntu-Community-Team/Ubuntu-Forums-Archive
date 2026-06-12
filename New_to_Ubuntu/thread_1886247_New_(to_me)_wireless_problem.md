---
title: "New (to me) wireless problem"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-11-24
Ok, yesterday, I installed Lucid on my new Toshiba C655D-S5300, in dual boot with W7. 
Thanks to the advise received in another thread, I could, after a short while, load the wireless driver, so I could get online.
Today, being that my video wasn't working right (I have a 1024x768 resolution, when I should have 1366x768.), I decided to run the Update Manager, before trying to find another solution in here.

Now, after running UM, my wireless driver is gone. I tried to reinstall it, the same way I did yesterday, but it didn't work.

What should I do?

Here's what lspci said:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510 
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42) 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40) 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) 
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1 
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704 
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718 
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716 
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) 
06:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1) 
```

---

### Post by Sealbhach on 2011-11-24
```
I tried to reinstall it, the same way I did yesterday, but it didn't work.
```

What didn't work? Are you installing with a .deb or a script or compiling it?

.

---

### Post by Inodoro Pereyra on 2011-11-25
I don't have a clue.
In this thread, [http://ubuntuforums.org/showthread.php?t=1885825](http://ubuntuforums.org/showthread.php?t=1885825) you can find all I did the first time. The second time, I just reinstalled the .sh file. 
Sorry I can't be more specific. I don't have much of a clue what I'm doing...:confused:

---

### Post by vegan1 on 2011-11-25
I'm encountering the same problem with Ubuntu on both my laptop and desktop. I think you hit the key for us non-technical users. I don't have the skill to edit configuration files. I think it has something to do with a recent update. Maybe, there is a way for us to re-install the OS, and refuse to update.:popcorn:

How can you get the update manager to go away? Sometimes, that little box gets persistent. This is good that you posted the same problem and your thread is really fresh. That saves me from having to create my own thread. I subscribed. Hopefully, I will be able to understand the answers somebody gives you!

---

### Post by Inodoro Pereyra on 2011-11-25
> **vegan1 said:**
> Hopefully, I will be able to understand the answers somebody gives you!

Hopefully, we both will. :)

---

### Post by vegan1 on 2011-11-25
Last night, I re-installed Ubuntu, and didn't install any of the updates and my connection still dropped. It happens with both wired and wireless. I'm returning to Windows System 7. I'm using System 7, now. I haven't had any dropped connections with system 7. That is what my ISP told me to try. But, I didn't believe them. Now, I realize they were right.:confused:

I have another idea. I start using Arch Linux and it should train me to edit configuration files. Then, after 6 months or a year, I should be able to be ready to tackle the wireless/wired issue.:guitar::lolflag:

---

### Post by Sealbhach on 2011-11-26
That's good thinking vegan1. The thing about Linux is that it works really great if you have hardware that works with it. Most hardware manufacturers now work with the Linux developers so that they can make native drivers for wireless, audio, video etc. Seems like Realtek have not given the Linux developers all the information they need to make a good native Linux driver, hence these awkward workarounds and configurations. I have a Sony Vaio and all my hardware works right out of the box (except the webcam which I can easily get working). 

To Inodoro Pereyra:

Let's see if your wireless driver is still present in your system Please install lshw if you haven't got it already:

```
sudo apt-get install lshw
```

Then run:

```
sudo lshw -C network
```

and copy the result here (please put it in Code # tags for easier reading).

.

---

### Post by mastablasta on 2011-11-26
> **vegan1 said:**
> I'm encountering the same problem with Ubuntu on both my laptop and desktop. I think you hit the key for us non-technical users. I don't have the skill to edit configuration files. I think it has something to do with a recent update. Maybe, there is a way for us to re-install the OS, and refuse to update.:popcorn:

How can you get the update manager to go away? Sometimes, that little box gets persistent. This is good that you posted the same problem and your thread is really fresh. That saves me from having to create my own thread. I subscribed. Hopefully, I will be able to understand the answers somebody gives you!


if it worked but doesn't work after updates, you should review what kind of updates you installed. for example if oyu had to install drivers and perhaps during th eporcess patch the kernel then when the updates include new kernel it will ofcourse be without your drivers/patch. Unlike in windows in Linux drivers are build into the kernel. using a PPA could solve this kind of issue. 

Also since they are part of the kernel you can boto with older kernel and it should porobably work again(hold shift on boot to get into GRUB menu where you can select the kernel you need)

you can also mark which updates you never want to install. you can read what each update does and if there i some update regarding wireless (let say a new driver patch messes things up for you but fixes for others) you just don't update it.

---

### Post by kurt18947 on 2011-11-26
You're using 10.04. I wonder if what you're seeing is related to the problem RealTek 8192SU.  A kernel update could break a working install.  You could run 'dmesg' from a terminal and see if you have something like this showing up.
```

rtl819xU:FirmwareRequest92S(): failed with TCR-Status: 
a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: 
a rtl819xU:FirmwareRequest92S(): failed with TCR-Status: 
a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: 
a rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! 
rtl819xU:FirmwareRequest92S(): failed with TCR-Status: 
a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: 
a rtl819xU:FirmwareRequest92S(): failed with TCR-Status: 
a rtl819xU:FirmwareDownload92S(): failed with TCR-Status: 
a rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! 
```If you see this there's a firmware file missing. The device in question is PCI, the fix I'm familiar with is for a USB device but I think both devices load an RTL817x module.  The other thing you could try would be to create a live install of 11.10.  The problem I had was fixed in 11.04 & 11.10.

---

### Post by Inodoro Pereyra on 2011-11-29
Sorry it took me so long to reply. The last few days have been...complicated.:(

Anyway, here's the info from lshw and dmesg:

```
 *-network UNCLAIMED      
       description: Network controller 
       product: Realtek Semiconductor Co., Ltd. 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: ioport:3000(size=256) memory:f0200000-f0203fff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: c1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list 
       configuration: latency=0 
       resources: memory:f0100000-f013ffff ioport:2000(size=128) 


```

```
[    0.020106] AppArmor: AppArmor initialized 
[    0.020934] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes) 
[    0.032227] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[    0.033602] Mount-cache hash table entries: 256 
[    0.033899] Initializing cgroup subsys ns 
[    0.033909] Initializing cgroup subsys cpuacct 
[    0.033918] Initializing cgroup subsys memory 
[    0.033934] Initializing cgroup subsys devices 
[    0.033940] Initializing cgroup subsys freezer 
[    0.033944] Initializing cgroup subsys net_cls 
[    0.033990] CPU: L1 I Cache: 32K (64 bytes/line), D cache 32K (64 bytes/line) 
[    0.033995] CPU: L2 Cache: 512K (64 bytes/line) 
[    0.034001] CPU 0/0x0 -> Node 0 
[    0.034005] CPU: Physical Processor ID: 0 
[    0.034008] CPU: Processor Core ID: 0 
[    0.034013] mce: CPU supports 6 MCE banks 
[    0.034033] Performance Events: AMD PMU driver. 
[    0.034042] ... version:                0 
[    0.034045] ... bit width:              48 
[    0.034048] ... generic registers:      4 
[    0.034051] ... value mask:             0000ffffffffffff 
[    0.034054] ... max period:             00007fffffffffff 
[    0.034058] ... fixed-purpose events:   0 
[    0.034061] ... event mask:             000000000000000f 
[    0.038280] ACPI: Core revision 20090903 
[    0.060047] ftrace: converting mcount calls to 0f 1f 44 00 00 
[    0.060060] ftrace: allocating 22484 entries in 89 pages 
[    0.070189] Setting APIC routing to flat 
[    0.070555] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.178027] CPU0: AMD E-300 APU with Radeon(tm) HD Graphics stepping 00 
[    0.180000] Booting processor 1 APIC 0x1 ip 0x6000 
[    0.030000] Initializing CPU#1 
[    0.030000] CPU: L1 I Cache: 32K (64 bytes/line), D cache 32K (64 bytes/line) 
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line) 
[    0.030000] CPU 1/0x1 -> Node 0 
[    0.030000] CPU: Physical Processor ID: 0 
[    0.030000] CPU: Processor Core ID: 1 
[    0.330072] CPU1: AMD E-300 APU with Radeon(tm) HD Graphics stepping 00 
[    0.330086] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[    0.340027] Brought up 2 CPUs 
[    0.340031] Total of 2 processors activated (5186.93 BogoMIPS). 
[    0.340515] CPU0 attaching sched-domain: 
[    0.340525]  domain 0: span 0-1 level MC 
[    0.340530]   groups: 0 1 
[    0.340541] CPU1 attaching sched-domain: 
[    0.340545]  domain 0: span 0-1 level MC 
[    0.340548]   groups: 1 0 
[    0.340686] devtmpfs: initialized 
[    0.340827] regulator: core version 0.5 
[    0.340827] Time: 15:29:03  Date: 11/27/11 
[    0.340827] NET: Registered protocol family 16 
[    0.340827] ACPI: bus type pci registered 
[    0.340827] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63 
[    0.340827] PCI: MCFG area at f8000000 reserved in E820 
[    0.345452] PCI: Using MMCONFIG at f8000000 - fbffffff 
[    0.345456] PCI: Using configuration type 1 for base access 
[    0.346935] Trying to unpack rootfs image as initramfs... 
[    0.346979] bio: create slab <bio-0> at 0 
[    0.351640] ACPI: EC: Look up EC in DSDT 
[    0.355579] ACPI: Executed 1 blocks of module-level executable AML code 
[    0.363826] ACPI: BIOS _OSI(Linux) query ignored 
[    0.396864] ACPI: Interpreter enabled 
[    0.396870] ACPI: (supports S0 S3 S4 S5) 
[    0.396914] ACPI: Using IOAPIC for interrupt routing 
[    0.431416] ACPI: Power Resource [PFA1] (off) 
[    0.432161] ACPI: No dock devices found. 
[    0.432558] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.432725] pci 0000:00:01.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff] 
[    0.432736] pci 0000:00:01.0: reg 14 io port: [0x4000-0x40ff] 
[    0.432745] pci 0000:00:01.0: reg 18 32bit mmio: [0xf0300000-0xf033ffff] 
[    0.432786] pci 0000:00:01.0: supports D1 D2 
[    0.432941] pci 0000:00:11.0: reg 10 io port: [0x4138-0x413f] 
[    0.432952] pci 0000:00:11.0: reg 14 io port: [0x414c-0x414f] 
[    0.432963] pci 0000:00:11.0: reg 18 io port: [0x4130-0x4137] 
[    0.432973] pci 0000:00:11.0: reg 1c io port: [0x4148-0x414b] 
[    0.432983] pci 0000:00:11.0: reg 20 io port: [0x4110-0x411f] 
[    0.432994] pci 0000:00:11.0: reg 24 32bit mmio: [0xf034a000-0xf034a3ff] 
[    0.433071] pci 0000:00:12.0: reg 10 32bit mmio: [0xf0349000-0xf0349fff] 
[    0.433174] pci 0000:00:12.2: reg 10 32bit mmio: [0xf0348000-0xf03480ff] 
[    0.433245] pci 0000:00:12.2: supports D1 D2 
[    0.433250] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot 
[    0.433257] pci 0000:00:12.2: PME# disabled 
[    0.433303] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0347000-0xf0347fff] 
[    0.433406] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0346000-0xf03460ff] 
[    0.433476] pci 0000:00:13.2: supports D1 D2 
[    0.433480] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot 
[    0.433486] pci 0000:00:13.2: PME# disabled 
[    0.433626] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0340000-0xf0343fff] 
[    0.433685] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold 
[    0.433692] pci 0000:00:14.2: PME# disabled 
[    0.433913] pci 0000:00:15.0: supports D1 D2 
[    0.434019] pci 0000:00:15.1: supports D1 D2 
[    0.434076] pci 0000:00:16.0: reg 10 32bit mmio: [0xf0345000-0xf0345fff] 
[    0.434179] pci 0000:00:16.2: reg 10 32bit mmio: [0xf0344000-0xf03440ff] 
[    0.434250] pci 0000:00:16.2: supports D1 D2 
[    0.434253] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot 
[    0.434260] pci 0000:00:16.2: PME# disabled 
[    0.434820] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff] 
[    0.434852] pci 0000:02:00.0: reg 18 64bit mmio: [0xf0200000-0xf0203fff] 
[    0.434932] pci 0000:02:00.0: supports D1 D2 
[    0.434935] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.434944] pci 0000:02:00.0: PME# disabled 
[    0.435034] pci 0000:00:15.0: bridge io port: [0x3000-0x3fff] 
[    0.435041] pci 0000:00:15.0: bridge 32bit mmio: [0xf0200000-0xf02fffff] 
[    0.435052] pci 0000:00:15.0: bridge 64bit mmio pref: [0xf0000000-0xf00fffff] 
[    0.435130] pci 0000:06:00.0: reg 10 64bit mmio: [0xf0100000-0xf013ffff] 
[    0.435144] pci 0000:06:00.0: reg 18 io port: [0x2000-0x207f] 
[    0.435231] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.435239] pci 0000:06:00.0: PME# disabled 
[    0.435326] pci 0000:00:15.1: bridge io port: [0x2000-0x2fff] 
[    0.435333] pci 0000:00:15.1: bridge 32bit mmio: [0xf0100000-0xf01fffff] 
[    0.435374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.435727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT] 
[    0.435876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT] 
[    0.436136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT] 
[    0.471521] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.472051] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.472578] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.473079] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.473601] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.473988] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.474346] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.474700] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0 
[    0.474950] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.474978] vgaarb: loaded 
[    0.475190] SCSI subsystem initialized 
[    0.475307] libata version 3.00 loaded. 
[    0.475307] usbcore: registered new interface driver usbfs 
[    0.475307] usbcore: registered new interface driver hub 
[    0.475307] usbcore: registered new device driver usb 
[    0.475307] ACPI: WMI: Mapper loaded 
[    0.475307] PCI: Using ACPI for IRQ routing 
[    0.475307] NetLabel: Initializing 
[    0.475307] NetLabel:  domain hash size = 128 
[    0.475307] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.475307] NetLabel:  unlabeled traffic allowed by default 
[    0.475307] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.475307] hpet0: 3 comparators, 32-bit 14.318180 MHz counter 
[    0.475307] Switching to clocksource tsc 
[    0.479572] AppArmor: AppArmor Filesystem Enabled 
[    0.479572] pnp: PnP ACPI init 
[    0.479572] ACPI: bus type pnp registered 
[    0.479572] pnp: PnP ACPI: found 11 devices 
[    0.479572] ACPI: ACPI bus type pnp unregistered 
[    0.479572] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.479572] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved 
[    0.479572] system 00:09: ioport range 0x400-0x4cf has been reserved 
[    0.479572] system 00:09: ioport range 0x4d0-0x4d1 has been reserved 
[    0.479572] system 00:09: ioport range 0x4d6-0x4d6 has been reserved 
[    0.479572] system 00:09: ioport range 0x680-0x6ff has been reserved 
[    0.479572] system 00:09: ioport range 0x77a-0x77a has been reserved 
[    0.479572] system 00:09: ioport range 0xc00-0xc01 has been reserved 
[    0.479572] system 00:09: ioport range 0xc14-0xc14 has been reserved 
[    0.479572] system 00:09: ioport range 0xc50-0xc52 has been reserved 
[    0.479572] system 00:09: ioport range 0xc6c-0xc6c has been reserved 
[    0.479572] system 00:09: ioport range 0xc6f-0xc6f has been reserved 
[    0.479572] system 00:09: ioport range 0xcd0-0xcdb has been reserved 
[    0.479572] system 00:0a: iomem range 0xff800000-0xff80ffff has been reserved 
[    0.479572] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved 
[    0.479572] system 00:0a: iomem range 0xffe00000-0xffffffff has been reserved 
[    0.483005] pci 0000:00:14.4: PCI bridge, secondary bus 0000:01 
[    0.483010] pci 0000:00:14.4:   IO window: disabled 
[    0.483018] pci 0000:00:14.4:   MEM window: disabled 
[    0.483025] pci 0000:00:14.4:   PREFETCH window: disabled 
[    0.483036] pci 0000:00:15.0: PCI bridge, secondary bus 0000:02 
[    0.483041] pci 0000:00:15.0:   IO window: 0x3000-0x3fff 
[    0.483049] pci 0000:00:15.0:   MEM window: 0xf0200000-0xf02fffff 
[    0.483057] pci 0000:00:15.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff 
[    0.483068] pci 0000:00:15.1: PCI bridge, secondary bus 0000:06 
[    0.483073] pci 0000:00:15.1:   IO window: 0x2000-0x2fff 
[    0.483081] pci 0000:00:15.1:   MEM window: 0xf0100000-0xf01fffff 
[    0.483088] pci 0000:00:15.1:   PREFETCH window: disabled 
[    0.483123]   alloc irq_desc for 16 on node -1 
[    0.483128]   alloc kstat_irqs on node -1 
[    0.483140] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.483148] pci 0000:00:15.0: setting latency timer to 64 
[    0.483162] pci 0000:00:15.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.483169] pci 0000:00:15.1: setting latency timer to 64 
[    0.483177] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.483181] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff] 
[    0.483187] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff] 
[    0.483191] pci_bus 0000:02: resource 1 mem: [0xf0200000-0xf02fffff] 
[    0.483196] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf00fffff] 
[    0.483201] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff] 
[    0.483205] pci_bus 0000:06: resource 1 mem: [0xf0100000-0xf01fffff] 
[    0.483280] NET: Registered protocol family 2 
[    0.483607] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.485966] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
[    0.491658] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.492357] TCP: Hash tables configured (established 524288 bind 65536) 
[    0.492362] TCP reno registered 
[    0.492576] NET: Registered protocol family 1 
[    0.492616] pci 0000:00:01.0: Boot video device 
[    0.610695] Simple Boot Flag at 0x44 set to 0x1 
[    0.611022] Scanning for low memory corruption every 60 seconds 
[    0.611279] audit: initializing netlink socket (disabled) 
[    0.611300] type=2000 audit(1322407742.610:1): initialized 
[    0.627352] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.630003] VFS: Disk quotas dquot_6.5.2 
[    0.630126] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    0.631495] fuse init (API version 7.13) 
[    0.631663] msgmni has been set to 7103 
[    0.632123] alg: No test for stdrng (krng) 
[    0.632244] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.632249] io scheduler noop registered 
[    0.632253] io scheduler anticipatory registered 
[    0.632256] io scheduler deadline registered 
[    0.632346] io scheduler cfq registered (default) 
[    0.632704]   alloc irq_desc for 24 on node -1 
[    0.632708]   alloc kstat_irqs on node -1 
[    0.632729] pcieport 0000:00:15.0: irq 24 for MSI/MSI-X 
[    0.632744] pcieport 0000:00:15.0: setting latency timer to 64 
[    0.632987]   alloc irq_desc for 25 on node -1 
[    0.632990]   alloc kstat_irqs on node -1 
[    0.633004] pcieport 0000:00:15.1: irq 25 for MSI/MSI-X 
[    0.633016] pcieport 0000:00:15.1: setting latency timer to 64 
[    0.633132] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.633260] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.633627] ACPI: AC Adapter [ADP0] (on-line) 
[    0.633744] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0 
[    0.633750] ACPI: Power Button [PWRB] 
[    0.633854] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1 
[    0.635895] ACPI: Lid Switch [LID0] 
[    0.635982] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[    0.635986] ACPI: Power Button [PWRF] 
[    0.636294] fan PNP0C0B:00: registered as cooling_device0 
[    0.636305] ACPI: Fan [FAN1] (off) 
[    0.636970] processor LNXCPU:00: registered as cooling_device1 
[    0.637074] processor LNXCPU:01: registered as cooling_device2 
[    0.642815] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.642829] ACPI: Thermal Zone [THZN] (51 C) 
[    0.645899] Linux agpgart interface v0.103 
[    0.645975] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.648315] brd: module loaded 
[    0.649216] loop: module loaded 
[    0.649396] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    0.650154] Fixed MDIO Bus: probed 
[    0.650217] PPP generic driver version 2.4.2 
[    0.650290] tun: Universal TUN/TAP device driver, 1.6 
[    0.650293] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.650515] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.650632]   alloc irq_desc for 17 on node -1 
[    0.650636]   alloc kstat_irqs on node -1 
[    0.650651] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.650742] ehci_hcd 0000:00:12.2: setting latency timer to 64 
[    0.650749] ehci_hcd 0000:00:12.2: EHCI Host Controller 
[    0.650816] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1 
[    0.650880] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM 
[    0.650930] ehci_hcd 0000:00:12.2: debug port 1 
[    0.650967] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0348000 
[    0.653215] ACPI: Battery Slot [BAT0] (battery present) 
[    0.670555] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00 
[    0.670772] usb usb1: configuration #1 chosen from 1 choice 
[    0.670838] hub 1-0:1.0: USB hub found 
[    0.670856] hub 1-0:1.0: 5 ports detected 
[    0.671068] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.671146] ehci_hcd 0000:00:13.2: setting latency timer to 64 
[    0.671152] ehci_hcd 0000:00:13.2: EHCI Host Controller 
[    0.671224] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2 
[    0.671280] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM 
[    0.671317] ehci_hcd 0000:00:13.2: debug port 1 
[    0.671342] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf0346000 
[    0.690534] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00 
[    0.690755] usb usb2: configuration #1 chosen from 1 choice 
[    0.690827] hub 2-0:1.0: USB hub found 
[    0.690845] hub 2-0:1.0: 5 ports detected 
[    0.691058] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[    0.691143] ehci_hcd 0000:00:16.2: setting latency timer to 64 
[    0.691149] ehci_hcd 0000:00:16.2: EHCI Host Controller 
[    0.691219] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3 
[    0.691274] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM 
[    0.691315] ehci_hcd 0000:00:16.2: debug port 1 
[    0.691340] ehci_hcd 0000:00:16.2: irq 17, io mem 0xf0344000 
[    0.710543] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00 
[    0.710804] usb usb3: configuration #1 chosen from 1 choice 
[    0.710863] hub 3-0:1.0: USB hub found 
[    0.710883] hub 3-0:1.0: 4 ports detected 
[    0.711059] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.711131]   alloc irq_desc for 18 on node -1 
[    0.711135]   alloc kstat_irqs on node -1 
[    0.711149] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    0.711235] ohci_hcd 0000:00:12.0: setting latency timer to 64 
[    0.711241] ohci_hcd 0000:00:12.0: OHCI Host Controller 
[    0.711312] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4 
[    0.711401] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf0349000 
[    0.766366] Freeing initrd memory: 8177k freed 
[    0.774855] usb usb4: configuration #1 chosen from 1 choice 
[    0.774910] hub 4-0:1.0: USB hub found 
[    0.774998] hub 4-0:1.0: 5 ports detected 
[    0.775141] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    0.775221] ohci_hcd 0000:00:13.0: setting latency timer to 64 
[    0.775228] ohci_hcd 0000:00:13.0: OHCI Host Controller 
[    0.775296] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5 
[    0.775371] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0347000 
[    0.834920] usb usb5: configuration #1 chosen from 1 choice 
[    0.834976] hub 5-0:1.0: USB hub found 
[    0.835064] hub 5-0:1.0: 5 ports detected 
[    0.835210] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    0.835290] ohci_hcd 0000:00:16.0: setting latency timer to 64 
[    0.835296] ohci_hcd 0000:00:16.0: OHCI Host Controller 
[    0.835364] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6 
[    0.835439] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0345000 
[    0.894924] usb usb6: configuration #1 chosen from 1 choice 
[    0.894980] hub 6-0:1.0: USB hub found 
[    0.895068] hub 6-0:1.0: 4 ports detected 
[    0.895213] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.895347] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    0.920259] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.920272] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    0.920449] mice: PS/2 mouse device common for all mice 
[    0.920712] rtc_cmos 00:05: RTC can wake from S4 
[    0.920787] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0 
[    0.920846] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs 
[    0.921089] device-mapper: uevent: version 1.0.3 
[    0.921337] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com 
[    0.922090] device-mapper: multipath: version 1.1.0 loaded 
[    0.922100] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    0.923085] cpuidle: using governor ladder 
[    0.923232] cpuidle: using governor menu 
[    0.923925] TCP cubic registered 
[    0.924237] NET: Registered protocol family 10 
[    0.925631] NET: Registered protocol family 17 
[    0.925742] powernow-k8: Found 1 AMD E-300 APU with Radeon(tm) HD Graphics processors (2 cpu cores) (version 2.20.00) 
[    0.926038] powernow-k8:    0 : pstate 0 (1300 MHz) 
[    0.926042] powernow-k8:    1 : pstate 1 (1114 MHz) 
[    0.926045] powernow-k8:    2 : pstate 2 (780 MHz) 
[    0.926050] [Firmware Warn]: powernow-k8: Invalid zero transition latency 
[    0.926281] [Firmware Warn]: powernow-k8: Invalid zero transition latency 
[    0.926723] PM: Resume from disk failed. 
[    0.926748] registered taskstats version 1 
[    0.927388]   Magic number: 3:577:488 
[    0.927589] rtc_cmos 00:05: setting system clock to 2011-11-27 15:29:03 UTC (1322407743) 
[    0.927595] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.927598] EDD information not available. 
[    0.927768] Freeing unused kernel memory: 888k freed 
[    0.928279] Write protecting the kernel read-only data: 7692k 
[    0.953551] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    0.970177] udev: starting version 151 
[    1.010531] usb 2-2: new high speed USB device using ehci_hcd and address 2 
[    1.175269] ahci 0000:00:11.0: version 3.0 
[    1.175294]   alloc irq_desc for 19 on node -1 
[    1.175298]   alloc kstat_irqs on node -1 
[    1.175314] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    1.175494] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 6 Gbps 0x7 impl SATA mode 
[    1.175502] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.185623] usb 2-2: configuration #1 chosen from 1 choice 
[    1.197478] scsi0 : ahci 
[    1.217325] scsi1 : ahci 
[    1.228585] scsi2 : ahci 
[    1.228730] ata1: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a100 irq 19 
[    1.228737] ata2: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a180 irq 19 
[    1.228743] ata3: SATA max UDMA/133 abar m1024@0xf034a000 port 0xf034a200 irq 19 
[    1.245348] Initializing USB Mass Storage driver... 
[    1.245603] scsi3 : SCSI emulation for USB Mass Storage devices 
[    1.245774] usbcore: registered new interface driver usb-storage 
[    1.245780] USB Mass Storage support registered. 
[    1.245791] usb-storage: device found at 2 
[    1.245794] usb-storage: waiting for device to settle before scanning 
[    1.311604] usb 3-4: new high speed USB device using ehci_hcd and address 2 
[    1.523111] usb 3-4: configuration #1 chosen from 1 choice 
[    1.571645] ata3: SATA link down (SStatus 0 SControl 300) 
[    1.750361] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.750408] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.762087] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633J, TF03, max UDMA/100 
[    1.777841] ata2.00: configured for UDMA/100 
[    1.792696] ata1.00: ATA-8: TOSHIBA MK3265GSXN, GH101M, max UDMA/100 
[    1.792704] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
[    1.793999] ata1.00: configured for UDMA/100 
[    1.812213] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GH10 PQ: 0 ANSI: 5 
[    1.812589] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    1.812826] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.813175] sd 0:0:0:0: [sda] Write Protect is off 
[    1.813186] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.813643] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.815134]  sda: 
[    1.818302] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633J  TF03 PQ: 0 ANSI: 5 
[    1.841569] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[    1.841580] Uniform CD-ROM driver Revision: 3.20 
[    1.841834] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    1.841952] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[    1.866314]  sda1 sda2 sda3 < sda5 sda6 > 
[    1.907570] sd 0:0:0:0: [sda] Attached SCSI disk 
[    2.474212] EXT4-fs (sda5): mounted filesystem with ordered data mode 
[    6.241240] usb-storage: device scan complete 
[    6.244458] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS 
[    6.247817] sd 3:0:0:0: Attached scsi generic sg2 type 0 
[    6.255658] sd 3:0:0:0: [sdb] Attached SCSI removable disk 
[   10.965623] udev: starting version 151 
[   11.043609] Adding 4630520k swap on /dev/sda6.  Priority:-1 extents:1 across:4630520k 
[   11.251837] lp: driver loaded but no devices found 
[   11.276223] vga16fb: initializing 
[   11.276233] vga16fb: mapped to 0xffff8800000a0000 
[   11.276361] fb0: VGA16 VGA frame buffer device 
[   11.278120] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0 
[   11.290291] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   11.466322] Linux video capture interface: v2.00 
[   11.525494] acpi device:00: registered as cooling_device3 
[   11.525734] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5 
[   11.525849] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   11.540374] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera (10f1:1a34) 
[   11.556954] input: TOSHIBA Web Camera as /devices/pci0000:00/0000:00:16.2/usb3/3-4/3-4:1.0/input/input6 
[   11.557132] usbcore: registered new interface driver uvcvideo 
[   11.557213] USB Video Class driver (v0.1.0) 
[   11.776435] Console: switching to colour frame buffer device 80x30 
[   11.920095] type=1505 audit(1322425754.483:2):  operation="profile_load" pid=681 name="/sbin/dhclient3" 
[   11.920607] type=1505 audit(1322425754.483:3):  operation="profile_load" pid=681 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   11.920901] type=1505 audit(1322425754.483:4):  operation="profile_load" pid=681 name="/usr/lib/connman/scripts/dhclient-script" 
[   12.008861] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   12.009329] HDA Intel 0000:00:14.2: setting latency timer to 64 
[   12.269650] type=1505 audit(1322425754.833:5):  operation="profile_replace" pid=812 name="/sbin/dhclient3" 
[   12.270272] type=1505 audit(1322425754.833:6):  operation="profile_replace" pid=812 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   12.270577] type=1505 audit(1322425754.833:7):  operation="profile_replace" pid=812 name="/usr/lib/connman/scripts/dhclient-script" 
[   12.272473] type=1505 audit(1322425754.843:8):  operation="profile_load" pid=811 name="/usr/share/gdm/guest-session/Xsession" 
[   12.292248] type=1505 audit(1322425754.863:9):  operation="profile_load" pid=815 name="/usr/lib/cups/backend/cups-pdf" 
[   12.304092] type=1505 audit(1322425754.873:10):  operation="profile_load" pid=813 name="/usr/bin/evince" 
[   12.310808] type=1505 audit(1322425754.873:11):  operation="profile_load" pid=815 name="/usr/sbin/cupsd" 
[   12.648823] input: PS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7 
[   12.721791] ppdev: user-space parallel port driver 
[   13.104897] CPU0 attaching NULL sched-domain. 
[   13.104911] CPU1 attaching NULL sched-domain. 
[   13.171540] CPU0 attaching sched-domain: 
[   13.171550]  domain 0: span 0-1 level MC 
[   13.171555]   groups: 0 1 
[   13.171567] CPU1 attaching sched-domain: 
[   13.171571]  domain 0: span 0-1 level MC 
[   13.171574]   groups: 1 0 
[   15.865173] CPU0 attaching NULL sched-domain. 
[   15.865187] CPU1 attaching NULL sched-domain. 
[   15.922520] CPU0 attaching sched-domain: 
[   15.922531]  domain 0: span 0-1 level MC 
[   15.922537]   groups: 0 1 
[   15.922550] CPU1 attaching sched-domain: 
[   15.922554]  domain 0: span 0-1 level MC 
[   15.922558]   groups: 1 0 
[  137.950366] usb 1-1: new high speed USB device using ehci_hcd and address 2 
[  138.108322] usb 1-1: configuration #1 chosen from 1 choice 
[  138.109740] scsi4 : SCSI emulation for USB Mass Storage devices 
[  138.110200] usb-storage: device found at 2 
[  138.110207] usb-storage: waiting for device to settle before scanning 
[  143.112362] usb-storage: device scan complete 
[  143.143823] scsi 4:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS 
[  143.148110] sd 4:0:0:0: Attached scsi generic sg3 type 0 
[  145.498487] sd 4:0:0:0: [sdc] 15638528 512-byte logical blocks: (8.00 GB/7.45 GiB) 
[  145.500259] sd 4:0:0:0: [sdc] Write Protect is off 
[  145.500275] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00 
[  145.500283] sd 4:0:0:0: [sdc] Assuming drive cache: write through 
[  145.509859] sd 4:0:0:0: [sdc] Assuming drive cache: write through 
[  145.509880]  sdc: sdc1 sdc2 < sdc5 > 
[  145.987641] sd 4:0:0:0: [sdc] Assuming drive cache: write through 
[  145.987659] sd 4:0:0:0: [sdc] Attached SCSI removable disk 
[  159.406765] EXT4-fs (sdc1): ext4_orphan_cleanup: deleting unreferenced inode 131385 
[  159.407027] EXT4-fs (sdc1): ext4_orphan_cleanup: deleting unreferenced inode 131367 
[  159.407076] EXT4-fs (sdc1): 2 orphan inodes deleted 
[  159.407086] EXT4-fs (sdc1): recovery complete 
[  159.488777] EXT4-fs (sdc1): mounted filesystem with ordered data mode 

```

I honestly hope you guys know how to read this stuff...

---

