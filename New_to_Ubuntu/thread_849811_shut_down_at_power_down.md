---
title: "shut down at power down"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by matchstich on 2008-07-04
i installed 8.04 on a old sag box.  when it had windows and i clicked on shut down.

it would power down and i would get a message saying it now safe

to shut off the box.  8.04 goes thru the steps and then i see the 

error message in the thumb nail.


any ideas on what, or if , i can do anything about that?

thanks

---

### Post by spiderbatdad on 2008-07-04
I don't believe those are errors per se, just a verbose shutdown with perhaps   unnecessarily alarming messages. As you can see, networking is terminated which triggers the messages that follow.

---

### Post by f37u5g0d on 2008-07-04
I get the same error when I shut down.  I have been lead to believe that they aren't important and that you don't need to fix anything.  The only difference is that mine flash and I can see them for less than 2 seconds (literally).  How long does your computer sit at that screen?

---

### Post by Dr Small on 2008-07-04
> **f37u5g0d said:**
> I get the same error when I shut down.  I have been lead to believe that they aren't important and that you don't need to fix anything.  The only difference is that mine flash and I can see them for less than 2 seconds (literally).  How long does your computer sit at that screen?
Same thing happens on my old Dapper Drake box, as far as I recall. Nothing harmful in itself, just meerly annoying.

---

### Post by unutbu on 2008-07-04
I hate it when Network Manager Terminiates.

---

### Post by dizee on 2008-07-04
I have been getting that Network manager junk since Gutsy (using Xubuntu). It's nothing to worry about although it does make shutdowns look unpolished.

---

### Post by Dr Small on 2008-07-04
> **dizee said:**
> I have been getting that Network manager junk since Gutsy (using Xubuntu). It's nothing to worry about although it does make shutdowns look unpolished.
Unpolished? Yes.
Annoying? Somewhat.
Geekier? Absolutely! :D

---

### Post by dizee on 2008-07-04
:D yeah I don't mind it myself it's just it kind of freaks people out when they see it, they assume i've just hacked into the pentagon or something.

---

### Post by unutbu on 2008-07-04
Add these two symlinks to /etc/rc0.d:
```
  lrwxrwxrwx   1 root root    13 2008-07-04 23:08 K16hal -> ../init.d/hal
  lrwxrwxrwx   1 root root    14 2008-07-04 23:18 K20dbus -> ../init.d/dbus
```
```

sudo ln -sf /etc/init.d/hal /etc/rc0.d/K16hal
sudo ln -sf /etc/init.d/dbus /etc/rc0.d/K20dbus
```

No more Terminiation. Hallelujah.

---

### Post by matchstich on 2008-07-05
> **f37u5g0d said:**
> I get the same error when I shut down.  I have been lead to believe that they aren't important and that you don't need to fix anything.  The only difference is that mine flash and I can see them for less than 2 seconds (literally).  How long does your computer sit at that screen?


till i turn the computer off with the switch.


thanks

---

### Post by sayakb on 2008-07-05
Check your BIOS settings and set the Power Off state from Standby to Suspend. Do you have an AT SMPS? If not, then the BIOS settings will do the trick..

---

### Post by matchstich on 2008-07-05
> **LinuxIsInnovation said:**
> Check your BIOS settings and set the Power Off state from Standby to Suspend. Do you have an AT SMPS? If not, then the BIOS settings will do the trick..

power off is set on suspend

thanks

---

### Post by matchstich on 2008-07-05
ok, i changed the time off from 4 minutes to 4 secs, now i am getting 

*will now halt

halt: unable to iterate ide devices: no such file or directory.

thanks

dang it , wrong thumbnail, my apologies

---

### Post by wjwh on 2008-07-28
> **dizee said:**
> I have been getting that Network manager junk since Gutsy (using Xubuntu). It's nothing to worry about although it does make shutdowns look unpolished.

I get these messages also and, as you say, it really does make the system look unpolished - especially when they can't even spell "termination" properly!  :)

---

### Post by matchstich on 2008-07-28
it is not the message that bugs me, i get that on all my boxes,(5) cept this one 

box hangs at that message and i have to power off by using the switch.

thanks

---

### Post by unutbu on 2008-07-28
I don't know if I can help you, but please post

```
cat /proc/cmdline
bzip2 -c /var/log/messages > messages.bz2
bzip2 -c /var/log/syslog > syslog.bz2
dmesg | bzip2 -c > dmesg.bz2
```

Please post messages.bz2, syslog.bz2 and dmesg.bz2 as attachments.

---

### Post by matchstich on 2008-07-28
1

---

### Post by matchstich on 2008-07-29
-desktop:~$ cat /proc/cmdline
root=UUID=18e790d0-d36d-4c47-8924-1d445ee46285 ro quiet splash

i copy and paste but this is the only thing that i got.

thanks

---

### Post by philinux on 2008-07-29
The other three commands should have created text files.

They will be in your home folder.

---

### Post by unutbu on 2008-07-29
Look inside your home account for the three files:
messages.bz2, syslog.bz2 and dmesg.bz2.
Then when you post a message here, click the "Manage  Attachments" button about half-way down the page and attach the three files to your post.

---

### Post by CEB2nd on 2008-07-29
Looks like this bug has been around for a while:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266)

On edit: I got rid of the problem, at least on my system, by
having two (no more, no less) blank lines after the [greeter] line
in the etc/gdm/gdm.conf-custom file.

The change doesn't take effect until you restart.

---

### Post by matchstich on 2008-07-30
ok, here are the other ones only found two .

thanks

---

### Post by unutbu on 2008-07-30
> 
ok, i changed the time off from 4 minutes to 4 secs, now i am getting

*will now halt

halt: unable to iterate ide devices: no such file or directory.

Can you explain this some more? How exactly did you change the 'time off' from 4min to 4sec? 

I also notice in your /var/log/messages:
```

Jul 29 11:57:04 truck-desktop kernel: [   86.741298] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Jul 29 11:57:04 truck-desktop kernel: [   86.741313] ata2: failed to recover some devices, retrying in 5 secs

```

Coupled with the error message you quoted, "halt: unable to iterate ide devices: no such file or directory." it sounds like there is something fishy going on with a drive.

Please post the output of

```
dmesg
lspci -nn
sudo lshw -C disk
```

---

### Post by matchstich on 2008-07-31
in my bios, power mangement , a line said shut down time.

i had thought it was waiting 4 minutes to shut down, so, i changed it to 4 seconds-- do not know much about bios, try to stay out of there.

-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb4f0
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: INTEL    Product ID: 440BX        APIC at: 0xFEE00000
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=UUID=18e790d0-d36d-4c47-8924-1d445ee46285 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 751.722 MHz processor.
[   78.830558] Console: colour VGA+ 80x25
[   78.830571] console [tty0] enabled
[   78.832057] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   78.833762] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   78.892849] Memory: 507780k/524288k available (2177k kernel code, 15940k reserved, 1006k data, 368k init, 0k highmem)
[   78.892873] virtual kernel memory layout:
[   78.892876]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   78.892880]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   78.892884]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   78.892888]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[   78.892891]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   78.892895]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   78.892899]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   78.892908] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   78.893002] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   78.973027] Calibrating delay using timer specific routine.. 1504.81 BogoMIPS (lpj=3009635)
[   78.973095] Security Framework initialized
[   78.973115] SELinux:  Disabled at boot.
[   78.973150] AppArmor: AppArmor initialized
[   78.973161] Failure registering capabilities with primary security module.
[   78.973184] Mount-cache hash table entries: 512
[   78.973485] Initializing cgroup subsys ns
[   78.973495] Initializing cgroup subsys cpuacct
[   78.973516] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   78.973545] CPU: L1 I cache: 16K, L1 D cache: 16K
[   78.973552] CPU: L2 cache: 256K
[   78.973561] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   78.973588] Compat vDSO mapped to ffffe000.
[   78.973623] Checking 'hlt' instruction... OK.
[   78.989696] SMP alternatives: switching to UP code
[   78.993258] Freeing SMP alternatives: 11k freed
[   78.993602] Early unpacking initramfs... done
[   79.937710] CPU0: Intel Pentium III (Coppermine) stepping 01
[   79.937784] Total of 1 processors activated (1504.81 BogoMIPS).
[   79.938153] ExtINT not setup in hardware but reported by MP table
[   79.938798] ENABLING IO-APIC IRQs
[   79.939190] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   80.193056] Brought up 1 CPUs
[   80.193166] CPU0 attaching sched-domain:
[   80.193175]  domain 0: span 01
[   80.193180]   groups: 01
[   80.193745] net_namespace: 64 bytes
[   80.193768] Booting paravirtualized kernel on bare hardware
[   80.195307] Time: 12:32:21  Date: 07/31/08
[   80.195402] NET: Registered protocol family 16
[   80.196042] EISA bus registered
[   80.227424] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=1
[   80.227433] PCI: Using configuration type 1
[   80.227462] Setting up standard PCI resources
[   80.231280] ACPI: Interpreter disabled.
[   80.231294] Linux Plug and Play Support v0.97 (c) Adam Belay
[   80.231388] pnp: PnP ACPI: disabled
[   80.231398] PnPBIOS: Scanning system for PnP BIOS support...
[   80.231701] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7280
[   80.231715] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6bd4, dseg 0xf0000
[   80.237165] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   80.237871] PCI: Probing PCI hardware
[   80.237881] PCI: Probing PCI hardware (bus 00)
[   80.238250] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   80.238255] * this clock source is slow. Consider trying other clock sources
[   80.238307] PCI quirk: region 0400-043f claimed by PIIX4 ACPI
[   80.238315] PCI quirk: region 0440-044f claimed by PIIX4 SMB
[   80.238324] PIIX4 devres B PIO at 0290-0297
[   80.285008] NET: Registered protocol family 8
[   80.285020] NET: Registered protocol family 20
[   80.285245] AppArmor: AppArmor Filesystem Enabled
[   80.285368] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   80.285377] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   80.285386] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   80.285395] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   80.285403] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   80.285412] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   80.285421] system 00:00: iomem range 0xfffc0000-0xffffffff could not be reserved
[   80.285452] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   80.285461] system 00:08: ioport range 0xcf8-0xcff could not be reserved
[   80.285469] system 00:08: ioport range 0x400-0x43f has been reserved
[   80.285477] system 00:08: ioport range 0x440-0x44f has been reserved
[   80.285487] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285495] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285502] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285509] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285517] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285524] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285532] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285539] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.285557] system 00:09: ioport range 0x290-0x297 has been reserved
[   80.285565] system 00:09: ioport range 0x398-0x399 has been reserved
[   80.286811] PCI: Bridge: 0000:00:01.0
[   80.286820]   IO window: d000-dfff
[   80.286830]   MEM window: ff500000-ff5fffff
[   80.286837]   PREFETCH window: eea00000-f6afffff
[   80.286884] NET: Registered protocol family 2
[   80.288898] Time: tsc clocksource has been installed.
[   80.321164] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   80.321994] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[   80.325181] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   80.328671] TCP: Hash tables configured (established 65536 bind 65536)
[   80.328683] TCP reno registered
[   80.337387] checking if image is initramfs... it is
[   82.122065] Freeing initrd memory: 7301k freed
[   82.123932] audit: initializing netlink socket (disabled)
[   82.123974] audit(1217507543.124:1): initialized
[   82.130390] VFS: Disk quotas dquot_6.5.1
[   82.130654] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   82.131313] io scheduler noop registered
[   82.131322] io scheduler anticipatory registered
[   82.131328] io scheduler deadline registered
[   82.131372] io scheduler cfq registered (default)
[   82.131460] PCI: Firmware left 0000:00:14.0 e100 interrupts enabled, disabling
[   82.131475] Boot video device is 0000:01:00.0
[   82.132183] isapnp: Scanning for PnP cards...
[   82.486299] isapnp: No Plug & Play device found
[   82.587522] Real Time Clock Driver v1.12ac
[   82.587736] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   82.587974] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   82.588334] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   82.590257] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   82.590954] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   82.593315] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   82.593534] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   82.593855] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   82.596740] serio: i8042 KBD port at 0x60,0x64 irq 1
[   82.596754] serio: i8042 AUX port at 0x60,0x64 irq 12
[   82.608836] mice: PS/2 mouse device common for all mice
[   82.609205] EISA: Probing bus 0 at eisa.0
[   82.609262] EISA: Detected 0 cards.
[   82.609271] cpuidle: using governor ladder
[   82.609276] cpuidle: using governor menu
[   82.609709] NET: Registered protocol family 1
[   82.609797] Using IPI No-Shortcut mode
[   82.609881] registered taskstats version 1
[   82.610128]   Magic number: 0:87:533
[   82.610346] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   82.610352] EDD information not available.
[   82.611846] Freeing unused kernel memory: 368k freed
[   82.652655] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   84.276102] fuse init (API version 7.9)
[   84.375484] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   85.342049] SCSI subsystem initialized
[   85.440426] usbcore: registered new interface driver usbfs
[   85.440494] usbcore: registered new interface driver hub
[   85.465246] usbcore: registered new device driver usb
[   85.700355] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   85.700368] e100: Copyright(c) 1999-2006 Intel Corporation
[   85.729490] e100: eth0: e100_probe: addr 0xffaec000, irq 9, MAC addr 00:d0:b7:21:e9:47
[   85.742387] libata version 3.00 loaded.
[   85.764333] USB Universal Host Controller Interface driver v3.0
[   85.764523] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   85.764540] PCI: No IRQ known for interrupt pin D of device 0000:00:07.2. Probably buggy MP table.
[   85.764550] uhci_hcd 0000:00:07.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:07.2 setup!
[   85.764563] uhci_hcd 0000:00:07.2: init 0000:00:07.2 fail, -19
[   85.785436] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   85.785594] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   85.786179] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   85.786229] ohci_hcd 0000:00:12.0: irq 5, io mem 0xffaed000
[   85.871473] usb usb1: configuration #1 chosen from 1 choice
[   85.871547] hub 1-0:1.0: USB hub found
[   85.871568] hub 1-0:1.0: 3 ports detected
[   85.983452] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   85.983570] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 2
[   85.983686] ehci_hcd 0000:00:12.2: irq 10, io mem 0xffaeff00
[   85.993331] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   85.993672] usb usb2: configuration #1 chosen from 1 choice
[   85.993751] hub 2-0:1.0: USB hub found
[   85.993771] hub 2-0:1.0: 5 ports detected
[   86.094393] Floppy drive(s): fd0 is 1.44M
[   86.110809] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   86.110914] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[   86.110960] ohci_hcd 0000:00:12.1: irq 9, io mem 0xffaee000
[   86.115013] FDC 0 is a post-1991 82077
[   86.195396] usb usb3: configuration #1 chosen from 1 choice
[   86.195473] hub 3-0:1.0: USB hub found
[   86.195494] hub 3-0:1.0: 2 ports detected
[   86.296735] ata_piix 0000:00:07.1: version 2.12
[   86.302094] scsi0 : ata_piix
[   86.304515] scsi1 : ata_piix
[   86.304658] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   86.304667] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   86.469429] ata1.00: ATA-5: WDC WD200AB-00CDB0, 05.04E05, max UDMA/100
[   86.469443] ata1.00: 39102336 sectors, multi 16: LBA 
[   86.485385] ata1.00: configured for UDMA/33
[   86.812240] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   86.812257] ata2: failed to recover some devices, retrying in 5 secs
[   92.127748] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   92.127762] ata2: failed to recover some devices, retrying in 5 secs
[   97.458766] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   97.458780] ata2: failed to recover some devices, retrying in 5 secs
[  102.782452] ata2.00: ATAPI: RICOH CD-R/RW MP7040A, 1.60, max MWDMA2
[  102.954371] ata2.00: configured for MWDMA2
[  102.954713] scsi 0:0:0:0: Direct-Access     ATA      WDC WD200AB-00CD 05.0 PQ: 0 ANSI: 5
[  102.958863] scsi 1:0:0:0: CD-ROM            RICOH    CD-R/RW MP7040A  1.60 PQ: 0 ANSI: 5
[  102.996275] Driver 'sd' needs updating - please use bus_type methods
[  103.000779] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[  103.000826] sd 0:0:0:0: [sda] Write Protect is off
[  103.000835] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.000893] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.001041] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[  103.001075] sd 0:0:0:0: [sda] Write Protect is off
[  103.001082] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.001136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.001150]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  103.022978]  sda1 sda2 < sda5 >
[  103.046243] sd 0:0:0:0: [sda] Attached SCSI disk
[  103.065962] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  103.066068] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  103.071225] sr0: scsi3-mmc drive: 20x/20x writer cd/rw xa/form2 cdda tray
[  103.071241] Uniform CD-ROM driver Revision: 3.20
[  103.071416] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  103.528650] Attempting manual resume
[  103.528661] swsusp: Resume From Partition 8:5
[  103.528667] PM: Checking swsusp image.
[  103.529057] PM: Resume from disk failed.
[  103.614431] kjournald starting.  Commit interval 5 seconds
[  103.614471] EXT3-fs: mounted filesystem with ordered data mode.
[  117.007544] ip_tables: (C) 2000-2006 Netfilter Core Team
[  117.227966] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[  120.136070] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  120.233332] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  120.332308] Linux agpgart interface v0.102
[  120.492755] agpgart: Detected an Intel 440GX Chipset.
[  120.497447] agpgart: AGP aperture is 64M @ 0xf8000000
[  120.809485] gameport: EMU10K1 is pci0000:00:10.1/gameport0, io 0xeff0, speed 1242kHz
[  121.043926] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  121.428097] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  124.470199] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[  125.010882] parport_pc 00:0d: reported by Plug and Play BIOS
[  125.010999] parport0: PC-style at 0x378, irq 7 [PCSPP]
[  129.907983] lp0: using parport0 (interrupt-driven).
[  130.039653] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[  130.633964] EXT3 FS on sda1, internal journal
[  134.064820] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  134.065030] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  134.065743] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  134.066091] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  135.621539] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  136.703996] ppdev: user-space parallel port driver
[  137.002082] audit(1217507598.372:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5049 profile="/usr/sbin/cupsd" namespace="default"
[  139.143051] Bluetooth: Core ver 2.11
[  139.144526] NET: Registered protocol family 31
[  139.144540] Bluetooth: HCI device and connection manager initialized
[  139.144551] Bluetooth: HCI socket layer initialized
[  139.353473] Bluetooth: L2CAP ver 2.9
[  139.353487] Bluetooth: L2CAP socket layer initialized
[  139.421804] Bluetooth: RFCOMM socket layer initialized
[  139.422366] Bluetooth: RFCOMM TTY layer initialized
[  139.422378] Bluetooth: RFCOMM ver 1.8
[  142.396963] [drm] Initialized drm 1.1.0 20060810
[  142.416270] [drm] Initialized r128 2.5.0 20030725 on minor 0
[  142.418211] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[  142.418250] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  142.418301] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  229.372533] NET: Registered protocol family 10
[  229.374043] lo: Disabled Privacy Extensions
[  229.376039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  240.625296] APIC error on CPU0: 00(02)
[  256.814674] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  256.817343] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  259.130397] NET: Registered protocol family 17
[  278.059765] eth0: no IPv6 routers present
-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440GX - 82443GX Host bridge [8086:71a0]
00:01.0 PCI bridge [0604]: Intel Corporation 440GX - 82443GX AGP bridge [8086:71a1]
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
00:0f.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:10.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 04)
00:10.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 01)
00:12.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:12.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:12.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:14.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 08)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 RF/SG AGP [1002:5246]
-desktop:~$ sudo lshw -C disk
[sudo] password : 
  *-disk                  
       description: ATA Disk
       product: WDC WD200AB-00CD
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMAAR1128691
       size: 18GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=14422eea
  *-cdrom
       description: CD-R/CD-RW writer
       product: CD-R/RW MP7040A
       vendor: RICOH
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.60
       serial: [RICOH   CD-R/RW MP7040A 1.600
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open

---

### Post by unutbu on 2008-07-31
Notice this in your dmesg output:

```
[ 0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[ 0.000000] ACPI: Disabling ACPI support
```

ACPI is involved in the shutdown process. My current feeling is that this, rather than the previous post about IDE detection is the source of the problem. (Actually, ACPI is also involved in hardware detection, so maybe it is tangentially related).

Anyway, according to this thread: [http://ubuntuforums.org/showthread.php?t=416645](http://ubuntuforums.org/showthread.php?t=416645), booting with the kernel option "acpi=force" may solve the shutdown problem.

To try it for just one boot:

Power up, press ESC to get to the GRUB menu, press 'e' to edit, press the down arrow to select the 'kernel' line, press 'e' to edit, press 'End' to get to the end of the line, (you should see something like "ro quiet splash"). Add "acpi=force" to the end of the line. Press Enter to end the line, Press 'b' to boot. 

Hopefully your system will be well behaved. Put it through its paces -- play a music file, play a video, view an image, surf the web, check all the hardware is detected and working.
Then try shutting down. 

Hopefully this will work. If it doesn't, I think there is a way to shutdown using apm, but I don't recall the steps off hand. If we get to this stage, post back and I'll do a little research. Anyway, whatever the case, the instructions I gave above will only last for that one boot -- the next time you boot, you'll be back to where you are currently as far as shutdown and hardware detection is concerned.

If by happy luck the "acpi=force" option works for you, then to make it permanent:
```
gksu gedit /boot/grub/menu.lst
```

Go about 2/3 of the way down the file and you'll find your boot stanzas (something like this):
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Edit the kernel line by appending "acpi=force" to the end. Save the file, and the kernel boot option will then be permanent.

---

### Post by matchstich on 2008-07-31
ok, i did what you had showed there, 

no joy.  still stops at that error screen.

thanks

---

### Post by adobrakic on 2008-07-31
> **unutbu said:**
> Add these two symlinks to /etc/rc0.d:


I don't even have "/etc/rc0.d" :x

---

### Post by unutbu on 2008-07-31
adobrakic, what distro/version do you use? /etc/rc0.d is mentioned in the debian-policy manual ([http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)), so I am under the impression that all Ubuntu installations have an /etc/rc0.d. 

Some possibilities:
(1) I don't know what I'm talking about, your installation is fine, but things are just handled a different way.
(2) Your installation is (slightly?) messed up.
If your machine is working overall, but you'd like to get rid of the Network Manager's Terminiation message(s), you could try the following:

```
sudo mkdir -p /etc/rc0.d
sudo ln -sf /etc/init.d/hal /etc/rc0.d/K16hal
sudo ln -sf /etc/init.d/dbus /etc/rc0.d/K20dbus
```

By the way, the commands above do not really fix anything substantial. It just kills Network Manager before it can display its spelling error on the final shutdown screen. If you look in your /var/log/syslog, all the same messages will still be there.

------------------------------------------------
matchstich, try 
[list]
[*] 
```
gksu gedit /etc/modules
```
Add 'apm' to the bottom of the file. Save.

[*]Create the file /etc/modprobe.d/power:
```
gksu gedit /etc/modprobe.d/power
```
Add the line
```
options apm power_off=1 realmode_power_off=1
```
Save and quit.

[*]Now try booting again, but this time with kernel option "apm=on".
[/list]

I'm getting my information from here: [http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)

That page suggests the kernel options "noacpi acpi=off apm=on nolapic".
It's best to avoid using acpi=off if you possibly can, however, because this can also cause other problems, such as with hardware detection. Therefore, I suggest trying the smallest change necessary (I'm guessing that is apm=on), and if that doesn't work, then start adding the other options one-by-one.

If it doesn't work, record what kernel options you've tried, and post the output 
of dmesg [with code tags]("http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") again after booting with some selection of those kernel options. Hopefully, if it comes to this, there will be an interesting error message in there that we can google.

---

### Post by matchstich on 2008-08-02
am curious about something.  this box did this when it had win 2000 pro.

it is now safe to turn off your machine.

then i got a copy of xp home.  wiped the drive and installed it. 

same message when i clicked on shut down.

xp would always shut down the other 4  boxes i had it on  cept for this one.

they all have ubuntu now ( used the same install disc on them all) and 

shut down with no problem cept for this one . 


my partner has a box like this and it had 2000 pro and got the 

same message. wiped his drive. he got the xp disc and i installed 

it for him . his will shut down.


thanks

ps:  am wanting  to give this away but would like  the shut down feature 

working before i do.

---

### Post by matchstich on 2008-08-02
------------------------------------------------
matchstich, try 
[list]
[*] 
```
gksu gedit /etc/modules
```
Add 'apm' to the bottom of the file. Save.


ok, i did this

[*]Create the file /etc/modprobe.d/power:
```
gksu gedit /etc/modprobe.d/power
```
Add the line




```
options apm power_off=1 realmode_power_off=1
```
Save and quit.

this file was blank,  that line i added is the only one in there.


[*]Now try booting again, but this time with kernel option "apm=on".
[/list]

do not understand this part.

I'm getting my information from here: [http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)

That page suggests the kernel options "noacpi acpi=off apm=on nolapic".
It's best to avoid using acpi=off if you possibly can, however, because this can also cause other problems, such as with hardware detection. Therefore, I suggest trying the smallest change necessary (I'm guessing that is apm=on), and if that doesn't work, then start adding the other options one-by-one.

If it doesn't work, record what kernel options you've tried, and post the output 
of dmesg [with code tags]("http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") again after booting with some selection of those kernel options. Hopefully, if it comes to this, there will be an interesting error message in there that we can google.[/QUOTE]

---

### Post by matchstich on 2008-08-02
ok, i did as i showed in the above post.  rebooted then shut down.

it went to where it shows ubuntu and the slide bar, the cylon looking thingy

that went all the way to the right as always, but, then i heard a click

and it froze there.  ctrl-alt-delete would not work, so i switched it off 

and back on..

dmesg gave this:  cept code tags--do not understand.

-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb4f0
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: INTEL    Product ID: 440BX        APIC at: 0xFEE00000
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=UUID=18e790d0-d36d-4c47-8924-1d445ee46285 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 751.707 MHz processor.
[   79.333498] Console: colour VGA+ 80x25
[   79.333511] console [tty0] enabled
[   79.335000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   79.336692] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   79.395779] Memory: 507780k/524288k available (2177k kernel code, 15940k reserved, 1006k data, 368k init, 0k highmem)
[   79.395803] virtual kernel memory layout:
[   79.395806]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   79.395810]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   79.395814]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   79.395817]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[   79.395821]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   79.395825]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   79.395828]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   79.395837] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   79.395931] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   79.475956] Calibrating delay using timer specific routine.. 1504.82 BogoMIPS (lpj=3009645)
[   79.476024] Security Framework initialized
[   79.476044] SELinux:  Disabled at boot.
[   79.476080] AppArmor: AppArmor initialized
[   79.476091] Failure registering capabilities with primary security module.
[   79.476113] Mount-cache hash table entries: 512
[   79.476415] Initializing cgroup subsys ns
[   79.476426] Initializing cgroup subsys cpuacct
[   79.476447] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   79.476475] CPU: L1 I cache: 16K, L1 D cache: 16K
[   79.476482] CPU: L2 cache: 256K
[   79.476491] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   79.476518] Compat vDSO mapped to ffffe000.
[   79.476554] Checking 'hlt' instruction... OK.
[   79.492626] SMP alternatives: switching to UP code
[   79.496189] Freeing SMP alternatives: 11k freed
[   79.496535] Early unpacking initramfs... done
[   80.440644] CPU0: Intel Pentium III (Coppermine) stepping 01
[   80.440718] Total of 1 processors activated (1504.82 BogoMIPS).
[   80.441086] ExtINT not setup in hardware but reported by MP table
[   80.441731] ENABLING IO-APIC IRQs
[   80.442120] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   80.695986] Brought up 1 CPUs
[   80.696097] CPU0 attaching sched-domain:
[   80.696105]  domain 0: span 01
[   80.696110]   groups: 01
[   80.696679] net_namespace: 64 bytes
[   80.696702] Booting paravirtualized kernel on bare hardware
[   80.698238] Time:  6:51:17  Date: 08/02/08
[   80.698333] NET: Registered protocol family 16
[   80.698979] EISA bus registered
[   80.730362] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=1
[   80.730370] PCI: Using configuration type 1
[   80.730399] Setting up standard PCI resources
[   80.734216] ACPI: Interpreter disabled.
[   80.734231] Linux Plug and Play Support v0.97 (c) Adam Belay
[   80.734329] pnp: PnP ACPI: disabled
[   80.734340] PnPBIOS: Scanning system for PnP BIOS support...
[   80.734642] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7280
[   80.734657] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6bd4, dseg 0xf0000
[   80.740104] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   80.740810] PCI: Probing PCI hardware
[   80.740821] PCI: Probing PCI hardware (bus 00)
[   80.741187] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   80.741192] * this clock source is slow. Consider trying other clock sources
[   80.741245] PCI quirk: region 0400-043f claimed by PIIX4 ACPI
[   80.741253] PCI quirk: region 0440-044f claimed by PIIX4 SMB
[   80.741262] PIIX4 devres B PIO at 0290-0297
[   80.787938] NET: Registered protocol family 8
[   80.787950] NET: Registered protocol family 20
[   80.788176] AppArmor: AppArmor Filesystem Enabled
[   80.788300] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   80.788309] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   80.788318] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   80.788326] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   80.788335] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   80.788344] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   80.788353] system 00:00: iomem range 0xfffc0000-0xffffffff could not be reserved
[   80.788384] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   80.788393] system 00:08: ioport range 0xcf8-0xcff could not be reserved
[   80.788402] system 00:08: ioport range 0x400-0x43f has been reserved
[   80.788409] system 00:08: ioport range 0x440-0x44f has been reserved
[   80.788419] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788427] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788434] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788442] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788449] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788457] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788464] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788471] system 00:08: iomem range 0x0-0x0 could not be reserved
[   80.788488] system 00:09: ioport range 0x290-0x297 has been reserved
[   80.788496] system 00:09: ioport range 0x398-0x399 has been reserved
[   80.789745] PCI: Bridge: 0000:00:01.0
[   80.789753]   IO window: d000-dfff
[   80.789763]   MEM window: ff500000-ff5fffff
[   80.789770]   PREFETCH window: eea00000-f6afffff
[   80.789817] NET: Registered protocol family 2
[   80.791828] Time: tsc clocksource has been installed.
[   80.824091] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   80.824918] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[   80.828114] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   80.831601] TCP: Hash tables configured (established 65536 bind 65536)
[   80.831612] TCP reno registered
[   80.840320] checking if image is initramfs... it is
[   82.625024] Freeing initrd memory: 7301k freed
[   82.626893] audit: initializing netlink socket (disabled)
[   82.626936] audit(1217659879.124:1): initialized
[   82.633365] VFS: Disk quotas dquot_6.5.1
[   82.633628] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   82.634289] io scheduler noop registered
[   82.634299] io scheduler anticipatory registered
[   82.634305] io scheduler deadline registered
[   82.634348] io scheduler cfq registered (default)
[   82.634435] PCI: Firmware left 0000:00:14.0 e100 interrupts enabled, disabling
[   82.634449] Boot video device is 0000:01:00.0
[   82.635156] isapnp: Scanning for PnP cards...
[   82.989371] isapnp: No Plug & Play device found
[   83.091108] Real Time Clock Driver v1.12ac
[   83.091315] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   83.091563] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   83.091936] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   83.093537] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   83.094224] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   83.096803] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   83.097018] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   83.097335] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   83.100291] serio: i8042 KBD port at 0x60,0x64 irq 1
[   83.100306] serio: i8042 AUX port at 0x60,0x64 irq 12
[   83.115736] mice: PS/2 mouse device common for all mice
[   83.116099] EISA: Probing bus 0 at eisa.0
[   83.116157] EISA: Detected 0 cards.
[   83.116166] cpuidle: using governor ladder
[   83.116171] cpuidle: using governor menu
[   83.116611] NET: Registered protocol family 1
[   83.116702] Using IPI No-Shortcut mode
[   83.116785] registered taskstats version 1
[   83.117032]   Magic number: 4:135:872
[   83.117189]   hash matches device ptytd
[   83.117256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   83.117262] EDD information not available.
[   83.118802] Freeing unused kernel memory: 368k freed
[   83.159591] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   84.786728] fuse init (API version 7.9)
[   84.886392] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   85.873713] usbcore: registered new interface driver usbfs
[   85.873783] usbcore: registered new interface driver hub
[   85.912755] SCSI subsystem initialized
[   85.968072] usbcore: registered new device driver usb
[   86.231248] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   86.231261] e100: Copyright(c) 1999-2006 Intel Corporation
[   86.260401] e100: eth0: e100_probe: addr 0xffaec000, irq 9, MAC addr 00:d0:b7:21:e9:47
[   86.279194] libata version 3.00 loaded.
[   86.294629] USB Universal Host Controller Interface driver v3.0
[   86.294809] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   86.294828] PCI: No IRQ known for interrupt pin D of device 0000:00:07.2. Probably buggy MP table.
[   86.294838] uhci_hcd 0000:00:07.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:07.2 setup!
[   86.294850] uhci_hcd 0000:00:07.2: init 0000:00:07.2 fail, -19
[   86.323305] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   86.323461] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   86.324024] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   86.324073] ohci_hcd 0000:00:12.0: irq 5, io mem 0xffaed000
[   86.409298] usb usb1: configuration #1 chosen from 1 choice
[   86.409371] hub 1-0:1.0: USB hub found
[   86.409393] hub 1-0:1.0: 3 ports detected
[   86.522158] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   86.522272] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 2
[   86.522392] ehci_hcd 0000:00:12.2: irq 10, io mem 0xffaeff00
[   86.532231] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   86.532549] usb usb2: configuration #1 chosen from 1 choice
[   86.532628] hub 2-0:1.0: USB hub found
[   86.532648] hub 2-0:1.0: 5 ports detected
[   86.599282] Floppy drive(s): fd0 is 1.44M
[   86.622932] FDC 0 is a post-1991 82077
[   86.649515] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   86.649619] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[   86.649665] ohci_hcd 0000:00:12.1: irq 9, io mem 0xffaee000
[   86.735510] usb usb3: configuration #1 chosen from 1 choice
[   86.735585] hub 3-0:1.0: USB hub found
[   86.735606] hub 3-0:1.0: 2 ports detected
[   86.839631] ata_piix 0000:00:07.1: version 2.12
[   86.843731] scsi0 : ata_piix
[   86.846085] scsi1 : ata_piix
[   86.846227] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   86.846236] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   87.008375] ata1.00: ATA-5: WDC WD200AB-00CDB0, 05.04E05, max UDMA/100
[   87.008389] ata1.00: 39102336 sectors, multi 16: LBA 
[   87.024360] ata1.00: configured for UDMA/33
[   87.351102] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   87.351119] ata2: failed to recover some devices, retrying in 5 secs
[   92.682370] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   92.682386] ata2: failed to recover some devices, retrying in 5 secs
[   98.013695] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   98.013709] ata2: failed to recover some devices, retrying in 5 secs
[  103.337345] ata2.00: ATAPI: RICOH CD-R/RW MP7040A, 1.60, max MWDMA2
[  103.509410] ata2.00: configured for MWDMA2
[  103.509745] scsi 0:0:0:0: Direct-Access     ATA      WDC WD200AB-00CD 05.0 PQ: 0 ANSI: 5
[  103.513837] scsi 1:0:0:0: CD-ROM            RICOH    CD-R/RW MP7040A  1.60 PQ: 0 ANSI: 5
[  103.549063] Driver 'sd' needs updating - please use bus_type methods
[  103.553594] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[  103.553641] sd 0:0:0:0: [sda] Write Protect is off
[  103.553650] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.553708] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.553854] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[  103.553888] sd 0:0:0:0: [sda] Write Protect is off
[  103.553895] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.553950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.553962]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  103.577428]  sda1 sda2 < sda5 >
[  103.600663] sd 0:0:0:0: [sda] Attached SCSI disk
[  103.622738] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  103.622806] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  103.629295] sr0: scsi3-mmc drive: 20x/20x writer cd/rw xa/form2 cdda tray
[  103.629313] Uniform CD-ROM driver Revision: 3.20
[  103.629481] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  104.032196] Attempting manual resume
[  104.032207] swsusp: Resume From Partition 8:5
[  104.032212] PM: Checking swsusp image.
[  104.032611] PM: Resume from disk failed.
[  104.110305] kjournald starting.  Commit interval 5 seconds
[  104.110344] EXT3-fs: mounted filesystem with ordered data mode.
[  117.508706] ip_tables: (C) 2000-2006 Netfilter Core Team
[  117.729032] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[  120.650154] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  120.744418] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  120.846833] Linux agpgart interface v0.102
[  120.991985] agpgart: Detected an Intel 440GX Chipset.
[  120.996710] agpgart: AGP aperture is 64M @ 0xf8000000
[  121.278422] gameport: EMU10K1 is pci0000:00:10.1/gameport0, io 0xeff0, speed 1217kHz
[  121.574906] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  121.891278] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  125.060254] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[  125.187972] parport_pc 00:0d: reported by Plug and Play BIOS
[  125.188038] parport0: PC-style at 0x378, irq 7 [PCSPP]
[  130.406248] lp0: using parport0 (interrupt-driven).
[  130.492567] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  130.621708] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[  131.217228] EXT3 FS on sda1, internal journal
[  134.612220] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  134.612432] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  134.613187] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  134.613512] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  137.342375] ppdev: user-space parallel port driver
[  137.690818] audit(1217659934.558:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5051 profile="/usr/sbin/cupsd" namespace="default"
[  139.612584] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  139.856287] Bluetooth: Core ver 2.11
[  139.857797] NET: Registered protocol family 31
[  139.857811] Bluetooth: HCI device and connection manager initialized
[  139.857822] Bluetooth: HCI socket layer initialized
[  140.064828] Bluetooth: L2CAP ver 2.9
[  140.064843] Bluetooth: L2CAP socket layer initialized
[  140.201113] Bluetooth: RFCOMM socket layer initialized
[  140.201161] Bluetooth: RFCOMM TTY layer initialized
[  140.201167] Bluetooth: RFCOMM ver 1.8
[  143.119166] NET: Registered protocol family 17
[  143.401814] [drm] Initialized drm 1.1.0 20060810
[  143.441688] [drm] Initialized r128 2.5.0 20030725 on minor 0
[  143.443314] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[  143.443352] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  143.443404] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  148.571365] NET: Registered protocol family 10
[  148.572838] lo: Disabled Privacy Extensions
[  158.901915] eth0: no IPv6 routers present
[  215.415505] Inbound IN=eth0 OUT= MAC=00:d0:b7:21:e9:47:00:0f:35:44:68:01:08:00 SRC=24.64.99.123 DST=72.128.98.92 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=2530 PROTO=UDP SPT=29439 DPT=1026 LEN=492 
[  215.415636] Inbound IN=eth0 OUT= MAC=00:d0:b7:21:e9:47:00:0f:35:44:68:01:08:00 SRC=24.64.99.123 DST=72.128.98.92 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=2531 PROTO=UDP SPT=29439 DPT=1027 LEN=492 
[  215.415691] Inbound IN=eth0 OUT= MAC=00:d0:b7:21:e9:47:00:0f:35:44:68:01:08:00 SRC=24.64.99.123 DST=72.128.98.92 LEN=512 TOS=0x00 PREC=0x00 TTL=66 ID=2532 PROTO=UDP SPT=29439 DPT=1028 LEN=492 
[  229.273621] APIC error on CPU0: 00(02)
[  378.006560] Inbound IN=eth0 OUT= MAC=00:d0:b7:21:e9:47:00:0f:35:44:68:01:08:00 SRC=202.97.238.204 DST=72.128.98.92 LEN=561 TOS=0x00 PREC=0x00 TTL=40 ID=0 DF PROTO=UDP SPT=45248 DPT=1026 LEN=541 

wonder if i should see if i can get a updated flash for my mobo?

and then, find some one to help me flash. never did that before.


thanks

---

### Post by unutbu on 2008-08-02
matchstich,
This post [http://ubuntuforums.org/showpost.php?p=5495458&postcount=25](http://ubuntuforums.org/showpost.php?p=5495458&postcount=25)
shows how to boot with the "acpi=force" kernel option.

I was suggesting you try booting with the "apm=on" kernel option.

Try that. If it works, great. If it doesn't work, you have at least a few options:

[list]
[*] Try booting with each of the following kernel options:

apm=on noapic
apm=on noapic nolapic
apm=on noapic nolapic noacpi
apm=on noapic nolapic noacpi acpi=off

I'm sorry I don't have the hardware+kernel knowledge necessary to attack this problem more intelligently. The best I can do is suggest you try kernel options such as these, and other combinations until you find one that works. If you try this, keep a record of what options you've tried.

[*] Try installing a different Linux distro, perhaps Mandriva. I was involved in a different thread where the OP tried a number of kernel options, none of them worked and in the end, the OP just installed Mandriva and everything worked. Just doing clean installs of various Linux distros may be a more pragmatic way of solving this problem. 

[*] Try flashing the BIOS.
I am uncomfortable with suggesting this because I have no experience with doing this, and I hear if you do it wrong you can brick your computer. 

[*] There might be a forum reader who knows what to do better than me. You could try bumping this thread occasionally and wait for other suggestions.
[/list]

---

### Post by matchstich on 2008-08-02
i really do appreciate all that you have done.  and appreciate your patience with dealing with this problem.  i did do everything suggested.

as far i could understand.  not sure about booting with the kernel options.

 i understand that my lack of

knowledge is hindering me.  

just an old dog who finds it really hard to learn new tricks.


thanks

---

### Post by unutbu on 2008-08-02
I'm sorry -- this is probably a case of me not writing clearly. You know, a lot of computer-talk sounds complicated but is really just simple actions wrapped up in obscure lingo.

I'm probably using computer lingo which is hindering understanding. Feel free to fire away with questions and I'll try to express myself more clearly.

As far as booting with kernel options is concerned, here is a guide which might describe the process better than I have: [http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu) (Just remember that to get to the GRUB menu you have to wait until the initial screen disappears and you see the message "Loading GRUB..." in the upper left corner of an otherwise black screen. At that moment you have 3 seconds to press ESC.)

---

### Post by matchstich on 2008-08-03
well, what is happening that when i hear that click.  all the lights on my keyboard go out.  is that the hard drive shutting off, you think?

but, the main power light on the box does not go out.

and that is when i use the switch to turn off power to the box.

maybe we are closer than i thought to solving this.

thanks

---

### Post by unutbu on 2008-08-03
When you boot without any kernel options, do you still boot ok? Or does the click-and-hang happen every time now?

---

### Post by matchstich on 2008-08-03
not when i boot, when i shut down.

would like the machine to  turn it self off.

without having to use the main power switch.

thanks

---

### Post by unutbu on 2008-08-03
Oops, okay -- this happens when you shutdown, not when you boot.

Have you managed to boot with various kernel options?
If so, which have you tried, and what were the results for each?

---

### Post by jamesrfla on 2008-08-03
I think I am having the same problem as you are. I have made a thread of that problem. [http://ubuntuforums.org/showthread.php?t=878805](http://ubuntuforums.org/showthread.php?t=878805) Any successful solutions yet?

---

### Post by matchstich on 2008-08-05
> **unutbu said:**
> Oops, okay -- this happens when you shutdown, not when you boot.

Have you managed to boot with various kernel options?
If so, which have you tried, and what were the results for each?

do not know how to boot with various kernel options.  just turn it on 

and let it do it's thing.

---

### Post by matchstich on 2008-08-08
i looked into using boot options and tried what was mentioned.

no joy.  did some searching and got a update for my bios from the 

manufacturer.  they were kinda surprised that the machine was still in use.,


will re-flash and get back to yall  as soon as i figure out how to get that

zip file open and on a floopy or cd.

thanks

---

