---
title: "[SOLVED] SATA HDD Won't Mount"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by D3M0L1$H3® on 2008-09-07
Hello All,

PC SPECS:
HP pavilon 750n
512MB RAM
Installed HDD: 30GB 
Other: 80GB SATA

  I just recently installed 8.04 back on my PC. Full install on my first HDD (about 30 GB). I also had another NTFS HDD in the computer (about 80GB) that I was going to use for doc space. I could not get it to mount. I do not remember the error message. (maybe something about permissions?)
And so I popped the DVD back in and have been trying to reformat it to get it to work. The HDD is read on /dev/sdb1.
Then when I tried mounting it, it said "Cannot mount...""mount_point cannt use the characters G_DIR_..." something like that.
Recently I cannot reformat it at all now and it doesn't show up in the computer list. :confused:
I attached the GParted error file if it helps. But I really need the HDD back. I just need to format to NTFS, and try to put it in my external enclosure if need be. Please help.
Thanks in advance, 
D3M0L1SH3R

UPDATE:
I just went back into the install and used the GParted there. I only used the Live CD because it had NTFS support and for whatever reason the download doesn't. I deleted the 'error' partition on /dev/sdb1 and made a new one with maximum size for ext3. It went fine it says. I am attaching the details for this now.
The problem still lies, I cannot access the device in Ubuntu now. It's not in places, or when I go 'Places'-'Computer', and going to /dev/sdb1 doesn't have anything I can open, just a file.
:confused:
I am still a newbie to a lot of stuff in ubunti, but I tried just mounting /dev/sdb1 and it didn't work:
sudo su -    (in case of permissions)
mount /dev/sdb1
[output]mount:: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

i now formatted to FAT32. Still didn't show up. Gave it the flag "PRep", showed up as "80.1GB Media." When I try opening, I got whats in the  screenhot

---

### Post by D3M0L1$H3® on 2008-09-07
bump?
:(

---

### Post by Glaxed on 2008-09-07
Post the output from these commands;
```

$ dmesg | grep sbd
$ lspci
$ cat /var/log/errors.log

```

I don't use Ubuntu anymore, so I don't know the exact package you'll need, so just;
```

$ apt-cache search ntfs | grep 3g

```
and install anything you find.

You may want to give this a shot (I doubt it'll work), but don't do this in the root shell, use sudo;
```

$ sudo umount -a
$ sudo mount -a
$ df -h

```

If NOTHING works, then there *may* be something wrong with your usergroups. Sometimes, idiots (like me) forget to add themselves to the necessary groups - and then whine when things don't work. It isn't much of a problem in Ubuntu, but it's common in Arch. Try this;
```

$ su
# gpasswd -a YOUR_USERNAME hal
# gpasswd -a YOUR_USERNAME storage
# gpasswd -a YOUR_USERNAME dbus
# gpasswd -a YOUR_USERNAME disk

```

good luck.

---

### Post by Glaxed on 2008-09-07
Yeah.. Your GParted error log says that;
> 
create new ntfs filesystem  00:00    ( ERROR )
mkntfs -Q -vv /dev/sdb1
The device doesn't exist; did you specify it correctly?
[...]     	
Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.


So either your device can't be mounted/isn't detected, the device is locked, or the kernel had an oops. But it seems that when you formatted it differently, everything was fine.. So that's weird. Try the stuff in my last post before you really panic.

---

### Post by D3M0L1$H3® on 2008-09-07
> **Glaxed said:**
> Post the output from these commands;
```

$ dmesg | grep sbd
$ lspci
$ cat /var/log/errors.log

``` 
Hmm... I typed the first on in, and it gave no output, just took me to a new line $.
Wait, lemme just send the whole window.
Here's the ooutput from everything you told me to do. Get ready. I also attatched the txt file of it all in case it's easier than in browser.
```
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ dmesg | grep sbd

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ dmesg | grep sbd

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 
[Brookdale] Chipset Host Bridge (rev 04)
00:01.0 
PCI bridge: Intel Corporation 82845 845 [Brookdale] 
Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 
PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 
IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB 

Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 
USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 

82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 

Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:08.0 Ethernet controller: Intel Corporation 

82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
02:0b.0 Communication 

controller: Agere Systems LT WinModem (rev 02)

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ cat /var/log/errors.log
cat: /var/log/errors.log: No such file or directory

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ apt-cache search ntfs | grep 3g

libntfs-3g-dev - ntfs-3g filesystem in userspace (FUSE) library 

headers
libntfs-3g23 - ntfs-3g filesystem in userspace (FUSE) library
ntfs-3g - read-write NTFS driver for FUSE

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ sudo umount -a
[sudo] password for d3m0l1sh3r: 
umount: /dev/shm: device is busy
umount: /dev: device 

is busy
umount: /var/run: device is busy
umount: /: device is busy
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ sudo mount -a
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  4.9G   29G  

15% /
varrun                252M  124K  252M   1% /var/run
udev                  252M   60K  252M   1% /dev
devshm                

252M   36K  252M   1% /dev/shm

d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 



d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ su

Password: 

root@D3M0L1SH3R-ubuntu:/home/d3m0l1sh3r# gpasswd -a d3m0l1sh3r hal
unknown group: hal
gpasswd: Permission denied.

root@D3M0L1SH3R-ubuntu:/home/d3m0l1sh3r# gpasswd -a d3m0l1sh3r storage
unknown group: storage
gpasswd: Permission denied.
root@D3M0L1SH3R-ubuntu:/home/d3m0l1sh3r# gpasswd -a d3m0l1sh3r dbus
unknown group: dbus
gpasswd: Permission denied.

root@D3M0L1SH3R-ubuntu:/home/d3m0l1sh3r# gpasswd -a d3m0l1sh3r disk
Adding user d3m0l1sh3r to group disk

root@D3M0L1SH3R-ubuntu:/home/d3m0l1sh3r# 


```

---

### Post by Glaxed on 2008-09-07
The dmesg doesn't have any references to sbd.
Is your hdd plugged in (and on)? Post this;
```

$ dmesg
$ cat /etc/groups
$ sudo apt-get install libntfs-3g23 ntfs-3g

```

---

### Post by D3M0L1$H3® on 2008-09-07
it wouldn't let me scroll up to the $ line to copy after I did ```
$ dmesg
```
but here's as much as I could get;
```
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131068
[    0.000000]   HighMem    131068 ->   131068
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131068
[    0.000000] On node 0 totalpages: 131068
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125981 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ASUS P4B266 detected: force use of acpi=ht
[    0.000000] ACPI: RSDP signature @ 0xC00F8CD0 checksum 0
[    0.000000] ACPI: RSDP 000F8CD0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFFC000, 0030 (r1 ASUS   P4B266LA 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFFC100, 0074 (r1 ASUS   P4B266LA 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFFC180, 25A2 (r1   ASUS P4B266LA     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   P4B266LA 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 1FFFC080, 005A (r1 ASUS   P4B266LA 42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130045
[    0.000000] Kernel command line: root=UUID=daeb2a98-9f0b-4ff1-9a19-85934939439f ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1594.211 MHz processor.
[    9.888104] Console: colour VGA+ 80x25
[    9.888111] console [tty0] enabled
[    9.888540] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.889010] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.909618] Memory: 507268k/524272k available (2177k kernel code, 16368k reserved, 1006k data, 368k init, 0k highmem)
[    9.909633] virtual kernel memory layout:
[    9.909635]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.909637]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.909639]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    9.909640]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[    9.909642]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    9.909644]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    9.909645]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    9.909651] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.909708] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.989696] Calibrating delay using timer specific routine.. 3192.25 BogoMIPS (lpj=6384517)
[    9.989735] Security Framework initialized
[    9.989745] SELinux:  Disabled at boot.
[    9.989768] AppArmor: AppArmor initialized
[    9.989776] Failure registering capabilities with primary security module.
[    9.989790] Mount-cache hash table entries: 512
[    9.990010] Initializing cgroup subsys ns
[    9.990018] Initializing cgroup subsys cpuacct
[    9.990038] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    9.990060] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    9.990065] CPU: L2 cache: 256K
[    9.990069] CPU: Hyper-Threading is disabled
[    9.990073] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[    9.990094] Compat vDSO mapped to ffffe000.
[    9.990116] Checking 'hlt' instruction... OK.
[   10.006326] SMP alternatives: switching to UP code
[   10.009036] Freeing SMP alternatives: 11k freed
[   10.009263] Early unpacking initramfs... done
[   10.591818] CPU0: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 02
[   10.591888] Total of 1 processors activated (3192.25 BogoMIPS).
[   10.697418] Brought up 1 CPUs
[   10.697448] CPU0 attaching sched-domain:
[   10.697453]  domain 0: span 01
[   10.697456]   groups: 01
[   10.697805] net_namespace: 64 bytes
[   10.697820] Booting paravirtualized kernel on bare hardware
[   10.698798] Time: 14:58:04  Date: 09/07/08
[   10.698850] NET: Registered protocol family 16
[   10.699297] EISA bus registered
[   10.701488] PCI: PCI BIOS revision 2.10 entry at 0xf1060, last bus=2
[   10.701493] PCI: Using configuration type 1
[   10.701515] Setting up standard PCI resources
[   10.708080] ACPI: Interpreter disabled.
[   10.708087] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.708155] pnp: PnP ACPI: disabled
[   10.708163] PnPBIOS: Scanning system for PnP BIOS support...
[   10.708210] PnPBIOS: Found PnP BIOS installation structure at 0xc00fcb60
[   10.708215] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xcb90, dseg 0xf0000
[   10.709752] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[   10.710237] PCI: Probing PCI hardware
[   10.710244] PCI: Probing PCI hardware (bus 00)
[   10.710556] PCI: Enabled i801 SMBus device
[   10.710566] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   10.710571] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   10.711502] PCI: Transparent bridge - 0000:00:1e.0
[   10.712726] PCI: Using IRQ router PIIX/ICH [8086/2440] at 0000:00:1f.0
[   10.712777] PCI: setting IRQ 9 as level-triggered
[   10.712782] PCI: Found IRQ 9 for device 0000:02:0b.0
[   10.712798] PCI: Sharing IRQ 9 with 0000:00:1f.4
[   10.729522] NET: Registered protocol family 8
[   10.729528] NET: Registered protocol family 20
[   10.729691] AppArmor: AppArmor Filesystem Enabled
[   10.729795] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[   10.729801] system 00:09: iomem range 0x100000-0x1fffffff could not be reserved
[   10.729806] system 00:09: iomem range 0xe8000-0xeffff has been reserved
[   10.729811] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
[   10.729815] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
[   10.729820] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
[   10.729824] system 00:09: iomem range 0xcd000-0xcffff has been reserved
[   10.729830] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   10.729850] system 00:13: ioport range 0x290-0x297 has been reserved
[   10.729855] system 00:13: ioport range 0x3f0-0x3f1 has been reserved
[   10.729860] system 00:13: ioport range 0xe400-0xe47f has been reserved
[   10.729865] system 00:13: ioport range 0xec00-0xec3f has been reserved
[   10.733328] Time: tsc clocksource has been installed.
[   10.760721] PCI: Bridge: 0000:00:01.0
[   10.760726]   IO window: d000-dfff
[   10.760733]   MEM window: df000000-dfffffff
[   10.760739]   PREFETCH window: e0000000-f7ffffff
[   10.760747] PCI: Bridge: 0000:00:1e.0
[   10.760751]   IO window: b000-bfff
[   10.760759]   MEM window: dd800000-deffffff
[   10.760764]   PREFETCH window: disabled.
[   10.760790] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.760812] NET: Registered protocol family 2
[   10.797436] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   10.797861] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   10.797981] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   10.798114] TCP: Hash tables configured (established 16384 bind 16384)
[   10.798119] TCP reno registered
[   10.809591] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   11.349726]  it is
[   11.944599] Freeing initrd memory: 7731k freed
[   11.944923] Simple Boot Flag at 0x3a set to 0x1
[   11.945649] audit: initializing netlink socket (disabled)
[   11.945673] audit(1220799484.932:1): initialized
[   11.949560] VFS: Disk quotas dquot_6.5.1
[   11.949735] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.950127] io scheduler noop registered
[   11.950132] io scheduler anticipatory registered
[   11.950136] io scheduler deadline registered
[   11.950164] io scheduler cfq registered (default)
[   11.950225] Boot video device is 0000:01:00.0
[   11.950713] isapnp: Scanning for PnP cards...
[   12.304980] isapnp: No Plug & Play device found
[   12.397984] Real Time Clock Driver v1.12ac
[   12.398136] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.398301] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.398604] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.399823] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.400593] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.402620] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.402757] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.402996] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   12.407492] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.407500] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.408712] mice: PS/2 mouse device common for all mice
[   12.408983] EISA: Probing bus 0 at eisa.0
[   12.409026] EISA: Detected 0 cards.
[   12.409031] cpuidle: using governor ladder
[   12.409034] cpuidle: using governor menu
[   12.409199] NET: Registered protocol family 1
[   12.409250] Using IPI No-Shortcut mode
[   12.409303] registered taskstats version 1
[   12.409434]   Magic number: 8:470:990
[   12.409449]   hash matches device ttyd3
[   12.409575] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.409578] EDD information not available.
[   12.410190] Freeing unused kernel memory: 368k freed
[   12.444405] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   13.864544] fuse init (API version 7.9)
[   13.925269] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   14.553103] SCSI subsystem initialized
[   14.707742] usbcore: registered new interface driver usbfs
[   14.707786] usbcore: registered new interface driver hub
[   14.752750] libata version 3.00 loaded.
[   14.771270] usbcore: registered new device driver usb
[   14.791983] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   14.791990] e100: Copyright(c) 1999-2006 Intel Corporation
[   14.792080] PCI: Enabling device 0000:02:08.0 (0014 -> 0017)
[   14.792095] PCI: setting IRQ 11 as level-triggered
[   14.792099] PCI: Assigned IRQ 11 for device 0000:02:08.0
[   14.825556] e100: eth0: e100_probe: addr 0xde800000, irq 11, MAC addr 00:e0:18:5d:4b:e4
[   14.872002] ata_piix 0000:00:1f.1: version 2.12
[   14.872091] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.892505] scsi0 : ata_piix
[   14.911910] USB Universal Host Controller Interface driver v3.0
[   14.919102] scsi1 : ata_piix
[   14.919193] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xa800 irq 14
[   14.919198] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xa808 irq 15
[   14.937784] Floppy drive(s): fd0 is 1.44M
[   14.955180] FDC 0 is a National Semiconductor PC87306
[   15.091483] ata1.00: ATA-6: ST340810A, 3.39, max UDMA/100
[   15.091490] ata1.00: 78165360 sectors, multi 16: LBA 
[   15.091668] ata1.01: ATA-6: SAMSUNG SV8004H, QR100-07, max UDMA/100
[   15.091672] ata1.01: 156368016 sectors, multi 16: LBA 
[   15.107387] ata1.00: configured for UDMA/100
[   15.123303] ata1.01: configured for UDMA/100
[   15.622999] ata2.00: ATAPI: Hewlett-Packard CD-Writer  cd16f, 1.1D, max UDMA/33
[   15.623047] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8160B, 0011, max UDMA/33
[   15.810793] ata2.00: configured for UDMA/33
[   16.014731] ata2.01: configured for UDMA/33
[   16.014938] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        3.39 PQ: 0 ANSI: 5
[   16.015151] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SV8004H  QR10 PQ: 0 ANSI: 5
[   16.019875] scsi 1:0:0:0: CD-ROM            HP       CD-Writer cd16f  1.1D PQ: 0 ANSI: 5
[   16.024121] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8160B 0011 PQ: 0 ANSI: 5
[   16.028664] PCI: Found IRQ 9 for device 0000:00:1f.2
[   16.028708] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   16.028714] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   16.029182] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   16.029223] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000a400
[   16.029485] usb usb1: configuration #1 chosen from 1 choice
[   16.029529] hub 1-0:1.0: USB hub found
[   16.029540] hub 1-0:1.0: 2 ports detected
[   16.130523] PCI: Found IRQ 9 for device 0000:00:1f.4
[   16.130556] PCI: Sharing IRQ 9 with 0000:02:0b.0
[   16.130570] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   16.130577] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   16.130622] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   16.130654] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000a000
[   16.130854] usb usb2: configuration #1 chosen from 1 choice
[   16.130899] hub 2-0:1.0: USB hub found
[   16.130910] hub 2-0:1.0: 2 ports detected
[   16.234645] PCI: Enabling device 0000:02:09.0 (0014 -> 0016)
[   16.234665] PCI: Assigned IRQ 11 for device 0000:02:09.0
[   16.286588] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   16.371515] Driver 'sd' needs updating - please use bus_type methods
[   16.371908] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.372185] sd 0:0:0:0: [sda] Write Protect is off
[   16.372191] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.372251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.372962] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   16.372990] sd 0:0:0:0: [sda] Write Protect is off

[   16.372995] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.373033] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.373040]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.403136]  sda1 sda2 < sda5 >
[   16.438174] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.438309] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   16.438334] sd 0:0:1:0: [sdb] Write Protect is off
[   16.438339] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   16.438379] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.438468] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   16.438491] sd 0:0:1:0: [sdb] Write Protect is off
[   16.438496] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   16.438534] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.438542]  sdb: sdb1
[   16.451356] sd 0:0:1:0: [sdb] Attached SCSI disk
[   16.474228] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.474265] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   16.474298] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   16.474335] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   16.477841] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   16.477850] Uniform CD-ROM driver Revision: 3.20
[   16.477958] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.505522] sr1: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[   16.505628] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   17.387015] Attempting manual resume
[   17.387022] swsusp: Resume From Partition 8:5
[   17.387026] PM: Checking swsusp image.
[   17.387355] PM: Resume from disk failed.
[   17.459721] kjournald starting.  Commit interval 5 seconds
[   17.459744] EXT3-fs: mounted filesystem with ordered data mode.
[   17.577687] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0005160000406205]
[   31.788594] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input2
[   31.897875] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   31.973669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.053585] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.117400] iTCO_vendor_support: vendor-support=0
[   32.153397] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.155372] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   32.155387] iTCO_wdt: No card detected
[   32.205326] Linux agpgart interface v0.102
[   32.505232] agpgart: Detected an Intel 845G Chipset.
[   32.509208] agpgart: AGP aperture is 64M @ 0xf8000000
[   32.562572] parport_pc 00:01: reported by Plug and Play BIOS
[   32.562627] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   32.689049] intel_rng: FWH not detected
[   34.564068] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   35.154794] PCI: Enabling device 0000:00:1f.5 (0004 -> 0005)
[   35.154814] PCI: Assigned IRQ 11 for device 0000:00:1f.5
[   35.154830] PCI: Sharing IRQ 11 with 0000:00:1f.3
[   35.154864] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.823364] intel8x0_measure_ac97_clock: measured 54887 usecs
[   35.823371] intel8x0: clocking to 48000
[   35.946307] NET: Registered protocol family 17
[   37.825790] lp0: using parport0 (interrupt-driven).
[   37.968402] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   38.537362] EXT3 FS on sda1, internal journal
[   38.884529] device-mapper: uevent: version 1.0.3
[   38.884580] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   39.249059] NET: Registered protocol family 10
[   39.249522] lo: Disabled Privacy Extensions
[   40.903515] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.778729] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   41.778851] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   41.779240] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   41.779446] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   43.121031] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   44.492899] ppdev: user-space parallel port driver
[   44.793512] audit(1220799518.196:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4855 profile="/usr/sbin/cupsd" namespace="default"
[   48.017142] Bluetooth: Core ver 2.11
[   48.018234] NET: Registered protocol family 31
[   48.018243] Bluetooth: HCI device and connection manager initialized
[   48.018250] Bluetooth: HCI socket layer initialized
[   48.048092] Bluetooth: L2CAP ver 2.9
[   48.048100] Bluetooth: L2CAP socket layer initialized
[   48.127977] Bluetooth: RFCOMM socket layer initialized
[   48.128406] Bluetooth: RFCOMM TTY layer initialized
[   48.128416] Bluetooth: RFCOMM ver 1.8
[   49.255424] eth0: no IPv6 routers present
[   50.585955] [drm] Initialized drm 1.1.0 20060810
[   50.604339] PCI: Found IRQ 11 for device 0000:01:00.0
[   50.604950] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   52.252759] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   52.253244] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   52.253605] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   52.528033] [drm] Setting GART location based on new memory map
[   52.528050] [drm] Loading R300 Microcode
[   52.528106] [drm] writeback test succeeded in 1 usecs
[   76.812813] glxinfo[5910]: segfault at 00000200 eip b7f22bad esp bfaf68c0 error 4
[   76.863259] glxinfo[5915]: segfault at 00000200 eip b7f07bad esp bffd0da0 error 4
[   76.962419] glxinfo[5930]: segfault at 00000200 eip b7fcabad esp bffbdd90 error 4
[   77.065672] glxinfo[5955]: segfault at 00000200 eip b7f05bad esp bfb57920 error 4
[  655.346167] end_request: I/O error, dev fd0, sector 0
[  668.408235] end_request: I/O error, dev fd0, sector 0
[  681.537364] end_request: I/O error, dev fd0, sector 0
[  694.602417] end_request: I/O error, dev fd0, sector 0
[  707.672946] end_request: I/O error, dev fd0, sector 0
[  707.672961] Buffer I/O error on device fd0, logical block 0
[  720.745496] end_request: I/O error, dev fd0, sector 0
[  720.745512] Buffer I/O error on device fd0, logical block 0
[  790.716595] end_request: I/O error, dev fd0, sector 0
[  803.773140] end_request: I/O error, dev fd0, sector 0
[  816.840064] end_request: I/O error, dev fd0, sector 0
[  816.840079] Buffer I/O error on device fd0, logical block 0
[  829.897738] end_request: I/O error, dev fd0, sector 0
[  829.897752] Buffer I/O error on device fd0, logical block 0
[ 1143.410408] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1143.578442] usb 2-1: configuration #1 chosen from 1 choice
[ 1144.029606] usbcore: registered new interface driver libusual
[ 1144.102289] Initializing USB Mass Storage driver...
[ 1144.105381] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1144.108032] usbcore: registered new interface driver usb-storage
[ 1144.108045] USB Mass Storage support registered.
[ 1144.108935] usb-storage: device found at 2
[ 1144.108944] usb-storage: waiting for device to settle before scanning
[ 1149.105185] usb-storage: device scan complete
[ 1149.108189] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[ 1149.121156] sd 2:0:0:0: [sdc] 8027790 512-byte hardware sectors (4110 MB)
[ 1149.124191] sd 2:0:0:0: [sdc] Write Protect is off
[ 1149.124203] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1149.124208] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1149.137924] sd 2:0:0:0: [sdc] 8027790 512-byte hardware sectors (4110 MB)
[ 1149.143156] sd 2:0:0:0: [sdc] Write Protect is off
[ 1149.143192] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1149.143198] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1149.143209]  sdc: sdc1
[ 1149.150322] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1149.150404] sd 2:0:0:0: Attached scsi generic sg4 type 0
[ 1187.293505] end_request: I/O error, dev fd0, sector 0
[ 1200.364060] end_request: I/O error, dev fd0, sector 0
[ 1213.429203] end_request: I/O error, dev fd0, sector 0
[ 1213.429220] Buffer I/O error on device fd0, logical block 0
[ 1225.328675] usb 2-1: USB disconnect, address 2
[ 1226.501335] end_request: I/O error, dev fd0, sector 0
[ 1226.501350] Buffer I/O error on device fd0, logical block 0
[ 2160.846433] end_request: I/O error, dev fd0, sector 0
[ 2173.908163] end_request: I/O error, dev fd0, sector 0
[ 2187.037830] end_request: I/O error, dev fd0, sector 0
[ 2200.099582] end_request: I/O error, dev fd0, sector 0
[ 2213.167521] end_request: I/O error, dev fd0, sector 0
[ 2213.167538] Buffer I/O error on device fd0, logical block 0
[ 2226.228202] end_request: I/O error, dev fd0, sector 0
[ 2226.228216] Buffer I/O error on device fd0, logical block 0
[ 2356.153268] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 2356.321297] usb 2-1: configuration #1 chosen from 1 choice
[ 2356.372486] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2356.374549] usb-storage: device found at 3
[ 2356.374559] usb-storage: waiting for device to settle before scanning
[ 2361.382335] usb-storage: device scan complete
[ 2361.385405] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[ 2361.400335] sd 3:0:0:0: [sdc] 8027790 512-byte hardware sectors (4110 MB)
[ 2361.407373] sd 3:0:0:0: [sdc] Write Protect is off
[ 2361.407385] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2361.407390] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2361.419389] sd 3:0:0:0: [sdc] 8027790 512-byte hardware sectors (4110 MB)
[ 2361.422379] sd 3:0:0:0: [sdc] Write Protect is off
[ 2361.422390] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2361.422395] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2361.422405]  sdc: sdc1
[ 2361.429538] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[ 2361.429628] sd 3:0:0:0: Attached scsi generic sg4 type 0
[ 2387.416113] end_request: I/O error, dev fd0, sector 0
[ 2400.474309] end_request: I/O error, dev fd0, sector 0
[ 2413.539067] end_request: I/O error, dev fd0, sector 0
[ 2413.539083] Buffer I/O error on device fd0, logical block 0
[ 2426.601791] end_request: I/O error, dev fd0, sector 0
[ 2426.601805] Buffer I/O error on device fd0, logical block 0
[ 3466.207083] gnome-screensav[24618]: segfault at 00000200 eip b7f1dbad esp bfed3db0 error 4
[ 3547.914131] end_request: I/O error, dev fd0, sector 0
[ 3560.985447] end_request: I/O error, dev fd0, sector 0
[ 3574.142959] end_request: I/O error, dev fd0, sector 0
[ 3587.212069] end_request: I/O error, dev fd0, sector 0
[ 3600.277653] end_request: I/O error, dev fd0, sector 0
[ 3600.277668] Buffer I/O error on device fd0, logical block 0
[ 3613.339943] end_request: I/O error, dev fd0, sector 0
[ 3613.339959] Buffer I/O error on device fd0, logical block 0
[ 3901.355532] end_request: I/O error, dev fd0, sector 0
[ 3914.424522] end_request: I/O error, dev fd0, sector 0
[ 3927.492059] end_request: I/O error, dev fd0, sector 0
[ 3927.492074] Buffer I/O error on device fd0, logical block 0
[ 3940.561964] end_request: I/O error, dev fd0, sector 0
[ 3940.561979] Buffer I/O error on device fd0, logical block 0
[ 4100.017859] usb 2-1: USB disconnect, address 3
[ 4120.290453] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 4120.472506] usb 2-2: configuration #1 chosen from 1 choice
[ 4120.509694] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4120.515117] usb-storage: device found at 4
[ 4120.515126] usb-storage: waiting for device to settle before scanning
[ 4125.512618] usb-storage: device scan complete
[ 4125.515627] scsi 4:0:0:0: Direct-Access     VBTM     Store 'n' Go     1.02 PQ: 0 ANSI: 0 CCS
[ 4125.717426] sd 4:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[ 4125.720439] sd 4:0:0:0: [sdc] Write Protect is off
[ 4125.720449] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 4125.720454] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 4125.732412] sd 4:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[ 4125.735427] sd 4:0:0:0: [sdc] Write Protect is off
[ 4125.735437] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 4125.735441] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 4125.735453]  sdc: sdc1
[ 4125.741590] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 4125.741677] sd 4:0:0:0: Attached scsi generic sg4 type 0
[ 4158.017282] usb 2-2: USB disconnect, address 4
[ 4158.017819] Buffer I/O error on device sdc1, logical block 1
[ 4158.017827] lost page write due to I/O error on sdc1
[ 4158.017845] Buffer I/O error on device sdc1, logical block 8192
[ 4158.017849] lost page write due to I/O error on sdc1
[ 4755.679002] gnome-screensav[13174]: segfault at 00000200 eip b7f45bad esp bfe104e0 error 4
[ 5486.911615] gnome-screensav[25871]: segfault at 00000200 eip b7f54bad esp bfb241f0 error 4
[ 6777.429671] gnome-screensav[16010]: segfault at 00000200 eip b7f7dbad esp bf874f50 error 4
[ 7624.670259] gnome-screensav[30704]: segfault at 00000200 eip b7f63bad esp bfa24100 error 4
[10893.457110] gnome-screensav[22734]: segfault at 00000200 eip b7fa0bad esp bfb161f0 error 4
[15115.911003] gnome-screensav[31362]: segfault at 00000200 eip b7f10bad esp bf990060 error 4
[15498.295953] usb 2-1: new full speed USB device using uhci_hcd and address 5
[15498.477997] usb 2-1: configuration #1 chosen from 1 choice
[15498.530471] scsi5 : SCSI emulation for USB Mass Storage devices
[15498.532309] usb-storage: device found at 5
[15498.532317] usb-storage: waiting for device to settle before scanning
[15503.531102] usb-storage: device scan complete
[15503.534110] scsi 5:0:0:0: Direct-Access     VBTM     Store 'n' Go     1.02 PQ: 0 ANSI: 0 CCS
[15504.267796] sd 5:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[15504.270767] sd 5:0:0:0: [sdc] Write Protect is off
[15504.270778] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[15504.270783] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[15504.291811] sd 5:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[15504.294564] sd 5:0:0:0: [sdc] Write Protect is off
[15504.294577] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[15504.294582] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[15504.294592]  sdc: sdc1
[15504.301672] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[15504.301781] sd 5:0:0:0: Attached scsi generic sg4 type 0
[16151.765628] gnome-screensav[16661]: segfault at 00000200 eip b7fe6bad esp bf8ff7d0 error 4
[17438.163657] gnome-screensav[6673]: segfault at 00000200 eip b7fbabad esp bfa6c140 error 4
[19523.651145] usb 2-1: USB disconnect, address 5
[19524.634576] usb 2-1: new full speed USB device using uhci_hcd and address 6
[19524.816240] usb 2-1: configuration #1 chosen from 1 choice
[19524.868565] scsi6 : SCSI emulation for USB Mass Storage devices
[19524.870621] usb-storage: device found at 6
[19524.870631] usb-storage: waiting for device to settle before scanning
[19529.869344] usb-storage: device scan complete
[19529.872356] scsi 6:0:0:0: Direct-Access     VBTM     Store 'n' Go     1.02 PQ: 0 ANSI: 0 CCS
[19530.603758] sd 6:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[19530.606771] sd 6:0:0:0: [sdc] Write Protect is off
[19530.606781] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[19530.606786] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[19530.618746] sd 6:0:0:0: [sdc] 1005568 512-byte hardware sectors (515 MB)
[19530.621756] sd 6:0:0:0: [sdc] Write Protect is off
[19530.621765] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[19530.621770] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[19530.621782]  sdc: sdc1
[19530.627926] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[19530.628016] sd 6:0:0:0: Attached scsi generic sg4 type 0
[19592.804305] usb 2-1: USB disconnect, address 6
[19592.804847] Buffer I/O error on device sdc1, logical block 1
[19592.804855] lost page write due to I/O error on sdc1
[19592.804872] Buffer I/O error on device sdc1, logical block 8192
[19592.804876] lost page write due to I/O error on sdc1
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ cat /etc/groups
cat: /etc/groups: No such file or directory
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ sudo apt-get install libntfs-3g23 ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libntfs-3g23 is already the newest version.
ntfs-3g is already the newest version.
The following packages were automatically installed and are no longer required:
  blt cabextract tcl8.4 tk8.4 mzscheme
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
d3m0l1sh3r@D3M0L1SH3R-ubuntu:~$ 

```
:guitar:

---

### Post by Glaxed on 2008-09-07
OK.
```

$ sudo apt-get autoremove # just because you're wasting space
$ dmesg | grep err >> /home/$USER/Desktop/post_this_to_the_site.txt

```

From what I can see, it looks like dev/sdc is corrupted;
> 
[19592.804847] Buffer I/O error on device sdc1, logical block 1
[19592.804855] lost page write due to I/O error on sdc1
[19592.804872] Buffer I/O error on device sdc1, logical block 8192
[19592.804876] lost page write due to I/O error on sdc1


You may want to re-install or uninstall gnome-screensaver, or just get rid of compiz (cuz its segfaulting);
> 
 gnome-screensav[31362]: segfault at 00000200 eip b7f10bad esp bf990060 error 4


Lots of other devices under sd* look weird or corrupted. Take a look;
[ 2413.539083] Buffer I/O error on device fd0, logical block 0
et all.

Seriously, disable compiz before you fry something;
> 
[   76.812813] glxinfo[5910]: segfault at 00000200 eip b7f22bad esp bfaf68c0 error 4


---

### Post by Glaxed on 2008-09-07
* double post (oops)

---

### Post by D3M0L1$H3® on 2008-09-07
Okay Here, sorry I didn't see your edit.
ATTACHED

> **Glaxed said:**
> OK.
Seriously, disable compiz before you fry something;
Okay,  I uninstalled the stuff for it in the "Add/Remove Programs" Synaptic. and my Visual Effects are set to normal.
SDC was a flashdrive that Ubuntu was having trouble reading. I didn't realize it was still in. SDB is the HDD.
So is my HDD going to work now?
:confused:

EDIT: No, it doesn't. But I have noticed a slight (just slight) speed increase in the GUI.

EDIT2: Is there any way reinstalling Ubuntu on SDA or installing 7.10 on SDA would refresh the "mount_point" (that cannot contain the characters: newline, G_DIR_SEPARATOR (usually /)) and lemme use the HDD?
I just got started again with Ubuntu so I don't have anything but a little bi of time to lose by reinstalling.

---

### Post by D3M0L1$H3® on 2008-09-07
*Double post- now I'm doing it...

---

