---
title: "Ubuntu not booting after upgrade"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by quarkhirad on 2008-10-08
My system had ubuntu 6.06 Lts hence i decided yesterday that it was time to upgrade to 8.04. Hence i went to update manager made sure the latest updates for 6.06 were installed then clicked on the upgrade button. It downloaded all the packages and then it started installing very smoothly. When suddenly it asked me whether it should change or keep a particular config file ( i dont remember its name ). I told it to change. It then suddenly froze. I waited for some time and then relized that the packages were getting installed. Basically my mouse and keyboard were responding but i could not open any application nor switch from one virtual desktop to another. But still in the terminal of the upgrade manager some lib files were upgraded. One of them was libegroupwise and kdelibs. It took about 25 min for each to be installed and then the other started. I just left and came back after 12 hrs (i left it overnight). When i came back there was a blank screen. When i pressed ctrl+alt+f1 it gave me the following:

Booting 'ubuntu, KErnel 2.6.15-52-686'

root (hd0,0)
Filesystem type is ext2fs, Partition type 0x83
kernel /boot/vmlinuz-2.6.15-52-686 root+/dev/hda1 ro quiet splash
    [Linux-bzImage, setup=0x1705e2]
initrd /boot/initrd.img-2.6.15-52-686
    [linux-initrd @ 0x1f62c000, 0x6b3a31 bytes]
savedefault
boot
uncompressing linux... ok, booting the kernel.

when i hard shut down the system as ctrl+alt+del dint work and rebooted i choose kernel verssion 2.6.15-52-686. i got the text output above and then the graphical usplash of unbuntu and then at the bottom it said

loading essential drivers           ok
mounting root file system           ok

and then the screen just goes blank. 

when i boot in recovery mode

it starts up and then after detecting my HDD it finds EHCI host controller 

Then 
Begin:Running /scripts/init-bottom ...
[17179578.588000] kjournald starting. commit interval 5 seconds
done.

and then nothing happens i just have a blinking courser. There is no prompt for me to even type any commands 

I have tried the above with other kernel versions in my grub but it is the same.

  
Can someone please help me restore the system as it is used as a file server in our college. 

Desktop config

 intel p4 1.73Ghz
 512Mb ram
 40 Gb HDD
 
thank you

---

### Post by Peter09 on 2008-10-08
I suspect that you just need to reconfigure your X server. However try typing 
```
startx
```
at the command prompt in safe mode and see what happens. It may get you back into a GUI from which you can recover.

---

### Post by quarkhirad on 2008-10-08
dear peter

There is no command prompt in recovery mode and when i typed startx nothing happened.

Any other solution

---

### Post by Peter09 on 2008-10-08
Can you boot the system using a liveCD, I believe there is a recover system option on that.

---

### Post by celticbhoy on 2008-10-08
Have you tried 8.04 from a live disk to make sure the server will run it?

---

### Post by quarkhirad on 2008-10-08
dear celticbhoy

Hi. I did not understand what u said can u please be more specific or give me more details.

Please remember i am not a newbie just a beginner.

---

### Post by celticbhoy on 2008-10-08
Sorry, what I meant was can you download the live disk version of 8.04 and burn it. Then boot the server from this to see if it will work. I have checked on google and this is a recurring problem, with no solutions posted, but some people have had success after re-installing. So I think the first step you should take is to check whether this version of Ubuntu will work on your hardware.

---

### Post by quarkhirad on 2008-10-08
dear peter

yes i can. However i only have the alternate cd. will that do

---

### Post by celticbhoy on 2008-10-08
The alternate cd is not a live cd, so will not boot only install.

---

### Post by celticbhoy on 2008-10-08
If you can get a hold of any live CD then you could access the servers file system and see what scripts are in the directory - that will narrow down the cuase of the problem.

---

### Post by Ryadt on 2008-10-08
Can you boot in recovery mode?
Also post the specs of your pc.

---

### Post by quarkhirad on 2008-10-08
dear celticbhoy

Yeah i have ubuntu 7.10 cd 

i have booted it and mounted all the partitions. Now what do i do

---

### Post by celticbhoy on 2008-10-08
Fire up a terminal and navigate to :-

/etc/initramfs-tools/scripts/init-bottom

and post the output of ls

---

### Post by quarkhirad on 2008-10-08
Dear ryadt

No as i mentioned earlier when i boot into recovery mode it goes upto this 


Begin:Running /scripts/init-bottom ...
[17179578.588000] kjournald starting. commit interval 5 seconds
done.

and then nothing happens i just have a blinking courser. There is no prompt for me to even type any commands.

as far as tech specs her is output of dmesg

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fcf0000 (usable)
[    0.000000]  BIOS-e820: 000000001fcf0000 - 000000001fcfb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fcfb000 - 000000001fd00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fd00000 - 000000001fe80000 (usable)
[    0.000000]  BIOS-e820: 000000001fe80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f62f0
[    0.000000] Entering add_active_range(0, 0, 130688) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130688
[    0.000000]   HighMem    130688 ->   130688
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130688
[    0.000000] On node 0 totalpages: 130688
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125603 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62C0 checksum 0
[    0.000000] ACPI: RSDP 000F62C0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FCF7641, 0034 (r1 PTLTD    RSDT    60400D0  LTP        0)
[    0.000000] ACPI: FACP 1FCFAEE2, 0074 (r1 IBM    NETVISTA  60400D0 PTL         1)
[    0.000000] ACPI: DSDT 1FCF7675, 386D (r1    IBM Yelotail  60400D0 MSFT  100000D)
[    0.000000] ACPI: FACS 1FCFBFC0, 0040
[    0.000000] ACPI: TCPA 1FCFAF56, 0032 (r1 IBM    NETVISTA  60400D0 PTL         1)
[    0.000000] ACPI: APIC 1FCFAF88, 0050 (r1 PTLTD  	 APIC    60400D0  LTP        0)
[    0.000000] ACPI: BOOT 1FCFAFD8, 0028 (r1 PTLTD  $SBFTBL$  60400D0  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 129667
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1694.589 MHz processor.
[   52.426331] Console: colour VGA+ 80x25
[   52.426787] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   52.427295] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   52.446200] Memory: 506380k/522752k available (2015k kernel code, 15676k reserved, 916k data, 364k init, 0k highmem)
[   52.446218] virtual kernel memory layout:
[   52.446219]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   52.446221]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   52.446223]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   52.446224]     lowmem  : 0xc0000000 - 0xdfe80000   ( 510 MB)
[   52.446226]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   52.446228]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   52.446229]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   52.446234] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   52.446291] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   52.526285] Calibrating delay using timer specific routine.. 3392.78 BogoMIPS (lpj=6785574)
[   52.526321] Security Framework v1.0.0 initialized
[   52.526332] SELinux:  Disabled at boot.
[   52.526352] Mount-cache hash table entries: 512
[   52.527125] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   52.527147] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   52.527152] CPU: L2 cache: 256K
[   52.527156] CPU: Hyper-Threading is disabled
[   52.527160] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   52.527179] Compat vDSO mapped to ffffe000.
[   52.527199] Checking 'hlt' instruction... OK.
[   52.542499] SMP alternatives: switching to UP code
[   52.542860] Freeing SMP alternatives: 11k freed
[   52.543391] Early unpacking initramfs... done
[   53.057295] ACPI: Core revision 20070126
[   53.057378] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   53.064000] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   53.064065] Total of 1 processors activated (3392.78 BogoMIPS).
[   53.064214] ENABLING IO-APIC IRQs
[   53.064416] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   53.210052] Brought up 1 CPUs
[   53.210249] Booting paravirtualized kernel on bare hardware
[   53.210342] Time: 11:39:45  Date: 09/08/108
[   53.210384] NET: Registered protocol family 16
[   53.210556] EISA bus registered
[   53.210579] ACPI: bus type pci registered
[   53.211167] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=2
[   53.211171] PCI: Using configuration type 1
[   53.211173] Setting up standard PCI resources
[   53.226044] ACPI: EC: Look up EC in DSDT
[   53.243282] ACPI: Interpreter enabled
[   53.243290] ACPI: (supports S0 S1 S3 S4 S5)
[   53.243324] ACPI: Using IOAPIC for interrupt routing
[   53.285197] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   53.285209] PCI: Probing PCI hardware (bus 00)
[   53.285784] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   53.285787] * this clock source is slow. If you are sure your timer does not have
[   53.285789] * this bug, please use "acpi_pm_good" to disable the workaround
[   53.285848] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   53.285853] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   53.286191] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   53.286286] PCI: Transparent bridge - 0000:00:1e.0
[   53.286322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   53.286639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[   53.358037] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   53.358192] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   53.358338] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   53.358484] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   53.358635] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   53.358787] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   53.358938] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   53.359090] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   53.359293] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.359320] pnp: PnP ACPI init
[   53.359339] ACPI: bus type pnp registered
[   53.414086] pnp: PnP ACPI: found 15 devices
[   53.414094] ACPI: ACPI bus type pnp unregistered
[   53.414101] PnPBIOS: Disabled by ACPI PNP
[   53.414227] PCI: Using ACPI for IRQ routing
[   53.414233] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   53.419045] NET: Registered protocol family 8
[   53.419049] NET: Registered protocol family 20
[   53.419217] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   53.419223] pnp: 00:01: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   53.419228] pnp: 00:01: iomem range 0xeffffc00-0xefffffff has been reserved
[   53.421900] Time: tsc clocksource has been installed.
[   53.449854] PCI: Bridge: 0000:00:1e.0
[   53.449859]   IO window: 2000-2fff
[   53.449867]   MEM window: c0100000-c01fffff
[   53.449873]   PREFETCH window: disabled.
[   53.449896] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   53.449920] NET: Registered protocol family 2
[   53.489940] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   53.490020] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   53.490215] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   53.490415] TCP: Hash tables configured (established 16384 bind 16384)
[   53.490421] TCP reno registered
[   53.502135] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   53.986667]  it is
[   54.516024] Freeing initrd memory: 7305k freed
[   54.516238] Simple Boot Flag at 0x6c set to 0x1
[   54.516683] audit: initializing netlink socket (disabled)
[   54.516705] audit(1223465985.872:1): initialized
[   54.520546] VFS: Disk quotas dquot_6.5.1
[   54.520659] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   54.520859] io scheduler noop registered
[   54.520864] io scheduler anticipatory registered
[   54.520867] io scheduler deadline registered
[   54.520905] io scheduler cfq registered (default)
[   54.520926] Boot video device is 0000:00:02.0
[   54.521409] isapnp: Scanning for PnP cards...
[   54.875756] isapnp: No Plug & Play device found
[   54.956527] Real Time Clock Driver v1.12ac
[   54.956690] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.956811] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.957304] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.958836] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.959479] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.960934] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.961375] input: Macintosh mouse button emulation as /class/input/input0
[   54.961539] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
[   54.963545] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.963558] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.963922] mice: PS/2 mouse device common for all mice
[   54.964137] EISA: Probing bus 0 at eisa.0
[   54.964151] Cannot allocate resource for EISA slot 1
[   54.964155] Cannot allocate resource for EISA slot 2
[   54.964187] EISA: Detected 0 cards.
[   54.964357] TCP cubic registered
[   54.964379] NET: Registered protocol family 1
[   54.964417] Using IPI No-Shortcut mode
[   54.964690]   Magic number: 12:921:680
[   54.965600] Freeing unused kernel memory: 364k freed
[   54.997226] input: AT Translated Set 2 keyboard as /class/input/input1
[   56.370744] AppArmor: AppArmor initialized<5>audit(1223465987.372:2):  type=1505 info="AppArmor initialized" pid=1179
[   56.386660] fuse init (API version 7.8)
[   56.397405] Failure registering capabilities with primary security module.
[   56.422610] ACPI: Processor [CPU0] (supports 8 throttling states)
[   56.425648] ACPI: Thermal Zone [THM0] (43 C)
[   57.558554] usbcore: registered new interface driver usbfs
[   57.558596] usbcore: registered new interface driver hub
[   57.558641] usbcore: registered new device driver usb
[   57.560370] USB Universal Host Controller Interface driver v3.0
[   57.560479] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   57.560495] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   57.560501] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   57.560714] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   57.560755] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[   57.560974] usb usb1: configuration #1 chosen from 1 choice
[   57.561019] hub 1-0:1.0: USB hub found
[   57.561035] hub 1-0:1.0: 2 ports detected
[   57.653475] SCSI subsystem initialized
[   57.663227] libata version 2.21 loaded.
[   57.665686] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   57.665704] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   57.665710] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   57.665750] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   57.665785] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[   57.665950] usb usb2: configuration #1 chosen from 1 choice
[   57.665996] hub 2-0:1.0: USB hub found
[   57.666011] hub 2-0:1.0: 2 ports detected
[   57.767897] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   57.767915] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   57.767921] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   57.767964] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   57.767999] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   57.768175] usb usb3: configuration #1 chosen from 1 choice
[   57.768220] hub 3-0:1.0: USB hub found
[   57.768233] hub 3-0:1.0: 2 ports detected
[   57.804840] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   57.804846] e100: Copyright(c) 1999-2006 Intel Corporation
[   57.872322] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   57.872345] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   57.872353] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   57.872416] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   57.872471] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   57.872487] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xc0080000
[   57.876367] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   57.876521] usb usb4: configuration #1 chosen from 1 choice
[   57.876569] hub 4-0:1.0: USB hub found
[   57.876585] hub 4-0:1.0: 6 ports detected
[   57.966951] Floppy drive(s): fd0 is 1.44M
[   57.984494] ata_piix 0000:00:1f.1: version 2.11
[   57.984521] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   57.984583] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   57.984723] scsi0 : ata_piix
[   57.984809] scsi1 : ata_piix
[   57.984972] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[   57.984978] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[   58.025840] FDC 0 is a post-1991 82077
[   58.172053] ata1.00: ATA-6: IC35L060AVV207-0, V22OA66A, max UDMA/100
[   58.172060] ata1.00: 78156288 sectors, multi 16: LBA48 
[   58.196043] ata1.00: configured for UDMA/100
[   58.555473] ata2.00: ATAPI: CD-ROM F567E, VER 00G9, max UDMA/33
[   58.767467] ata2.00: configured for UDMA/33
[   58.767698] scsi 0:0:0:0: Direct-Access     ATA      IC35L060AVV207-0 V22O PQ: 0 ANSI: 5
[   58.778925] scsi 1:0:0:0: CD-ROM            CD-ROM   F567E            00G9 PQ: 0 ANSI: 5
[   58.779831] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   58.805227] e100: eth0: e100_probe: addr 0xc0100000, irq 20, MAC addr 00:09:6B:C4:0D:85
[   58.837842] sd 0:0:0:0: [sda] 78156288 512-byte hardware sectors (40016 MB)
[   58.837889] sd 0:0:0:0: [sda] Write Protect is off
[   58.837894] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   58.837924] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.838033] sd 0:0:0:0: [sda] 78156288 512-byte hardware sectors (40016 MB)
[   58.838051] sd 0:0:0:0: [sda] Write Protect is off
[   58.838055] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   58.838083] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   58.838091]  sda:end_request: I/O error, dev fd0, sector 0
[   58.858789]  sda1 sda2 sda3 sda4
[   58.877739] sd 0:0:0:0: [sda] Attached SCSI disk
[   58.886227] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   58.886261] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   58.932665] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   58.932674] Uniform CD-ROM driver Revision: 3.20
[   58.933105] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   59.910562] end_request: I/O error, dev fd0, sector 0
[   60.076683] kjournald starting.  Commit interval 5 seconds
[   60.076706] EXT3-fs: mounted filesystem with ordered data mode.
[   60.141597] EXT3-fs: INFO: recovery required on readonly filesystem.
[   60.141605] EXT3-fs: write access will be enabled during recovery.
[   61.652203] kjournald starting.  Commit interval 5 seconds
[   61.652230] EXT3-fs: recovery complete.
[   61.656557] EXT3-fs: mounted filesystem with ordered data mode.
[   62.080792] EXT3-fs: INFO: recovery required on readonly filesystem.
[   62.080801] EXT3-fs: write access will be enabled during recovery.
[   62.370004] kjournald starting.  Commit interval 5 seconds
[   62.370030] EXT3-fs: recovery complete.
[   62.370603] EXT3-fs: mounted filesystem with ordered data mode.
[   63.067835] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.115323] ISO 9660 Extensions: RRIP_1991A
[   63.363607] Registering unionfs 1.4
[   63.363613] unionfs: debugging is not enabled
[   63.384136] loop: module loaded
[   63.651474] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[  138.029387] Linux agpgart interface v0.102 (c) Dave Jones
[  138.073810] agpgart: Detected an Intel 830M Chipset.
[  138.073933] agpgart: Detected 892K stolen memory.
[  138.092453] agpgart: AGP aperture is 128M @ 0x88000000
[  138.192516] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[  139.146562] iTCO_vendor_support: vendor-support=0
[  139.148435] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  139.260571] input: PS/2 Generic Mouse as /class/input/input2
[  139.263146] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x1060)
[  139.263267] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  139.495483] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  139.622210] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  139.721695] input: PC Speaker as /class/input/input3
[  139.875259] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[  139.875264]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[  139.875266]  you are certain that your <4>intel_rng: system has a functional
[  139.875268]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[  140.055799] parport_pc 00:0e: reported by Plug and Play ACPI
[  140.055859] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  141.241074] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  141.241113] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  141.612510] intel8x0_measure_ac97_clock: measured 54630 usecs
[  141.612516] intel8x0: clocking to 48000
[  143.769830] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[  146.965166] No dock devices found.
[  147.426189] input: Power Button (FF) as /class/input/input4
[  147.433769] ACPI: Power Button (FF) [PWRF]
[  147.497063] input: Power Button (CM) as /class/input/input5
[  147.504622] ACPI: Power Button (CM) [PWRB]
[  155.129504] lp0: using parport0 (interrupt-driven).
[  155.276645] ppdev: user-space parallel port driver
[  157.818254] IBM machine detected. Enabling interrupts during APM calls.
[  157.818264] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  157.818268] apm: overridden by ACPI.
[  158.319011] Failure registering capabilities with primary security module.
[  159.353783] Bluetooth: Core ver 2.11
[  159.353982] NET: Registered protocol family 31
[  159.353987] Bluetooth: HCI device and connection manager initialized
[  159.353992] Bluetooth: HCI socket layer initialized
[  159.513258] Bluetooth: L2CAP ver 2.8
[  159.513265] Bluetooth: L2CAP socket layer initialized
[  159.803110] Bluetooth: RFCOMM socket layer initialized
[  159.803299] Bluetooth: RFCOMM TTY layer initialized
[  159.803304] Bluetooth: RFCOMM ver 1.8
[  169.093284] [drm] Initialized drm 1.1.0 20060810
[  169.126119] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  169.130129] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  384.691182] kjournald starting.  Commit interval 5 seconds
[  384.691705] EXT3 FS on sda1, internal journal
[  384.691835] EXT3-fs: mounted filesystem with ordered data mode.
[  399.458534] kjournald starting.  Commit interval 5 seconds
[  399.458715] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  399.459224] EXT3 FS on sda3, internal journal
[  399.459352] EXT3-fs: mounted filesystem with ordered data mode.
[  404.341597] kjournald starting.  Commit interval 5 seconds
[  404.341777] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  404.342295] EXT3 FS on sda4, internal journal
[  404.342421] EXT3-fs: mounted filesystem with ordered data mode.
[ 1259.371817] NET: Registered protocol family 10
[ 1259.372345] lo: Disabled Privacy Extensions
[ 1259.372689] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1280.106768] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1280.107368] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1291.009052] eth0: no IPv6 routers present

---

### Post by celticbhoy on 2008-10-08
Just done a little research on Kjournald and found that this is the journalling system for ext3 formatted partitions, your problem might be as simple as to reboot the server now thaT YOU HAVE MOUNTED THE PARTITIONS FROM LIVE CD. The problem may have been cuasewd by the hard reset that you had to perform as the drives would not have been unmounted.

---

### Post by celticbhoy on 2008-10-08
If that does not work you could try and fsck the drives from the live CD

---

### Post by quarkhirad on 2008-10-08
dear celticbhoy 

There are no files in the folder 

ubuntu@ubuntu:~$ cd /media/disk1/etc/initramfs-tools/scripts/init-bottom/
ubuntu@ubuntu:/media/disk1/etc/initramfs-tools/scripts/init-bottom$ ls -a
.  ..
ubuntu@ubuntu:/media/disk1/etc/initramfs-tools/scripts/init-bottom$


I have mounted the root partition

code
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/disk1

---

### Post by celticbhoy on 2008-10-08
Yeah sorry I was focusing on the wrong part of your first post. As I say I think that the problem is down to the hard reset. If you cant reboot correctly now the reboot to the live CD again and run fsck on the drives. That should sort it.

---

### Post by quarkhirad on 2008-10-08
Hey this is what i got from fsck the partitions 

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean, 177002/1221600 files, 2215947/2441872 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3 has been mounted 145 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda3: 651/1064960 files (10.8% non-contiguous), 720380/2100498 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3: clean, 651/1064960 files, 720380/2100498 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda4 has been mounted 145 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda4: 3647/2492064 files (18.0% non-contiguous), 4177054/4982158 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 3647/2492064 files, 4177054/4982158 blocks

---

### Post by celticbhoy on 2008-10-08
You may need to use the -f option to force a check on the file systems that it thinks are clean.

---

### Post by quarkhirad on 2008-10-08
Sorry but problem still persists :( . any more ideas

---

### Post by celticbhoy on 2008-10-08
A couple of points after looking throught your dmesg output.

1 it says to use e2fsck - I dont know if this will make a differance from just fsck.

2 It stops after encountering a problem with your ethernet eth0, is your ethernet on board, or an installed card?

---

### Post by quarkhirad on 2008-10-08
The force option gave the following 

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 177003/1221600 files (3.1% non-contiguous), 2215948/2441872 blocks
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda2
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda3: 651/1064960 files (10.8% non-contiguous), 720380/2100498 blocks
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda4
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda4: 3647/2492064 files (18.0% non-contiguous), 4177054/4982158 blocks

and after resstarting the problem is still persisting

Any new ideas????

---

### Post by quarkhirad on 2008-10-08
my ethernet card is onboard.

---

### Post by celticbhoy on 2008-10-08
Just found this post which looks like it may help you :-

[https://answers.launchpad.net/ubuntu/+question/3548](https://answers.launchpad.net/ubuntu/+question/3548)

Give it a good read and the values which corespond to yours.
If that does not work try and dissable the onboard ethernet and see if the system boots

---

### Post by celticbhoy on 2008-10-08
Just found this post which looks like it may help you :-

[https://answers.launchpad.net/ubuntu/+question/3548](https://answers.launchpad.net/ubuntu/+question/3548)

Give it a good read and the values which corespond to yours.
If that does not work try and dissable the onboard ethernet and see if the system boots

---

### Post by quarkhirad on 2008-10-08
Sorry buddy both dint work thanks. any more ideas

---

### Post by celticbhoy on 2008-10-08
The only other thing I can think of is to boot from the live CD again, and run gparted. Once in select the swap partition and delete it. Apply the changes and remake it again and format as swap. I am not sure but you may have to run mkswap from the terminal to activate the swap file. Just be careful and make sure you use the right partition.

---

### Post by celticbhoy on 2008-10-08
Sorry I meant to say if that does not work I would start a new thread listing the fsck error on the swap drive and the fact that boot stops at the ethernet card. And see if someone more intelegent than I can help you out.

---

### Post by b0b138 on 2008-10-08
Try selecting a different kernel at boot since according to your first post your trying to boot hardy on an old kernel

---

### Post by quarkhirad on 2008-10-08
ok buddy it failed. Ok thanks. i shall start a recovery of data and then reinstall. Thanks for trying

---

### Post by celticbhoy on 2008-10-08
Thats ok. Just sorry I could not be of any better help.

---

### Post by quarkhirad on 2008-10-08
dear b0b138

well these are the kernels i have in my grub
2.6.15-52-686
2.6.15-51-686
2.6.15-29-686
2.6.15-23-686

which one do i use

---

### Post by Keen101 on 2008-10-08
> well these are the kernels i have in my grub
2.6.15-52-686
2.6.15-51-686
2.6.15-29-686
2.6.15-23-686

which one do i use 


Try any kernel except the latest one (which might have problems), which is probably near the top. Try the second from the top. Or you could try all of them one at a time.

Maybe one of the older recover modes will work too. not sure.

---

### Post by celticbhoy on 2008-10-08
Just wondering how you got on, if you managed to fix it or had to re-install?

---

### Post by quarkhirad on 2008-10-10
OK guys i got a 8.04 cd the did the following 

sudo mount /dev/sda1 /media
chroot /media
apt-get update

Now the problem is that i am connecting to the net via a proxy
Now how do i do it. The problem is that last time i had this problem i had posted a thread and i got a reply 
[http://ubuntuforums.org/showthread.php?t=355613](http://ubuntuforums.org/showthread.php?t=355613)
The problem is that i am not able to view the site do to some problems can someone help 
hence it fails to get the packages however at the end it says
 
dpkg some errors found please run dpkg --configure -a 

I dont remember the exact statement but i remember the command 

So i did

dpkg --configure -a

and it started configuring the packages but some of them failed so i restarted the comp in hope of it working. but it dint. Hence i again i  did the following 

sudo mount /dev/sda1 /media
chroot /media
apt-get update
dpkg --cofigure -a

and this is the output i get 

root@ubuntu:/# dpkg --configure -a
Setting up samba (3.0.28a-1ubuntu4.5) ...
invoke-rc.d: initscript openbsd-inetd, action "force-reload" failed.
 * Starting Samba daemons                                                       start-stop-daemon: nothing in /proc - not mounted? (Success)
                                                                         [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of policykit:
 policykit depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gnome:
 bluez-gnome depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing bluez-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
Setting up openbsd-inetd (0.20050402-6) ...
invoke-rc.d: initscript openbsd-inetd, action "stop" failed.
invoke-rc.d: initscript openbsd-inetd, action "start" failed.
dpkg: error processing openbsd-inetd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up winbind (3.0.28a-1ubuntu4.5) ...
 * Starting the Winbind daemon winbind                                          start-stop-daemon: nothing in /proc - not mounted? (Success)
                                                                         [fail]
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
 hal depends on policykit (>= 0.7); however:
  Package policykit is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
Setting up console-setup (1.21ubuntu8) ...
invoke-rc.d: initscript console-setup, action "start" failed.
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on winbind; however:
  Package winbind is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dhcdbd:
 dhcdbd depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing dhcdbd (--configure):
 dependency problems - leaving unconfigured
Setting up termnetd (3.3-9) ...
invoke-rc.d: initscript termnetd, action "start" failed.
dpkg: error processing termnetd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
Setting up at (3.1.10ubuntu4) ...
invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
Setting up openssh-server (1:4.7p1-8ubuntu1.2) ...
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-gnome-module:
 libgail-gnome-module depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgail-gnome-module (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on consolekit; however:
  Package consolekit is not configured yet.
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-search-tool:
 tracker-search-tool depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing tracker-search-tool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
 network-manager depends on hal (>= 0.5.7.1); however:
  Package hal is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on dbus; however:
  Package dbus is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on dbus; however:
  Package dbus is not configured yet.
 f-spot depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing bluez-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-spell:
 gnome-spell depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-spell depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-spell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-applets depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 policykit-gnome depends on policykit; however:
  Package policykit is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker:
 tracker depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-bin:
 libgnomevfs2-bin depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-1-0:
 libgdl-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomecupsui1.0-1c2a:
 libgnomecupsui1.0-1c2a depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnomecupsui1.0-1c2a depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomecupsui1.0-1c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 compiz-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
Setting up powernowd (0.97-2ubuntu4) ...
invoke-rc.d: initscript powernowd, action "start" failed.
dpkg: error processing powernowd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted
root@ubuntu:/#

---

### Post by quarkhirad on 2008-10-10
Ok just so that people dont get confused i can see the thread 
[http://ubuntuforums.org/showthread.php?t=355613](http://ubuntuforums.org/showthread.php?t=355613)

But the automatix site i cant

---

