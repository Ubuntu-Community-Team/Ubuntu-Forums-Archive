---
title: "filesystem always have errors"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by oliviacond on 2008-07-16
i torrent (using ktorrent) quite a lot, the problem is, this activity causes errors on the filesystem (once per month), after i reboot, i have to fsck manually.

the hard disk(PATA) is already 3 years.

is there anyway that I can reduce/avoid the errors occur on the filesystem (ext3)?
use xfs? use SATA?

---

### Post by iaculallad on 2008-07-16
> **oliviacond said:**
> i torrent (using ktorrent) quite a lot, the problem is, this activity causes errors on the filesystem (once per month), after i reboot, i have to fsck manually.

the hard disk(PATA) is already 3 years.

is there anyway that I can reduce/avoid the errors occur on the filesystem (ext3)?
use xfs? use SATA?

FSCK of a drive is just a normal phenomena in Ubuntu. The 30th (*correct me if I'm wrong with this integer count*) time you mount your filesystem,  fsck utility will automatically activate at boot-up and check your partitions/filesystem for errors, which is exactly good to keep your Ubuntu on top performance.

---

### Post by oliviacond on 2008-07-17
the problem is the automatic fsck cannot be finished 100% (error occured) and I have to manually fsck it.

---

### Post by unutbu on 2008-07-17
Do you have any suspicions about what might be causing the problem?
Could it be too much heat? 
An aging hard drive?
A wrong hard drive mode? 
overclocking?
Frequent power outages?

I'm not sure if I know enough to help you, but it may help if you post
```

uname -a
cat /proc/cmdline 
cat /etc/fstab
lspci -nnvv
sudo hdparm -cudagiI /dev/sda    # change sda to your drive's device name
sudo tune2fs -l /dev/sda3        # change sda3 to the partition that is requiring fsck
```

Also check the output of dmesg and the contents of /var/log/messages for any clues.

---

### Post by oliviacond on 2008-07-17
> **unutbu said:**
> Do you have any suspicions about what might be causing the problem?
Could it be too much heat? 
An aging hard drive?
A wrong hard drive mode? 
overclocking?
Frequent power outages?

I'm not sure if I know enough to help you, but it may help if you post
```

uname -a
cat /proc/cmdline 
cat /etc/fstab
lspci -nnvv
sudo hdparm -cudagiI /dev/sda    # change sda to your drive's device name
sudo tune2fs -l /dev/sda3        # change sda3 to the partition that is requiring fsck
```

Also check the output of dmesg and the contents of /var/log/messages for any clues.

i suspect
1. torrent
2. aging hard drive (3 years ain't that old, actually)

uname -a
```

2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```

cat /proc/cmdline 
```
root=UUID=ecd82627-e549-42c6-b385-97b070188951 ro quiet splash

```

cat /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ecd82627-e549-42c6-b385-97b070188951 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=376d8e5a-4270-4697-bd97-4eb358aeb9e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

lspci -nnvv
```
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0000000-f1ffffff
	Prefetchable memory behind bridge: d0000000-efffffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:3101]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at bc00 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:3101]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 4: I/O ports at b000 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:3101]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at b400 [size=32]

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:3101]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at b800 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device [1565:3101]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2000000-f3ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:5200]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f000 [size=16]

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: Biostar Microtech Int'l Corp P4TSV Motherboard (865G) [1565:3101]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 9
	Region 4: I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Unknown device [17af:200e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 255 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 9000 [size=256]
	Region 2: Memory at f1000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
	Subsystem: Hightech Information System Ltd. Unknown device [17af:200f]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: Memory at e0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Region 1: Memory at f1010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

02:00.0 Multimedia audio controller [0401]: Creative Labs [SB Live! Value] EMU10k1X [1102:0006]
	Subsystem: Creative Labs Unknown device [1102:1001]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at a000 [size=32]
	Capabilities: <access denied>

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Biostar Microtech Int'l Corp P4TSV Onboard LAN (RTL8100B) [1565:2300]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at a400 [size=256]
	Region 1: Memory at f3000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at f2000000 [disabled] [size=64K]
	Capabilities: <access denied>

```

sudo hdparm -cudagiI /dev/sdb
```
/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     = 256 (on)
 geometry      = 4998/255/63, sectors = 80293248, start = 0

 Model=Maxtor 6E040L0                          , FwRev=NAR61EA0, SerialNo=E1TN95CE            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       Maxtor 6E040L0                          
	Serial Number:      E1TN95CE            
	Firmware Revision:  NAR61EA0
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   80293248
	device size with M = 1024*1024:       39205 MBytes
	device size with M = 1000*1000:       41110 MBytes (41 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	Recommended acoustic management value: 192, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 1 determined by the jumper
Checksum: correct

```

sudo tune2fs -l /dev/sdb1
```
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          ecd82627-e549-42c6-b385-97b070188951
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4807488
Block count:              9612886
Reserved block count:     480644
Free blocks:              2346123
Free inodes:              4637216
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1021
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16352
Inode blocks per group:   511
Filesystem created:       Sat Apr 26 12:57:06 2008
Last mount time:          Fri Jul 18 07:18:36 2008
Last write time:          Fri Jul 18 07:18:36 2008
Mount count:              1
Maximum mount count:      28
Last checked:             Fri Jul 18 07:15:46 2008
Check interval:           15552000 (6 months)
Next check after:         Wed Jan 14 07:15:46 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       376233
Default directory hash:   tea
Directory Hash Seed:      17a37954-6f20-463b-8430-26a577d025c2
Journal backup:           inode blocks

```

dmesg
```
56301488 512-byte hardware sectors (80026 MB)
s /devices/virtual/input/input7
[   44.291731bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   26.203042] sd 0:0:0:0: [sda] Write Protect is off
] ACPI: Sleep Button (CM) [SLPB]
[   44.293541] shpchpbash: [: missing `]'
darrein@darrein-desktop:~$ [   26.203047] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
: Standard Hot Plug PCI Controller Driver version: 0.4
[ bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.203083] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  44.434729] agpgart: Detected an Intel 865 Chipset.
[   44.445768] agpgart: AGP aperture is 256M @ 0xc> [   26.203189] sd 0:0:0:0: [)da] 156301488 512-byte hardware sectors (80026 MB 
0000000
[   44.562493] iTCO_vendor_support: vendor-support=0
[   44.594213] iTCO> [   26.203213] sd 0:0:0:0: [sda] Write Protect is off
> [   26.203217] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
> [   26.203259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   44.594351] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   44.594399] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.203266]  sda: sda1
  46.488755] fglrx: module
bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.207697] sd 0:0:0:0: [sda] Attached SCSI disk
[   46.568633] [fglrx] Maximum main memory to use f
bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.207806] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   46.568683] [fglrx] ASYNCIO init succeed!
[   46.568904] [fglrx] PAT is enabash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   26.207828] sd 1:0:1:0: [sdb] Write Protect is off
bled successfully!
[   46.569557] [fglrx] module loadebash: [: missing `]'
darrein@darrein-desktop:~$ [   26.207833] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
bash: [: missing `]'
d - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   46.760442] darrein@darrein-desktop:~$ [   26.207866] sd 1:0:1:0: [sdb] Write, read cache: enabled, doesn't support DPO or FUA
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.760484] ALSA /build/buildd/> [   26.207938] sd 1:0:1:0: [sdb] 80293248 5)
linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver
> [   26.207958] sd 1:0:1:0: [sdb] Write Protect is off
[   48.481256] lp0: using parport0 (interrupt-driven)
> [   26.207962] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
> [   26.207997] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
bash: [: missing `]'
[   48.578156] Adding 1694816k swap on /dev/sdb5.  Priority:-1 extents:1 across:1694816k
[   63.965938] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0darrein@dalease use bus_type methods8003]  sdb:<4>Driver 'sr' needs updating - p 
bash: syntax error near unexpected token `4'
x0
[   63.965944] ata2.01: BMDMA stat 0x64
[   63.965951] ata2.01: cmd c8/00:f8:darrein@darrein-desktop:~$ [   26.523689] ug uhci_hcd and address 4B device usin 
17:10:64/00:00:00:00:00/f1 tag 0 dma 126976 in
[   63.965952]          res 51/bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.722759] usb 1-1: configuration #1 chosen from 1 choice
40:00:48:10:64/00:00:00:00:00/f1 Emask 0x9 (media error)
[   6bash: [: missing `]'
darrein@darrein-desktop:~$ [   26.966454] usb 1-2: new low speed USB device using uhci_hcd and address 5
bash: [: missing `]'
3.965955] ata2.01: status: { DRDY ERR }
[   63.965957] ata2.01: error: { UNC }darrein@darrein-desktop:~$ [   27.145508] 1 choice configuration #1 chosen from  
bash: [: missing `]'

[   64.143532] ata2.00: configured for UDMA/33
[   64.159649]darrein@darrein-desktop:~$ [   27.148611] usbcore: registered new er hiddev driv 
 ata2.01: configured for UDMA/33
[   64.159668] ata2: EH complebash: [: missing `]'
darrein@darrein-desktop:~$ [   27.187504] input: HID 1241:1177 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
te
[   65.010952] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   65.014880] sd 1:bash: [: missing `]'
darrein@darrein-desktop:~$ [   27.209840] input,hidraw0: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.0-1
bash: [: missing `]'
0:1:0: [sdb] Write Protect is off
[   65.014883] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 darrein@darrein-desktop:~$  as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
bash: [: missing `]'
00
[   65.017920] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  218.381064] darrein@darrein-desktop:~$ [   27.233738] input,hidraw1: USB HID [Silitek USB Multimedia Keyboard ] on usb-0000:00:1d.0-2
EXT3 FS on sdb1, internal journal
[  219.453271] ip_tables: (C) 2000-2006 Netfilter Core Team
[  220.045870] Nbash: [: missing `]'
darrein@darrein-desktop:~$ [   27.261147] input: Silitek USB Multimedia Keyboard  as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input3
bash: [: missing `]'
o dock devices found.
[  220.849455] ppdev: user-space parallel port driver
[  221.061856] audit(1216336719.237:2): type=darrein@darrein-desktop:~$ [   27.2Device [Silitek USB Multimedia Keyboard ] on usb-0000:00:1d.0-2
bash: [: missing `]'
1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6777 profile="/usr/sbin/
darrein@darrein-desktop:~$ [   27.269724] usbcore: registered new interface driver usbhid
[  221.183119] apm: BIOS version 1.2 Flags 0x07 (Driver versio
bash: [: missing `]'
darrein@darrein-desktop:~$ [   27.269731] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  221.183130] apm: disabled - APM is not SMP safe.
[  223.259863] eth0: link up, 100Mbps, full-dbash: [: missing `]'
darrein@darrein-desktop:~$ [   28.329326]  sdb1 sdb2 < sdb5 >
uplex, lpa 0x45E1
[  226.221461] ACbash: syntax error near unexpected token `newline'
darrein@darrein-desktop:~$ [   28.353727] sd 1:0:1:0: [sdb] Attached SCSI disk
bash: [: missing `]'
PI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, 
darrein@darrein-desktop:~$ [   28.361199] sd 0:0:0:0: Attached scsi generic sg0 type 0
bash: [: missing `]'
[  226.630582] NET: Registered protocol family 17
[  228.94darrein@darrein-desktop:~$ [   28.361239] sr 1:0:0:0: Attached scsi gentype 5g1  
4397] [fglrx] Internal AGP support requested, but kernel AGP
bash: [: missing `]'
darrein@darrein-desktop:~$ [   28.361272] sd 1:0:1:0: Attached scsi generic sg2 type 0
[  228.944407] [fglrx] Have to use kernel AGP support to av
bash: [: missing `]'
darrein@darrein-desktop:~$ [   28.361818] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
bash: [: missing `]'
[  228.944415] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chips
darrein@darrein-desktop:~$ [   28.361826] Uniform CD-ROM driver Revision: 3.20
bash: [: missing `]'
[  228.944581] agpgart: Found an AGP 3.0 compliant 
darrein@darrein-desktop:~$ [   28.361916] sr 1:0:0:0: Attached scsi CD-ROM sr0
bash: [: missing `]'
[  228.944602] agpgart: Putting AGP V3 device at 00
darrein@darrein-desktop:~$ [   28.615141] Attempting manual resume
[  228.944632] agpgart: Putting AGP V3 
bash: [: missing `]'
darrein@darrein-desktop:~$ [   28.615145] swsusp: Resume From Partition 8:21
[  228.944660] [fglrx] AGP enabled,  AgpCommand =
bash: [: missing `]'
darrein@darrein-desktop:~$ [   28.615147] PM: Checking swsusp image.
[  228.950589] [fglrx] GART Table is not 
bash: [: missing `]'
darrein@darrein-desktop:~$ [   28.615549] PM: Resume from disk failed.
bash: [: missing `]'
[  228.950606] [fglrx] Reserve Block - 0 of
darrein@darrein-desktop:~$ [   28.665190] kjournald starting.  Commit interval 5 seconds
bash: [: missing `]'
[  228.950610] [fglrx] Reserve Block - 1 offset =  0Xffff000 
darrein@darrein-desktop:~$ [   28.665196] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[  229.125654] [fglrx] interrupt source 20008000 successfully enabled
[  229.125666] [fglrx] enable ID = 0x00000004
[  229.1256bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   28.665206] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Marking fs in need of filesystem check.
81] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  229.125878] [fglrx] interrupt soubash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   28.669936] EXT3-fs: mounted filesystem with ordered data mode.
bash: [: missing `]'
rce 10000000 successfully enabled
[  229.125885] [fglrx] enable ID darrein@darrein-desktop:~$ [   43.629012] input/pcspkr/input/input4ices/platform 
bash: [: missing `]'
= 0x00000005
[  229.125891] [fglrx] Receive enable interrupt message with darrein@darrein-des Play ACPI  44.088124] parport_pc 00:08: reported by Plug and 
irqEnableMask: 10000000
[  231.174109] NET: Registered protocol bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.088174] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
family 10
[  231.174691] lo: Disabled Privacy Extensions
[  241.381bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.104671] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
bash: [: missing `]'
853] eth0: no IPv6 routers present
darrein@darrein-desktop:~$ [   44.163363] intel_rng: FWH not detected
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.207459] input: Power Button (FF) as /devices/virtual/input/input5
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.227132] ACPI: Power Button (FF) [PWRF]
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.227260] input: Power Button (CM) as /devices/virtual/input/input6
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.249325] Linux agpgart interface v0.102
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.259020] ACPI: Power Button (CM) [PWRB]
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.259144] input: Sleep Button (CM) as /devices/virtual/input/input7
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.291731] ACPI: Sleep Button (CM) [SLPB]
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.293541] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.434729] agpgart: Detected an Intel 865 Chipset.
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.445768] agpgart: AGP aperture is 256M @ 0xc0000000
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.562493] iTCO_vendor_support: vendor-support=0
bash: [: missing `]'
darrein@darrein-desktop:~$ [   44.594213] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.594351] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   44.594399] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   46.488755] fglrx: module
bash: [: missing `]'
darrein@darrein-desktop:~$ [   46.568633] [fglrx] Maximum main memory to use f
bash: [: missing `]'
darrein@darrein-desktop:~$ [   46.568683] [fglrx] ASYNCIO init succeed!
bash: [: missing `]'
darrein@darrein-desktop:~$ [   46.568904] [fglrx] PAT is enabled successfully!
bash: [: missing `]'
darrein@darrein-desktop:~$ [   46.569557] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
bash: [: missing `]'
darrein@darrein-desktop:~$ [   46.760442] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   46.760484] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver
bash: [: missing `]'
darrein@darrein-desktop:~$ [   48.481256] lp0: using parport0 (interrupt-driven)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   48.578156] Adding 1694816k swap on /dev/sdb5.  Priority:-1 extents:1 across:1694816k
bash: [: missing `]'
darrein@darrein-desktop:~$ [   63.965938] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
bash: [: missing `]'
darrein@darrein-desktop:~$ [   63.965944] ata2.01: BMDMA stat 0x64
bash: [: missing `]'
darrein@darrein-desktop:~$ [   63.965951] ata2.01: cmd c8/00:f8:17:10:64/00:00:00:00:00/f1 tag 0 dma 126976 in
bash: [: missing `]'
darrein@darrein-desktop:~$ [   63.965952]          res 51/40:00:48:10:64/00:00:00:00:00/f1 Emask 0x9 (media error)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   63.965955] ata2.01: status: { DRDY ERR }
bash: [: missing `]'
darrein@darrein-desktop:~$ [   63.965957] ata2.01: error: { UNC }
bash: [: missing `]'
darrein@darrein-desktop:~$ [   64.143532] ata2.00: configured for UDMA/33
bash: [: missing `]'
darrein@darrein-desktop:~$ [   64.159649] ata2.01: configured for UDMA/33
bash: [: missing `]'
darrein@darrein-desktop:~$ [   64.159668] ata2: EH complete
bash: [: missing `]'
darrein@darrein-desktop:~$ [   65.010952] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
bash: syntax error near unexpected token `('
darrein@darrein-desktop:~$ [   65.014880] sd 1:0:1:0: [sdb] Write Protect is off
bash: [: missing `]'
darrein@darrein-desktop:~$ [   65.014883] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
bash: [: missing `]'
darrein@darrein-desktop:~$ [   65.017920] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
> [  218.381064] EXT3 FS on sdb1, internal journal
> [  219.453271] ip_tables: (C) 2000-2006 Netfilter Core Team
> [  220.045870] No dock devices found.
> [  220.849455] ppdev: user-space parallel port driver
> [  221.061856] audit(1216336719.237:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6777 profile="/usr/sbin/
> [  221.183119] apm: BIOS version 1.2 Flags 0x07 (Driver versio
> [  221.183130] apm: disabled - APM is not SMP safe.
> [  223.259863] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
> [  226.221461] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, 
> [  226.630582] NET: Registered protocol family 17
> [  228.944397] [fglrx] Internal AGP support requested, but kernel AGP
> [  228.944407] [fglrx] Have to use kernel AGP support to av
> [  228.944415] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chips
> [  228.944581] agpgart: Found an AGP 3.0 compliant 
> [  228.944602] agpgart: Putting AGP V3 device at 00
> [  228.944632] agpgart: Putting AGP V3 
> [  228.944660] [fglrx] AGP enabled,  AgpCommand =
> [  228.950589] [fglrx] GART Table is not 
> [  228.950606] [fglrx] Reserve Block - 0 of
> [  228.950610] [fglrx] Reserve Block - 1 offset =  0Xffff000 
> [  229.125654] [fglrx] interrupt source 20008000 successfully enabled
> [  229.125666] [fglrx] enable ID = 0x00000004
> [  229.125681] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
> [  229.125878] [fglrx] interrupt source 10000000 successfully enabled
> [  229.125885] [fglrx] enable ID = 0x00000005
> [  229.125891] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
> [  231.174109] NET: Registered protocol family 10
> [  231.174691] lo: Disabled Privacy Extensions
> [  241.381853] eth0: no IPv6 routers present

```

var/log/messages
```
Jul 18 07:18:38 darrein-desktop kernel: [   21.901520] PnPBIOS: Disabled by ACPI PNP
Jul 18 07:18:38 darrein-desktop kernel: [   21.901877] PCI: Using ACPI for IRQ routing
Jul 18 07:18:38 darrein-desktop kernel: [   21.901882] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 18 07:18:38 darrein-desktop kernel: [   21.932770] NET: Registered protocol family 8
Jul 18 07:18:38 darrein-desktop kernel: [   21.932774] NET: Registered protocol family 20
Jul 18 07:18:38 darrein-desktop kernel: [   21.932915] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 18 07:18:38 darrein-desktop kernel: [   21.932921] hpet0: 3 64-bit timers, 14318180 Hz
Jul 18 07:18:38 darrein-desktop kernel: [   21.933971] AppArmor: AppArmor Filesystem Enabled
Jul 18 07:18:38 darrein-desktop kernel: [   21.936534] Time: tsc clocksource has been installed.
Jul 18 07:18:38 darrein-desktop kernel: [   21.960527] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960530] system 00:01: ioport range 0x290-0x29f has been reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960533] system 00:01: ioport range 0x800-0x805 has been reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960554] system 00:0c: ioport range 0x400-0x4bf could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960565] system 00:0e: iomem range 0xd0000-0xd3fff has been reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960568] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960571] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960574] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960577] system 00:0e: iomem range 0x3fff0000-0x3fffffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960580] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960583] system 00:0e: iomem range 0x100000-0x3ffeffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960586] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960589] system 00:0e: iomem range 0xfec01000-0xfed8ffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960592] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960595] system 00:0e: iomem range 0xffb00000-0xffb7ffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.960598] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
Jul 18 07:18:38 darrein-desktop kernel: [   21.991118] PCI: Bridge: 0000:00:01.0
Jul 18 07:18:38 darrein-desktop kernel: [   21.991122]   IO window: 9000-9fff
Jul 18 07:18:38 darrein-desktop kernel: [   21.991127]   MEM window: f0000000-f1ffffff
Jul 18 07:18:38 darrein-desktop kernel: [   21.991132]   PREFETCH window: d0000000-efffffff
Jul 18 07:18:38 darrein-desktop kernel: [   21.991137] PCI: Bridge: 0000:00:1e.0
Jul 18 07:18:38 darrein-desktop kernel: [   21.991140]   IO window: a000-afff
Jul 18 07:18:38 darrein-desktop kernel: [   21.991146]   MEM window: f2000000-f3ffffff
Jul 18 07:18:38 darrein-desktop kernel: [   21.991150]   PREFETCH window: disabled.
Jul 18 07:18:38 darrein-desktop kernel: [   21.991182] NET: Registered protocol family 2
Jul 18 07:18:38 darrein-desktop kernel: [   22.032363] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 18 07:18:38 darrein-desktop kernel: [   22.032753] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 18 07:18:38 darrein-desktop kernel: [   22.033642] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 18 07:18:38 darrein-desktop kernel: [   22.034183] TCP: Hash tables configured (established 131072 bind 65536)
Jul 18 07:18:38 darrein-desktop kernel: [   22.034191] TCP reno registered
Jul 18 07:18:38 darrein-desktop kernel: [   22.044448] checking if image is initramfs... it is
Jul 18 07:18:38 darrein-desktop kernel: [   22.649346] Freeing initrd memory: 7308k freed
Jul 18 07:18:38 darrein-desktop kernel: [   22.650124] audit: initializing netlink socket (disabled)
Jul 18 07:18:38 darrein-desktop kernel: [   22.650141] audit(1216365319.348:1): initialized
Jul 18 07:18:38 darrein-desktop kernel: [   22.650391] highmem bounce pool size: 64 pages
Jul 18 07:18:38 darrein-desktop kernel: [   22.653100] VFS: Disk quotas dquot_6.5.1
Jul 18 07:18:38 darrein-desktop kernel: [   22.653205] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 18 07:18:38 darrein-desktop kernel: [   22.653382] io scheduler noop registered
Jul 18 07:18:38 darrein-desktop kernel: [   22.653384] io scheduler anticipatory registered
Jul 18 07:18:38 darrein-desktop kernel: [   22.653387] io scheduler deadline registered
Jul 18 07:18:38 darrein-desktop kernel: [   22.653400] io scheduler cfq registered (default)
Jul 18 07:18:38 darrein-desktop kernel: [   22.653881] isapnp: Scanning for PnP cards...
Jul 18 07:18:38 darrein-desktop kernel: [   23.006814] isapnp: No Plug & Play device found
Jul 18 07:18:38 darrein-desktop kernel: [   23.046216] Real Time Clock Driver v1.12ac
Jul 18 07:18:38 darrein-desktop kernel: [   23.046357] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 18 07:18:38 darrein-desktop kernel: [   23.046496] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 18 07:18:38 darrein-desktop kernel: [   23.047394] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 18 07:18:38 darrein-desktop kernel: [   23.048569] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 18 07:18:38 darrein-desktop kernel: [   23.048663] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 18 07:18:38 darrein-desktop kernel: [   23.048888] PNP: No PS/2 controller found. Probing ports directly.
Jul 18 07:18:38 darrein-desktop kernel: [   23.301092] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 18 07:18:38 darrein-desktop kernel: [   23.309787] mice: PS/2 mouse device common for all mice
Jul 18 07:18:38 darrein-desktop kernel: [   23.309957] EISA: Probing bus 0 at eisa.0
Jul 18 07:18:38 darrein-desktop kernel: [   23.309998] EISA: Detected 0 cards.
Jul 18 07:18:38 darrein-desktop kernel: [   23.310002] cpuidle: using governor ladder
Jul 18 07:18:38 darrein-desktop kernel: [   23.310004] cpuidle: using governor menu
Jul 18 07:18:38 darrein-desktop kernel: [   23.310110] NET: Registered protocol family 1
Jul 18 07:18:38 darrein-desktop kernel: [   23.310145] Using IPI No-Shortcut mode
Jul 18 07:18:38 darrein-desktop kernel: [   23.310183] registered taskstats version 1
Jul 18 07:18:38 darrein-desktop kernel: [   23.310291]   Magic number: 0:817:268
Jul 18 07:18:38 darrein-desktop kernel: [   23.310325]   hash matches device ttyud
Jul 18 07:18:38 darrein-desktop kernel: [   23.310421] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 18 07:18:38 darrein-desktop kernel: [   23.310423] EDD information not available.
Jul 18 07:18:38 darrein-desktop kernel: [   23.310826] Freeing unused kernel memory: 368k freed
Jul 18 07:18:38 darrein-desktop kernel: [   24.588533] fuse init (API version 7.9)
Jul 18 07:18:38 darrein-desktop kernel: [   24.608536] ACPI: Fan [FAN] (on)
Jul 18 07:18:38 darrein-desktop kernel: [   24.617619] ACPI: Thermal Zone [THRM] (40 C)
Jul 18 07:18:38 darrein-desktop kernel: [   24.837113] usbcore: registered new interface driver usbfs
Jul 18 07:18:38 darrein-desktop kernel: [   24.837149] usbcore: registered new interface driver hub
Jul 18 07:18:38 darrein-desktop kernel: [   24.838046] usbcore: registered new device driver usb
Jul 18 07:18:38 darrein-desktop kernel: [   24.853475] USB Universal Host Controller Interface driver v3.0
Jul 18 07:18:38 darrein-desktop kernel: [   24.853582] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 18 07:18:38 darrein-desktop kernel: [   24.853608] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 18 07:18:38 darrein-desktop kernel: [   24.854055] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 18 07:18:38 darrein-desktop kernel: [   24.854094] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bc00
Jul 18 07:18:38 darrein-desktop kernel: [   24.854324] usb usb1: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   24.854364] hub 1-0:1.0: USB hub found
Jul 18 07:18:38 darrein-desktop kernel: [   24.854375] hub 1-0:1.0: 2 ports detected
Jul 18 07:18:38 darrein-desktop kernel: [   24.957281] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 18 07:18:38 darrein-desktop kernel: [   24.957310] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 18 07:18:38 darrein-desktop kernel: [   24.957354] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 18 07:18:38 darrein-desktop kernel: [   24.957389] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000b000
Jul 18 07:18:38 darrein-desktop kernel: [   24.957591] usb usb2: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   24.957632] hub 2-0:1.0: USB hub found
Jul 18 07:18:38 darrein-desktop kernel: [   24.957644] hub 2-0:1.0: 2 ports detected
Jul 18 07:18:38 darrein-desktop kernel: [   25.060999] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 18 07:18:38 darrein-desktop kernel: [   25.061022] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 18 07:18:38 darrein-desktop kernel: [   25.061064] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 18 07:18:38 darrein-desktop kernel: [   25.061100] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
Jul 18 07:18:38 darrein-desktop kernel: [   25.061292] usb usb3: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   25.061334] hub 3-0:1.0: USB hub found
Jul 18 07:18:38 darrein-desktop kernel: [   25.061345] hub 3-0:1.0: 2 ports detected
Jul 18 07:18:38 darrein-desktop kernel: [   25.164644] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
Jul 18 07:18:38 darrein-desktop kernel: [   25.164668] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 18 07:18:38 darrein-desktop kernel: [   25.164707] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jul 18 07:18:38 darrein-desktop kernel: [   25.164735] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
Jul 18 07:18:38 darrein-desktop kernel: [   25.164919] usb usb4: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   25.164959] hub 4-0:1.0: USB hub found
Jul 18 07:18:38 darrein-desktop kernel: [   25.164970] hub 4-0:1.0: 2 ports detected
Jul 18 07:18:38 darrein-desktop kernel: [   25.196422] usb 1-1: new low speed USB device using uhci_hcd and address 2
Jul 18 07:18:38 darrein-desktop kernel: [   25.268444] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 18 07:18:38 darrein-desktop kernel: [   25.268473] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 18 07:18:38 darrein-desktop kernel: [   25.268512] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jul 18 07:18:38 darrein-desktop kernel: [   25.272431] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf4000000
Jul 18 07:18:38 darrein-desktop kernel: [   25.282050] 8139too Fast Ethernet driver 0.9.28
Jul 18 07:18:38 darrein-desktop kernel: [   25.296623] SCSI subsystem initialized
Jul 18 07:18:38 darrein-desktop kernel: [   25.336064] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 18 07:18:38 darrein-desktop kernel: [   25.336259] usb usb5: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   25.336301] hub 5-0:1.0: USB hub found
Jul 18 07:18:38 darrein-desktop kernel: [   25.336311] hub 5-0:1.0: 8 ports detected
Jul 18 07:18:38 darrein-desktop kernel: [   25.378661] Floppy drive(s): fd0 is 1.44M
Jul 18 07:18:38 darrein-desktop kernel: [   25.401601] FDC 0 is a post-1991 82077
Jul 18 07:18:38 darrein-desktop kernel: [   25.440905] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 17
Jul 18 07:18:38 darrein-desktop kernel: [   25.441687] eth0: RealTek RTL8139 at 0xa400, 00:e0:4c:b5:52:4d, IRQ 17
Jul 18 07:18:38 darrein-desktop kernel: [   25.457838] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
Jul 18 07:18:38 darrein-desktop kernel: [   25.457935] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jul 18 07:18:38 darrein-desktop kernel: [   25.463753] ata_piix 0000:00:1f.2: MAP [ P1 P0 IDE IDE ]
Jul 18 07:18:38 darrein-desktop kernel: [   25.463780] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
Jul 18 07:18:38 darrein-desktop kernel: [   25.466241] scsi0 : ata_piix
Jul 18 07:18:38 darrein-desktop kernel: [   25.466414] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 18 07:18:38 darrein-desktop kernel: [   25.466457] scsi1 : ata_piix
Jul 18 07:18:38 darrein-desktop kernel: [   25.467416] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jul 18 07:18:38 darrein-desktop kernel: [   25.467421] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jul 18 07:18:38 darrein-desktop kernel: [   25.631467] ata1.00: ATA-7: WDC WD800JD-60LSA5, 10.01E03, max UDMA/100
Jul 18 07:18:38 darrein-desktop kernel: [   25.631472] ata1.00: 156301488 sectors, multi 16: LBA48 
Jul 18 07:18:38 darrein-desktop kernel: [   25.640688] ata1.00: configured for UDMA/100
Jul 18 07:18:38 darrein-desktop kernel: [   25.966595] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
Jul 18 07:18:38 darrein-desktop kernel: [   25.966791] ata2.01: ATA-7: Maxtor 6E040L0, NAR61EA0, max UDMA/133
Jul 18 07:18:38 darrein-desktop kernel: [   25.966797] ata2.01: 80293248 sectors, multi 16: LBA 
Jul 18 07:18:38 darrein-desktop kernel: [   25.966817] ata2.01: limited to UDMA/33 due to 40-wire cable
Jul 18 07:18:38 darrein-desktop kernel: [   26.137036] ata2.00: configured for UDMA/33
Jul 18 07:18:38 darrein-desktop kernel: [   26.153149] ata2.01: configured for UDMA/33
Jul 18 07:18:38 darrein-desktop kernel: [   26.153376] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-60LS 10.0 PQ: 0 ANSI: 5
Jul 18 07:18:38 darrein-desktop kernel: [   26.154510] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5
Jul 18 07:18:38 darrein-desktop kernel: [   26.154730] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
Jul 18 07:18:38 darrein-desktop kernel: [   26.202834] Driver 'sd' needs updating - please use bus_type methods
Jul 18 07:18:38 darrein-desktop kernel: [   26.203015] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 18 07:18:38 darrein-desktop kernel: [   26.203042] sd 0:0:0:0: [sda] Write Protect is off
Jul 18 07:18:38 darrein-desktop kernel: [   26.203083] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 07:18:38 darrein-desktop kernel: [   26.203189] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 18 07:18:38 darrein-desktop kernel: [   26.203213] sd 0:0:0:0: [sda] Write Protect is off
Jul 18 07:18:38 darrein-desktop kernel: [   26.203259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 07:18:38 darrein-desktop kernel: [   26.203266]  sda: sda1
Jul 18 07:18:38 darrein-desktop kernel: [   26.207697] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 18 07:18:38 darrein-desktop kernel: [   26.207806] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
Jul 18 07:18:38 darrein-desktop kernel: [   26.207828] sd 1:0:1:0: [sdb] Write Protect is off
Jul 18 07:18:38 darrein-desktop kernel: [   26.207866] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 07:18:38 darrein-desktop kernel: [   26.207938] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
Jul 18 07:18:38 darrein-desktop kernel: [   26.207958] sd 1:0:1:0: [sdb] Write Protect is off
Jul 18 07:18:38 darrein-desktop kernel: [   26.207997] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 07:18:38 darrein-desktop kernel: [   26.208003]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
Jul 18 07:18:38 darrein-desktop kernel: [   26.523689] usb 1-1: new low speed USB device using uhci_hcd and address 4
Jul 18 07:18:38 darrein-desktop kernel: [   26.722759] usb 1-1: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   26.966454] usb 1-2: new low speed USB device using uhci_hcd and address 5
Jul 18 07:18:38 darrein-desktop kernel: [   27.145508] usb 1-2: configuration #1 chosen from 1 choice
Jul 18 07:18:38 darrein-desktop kernel: [   27.148611] usbcore: registered new interface driver hiddev
Jul 18 07:18:38 darrein-desktop kernel: [   27.187504] input: HID 1241:1177 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
Jul 18 07:18:38 darrein-desktop kernel: [   27.209840] input,hidraw0: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.0-1
Jul 18 07:18:38 darrein-desktop kernel: [   27.224472] input: Silitek USB Multimedia Keyboard  as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
Jul 18 07:18:38 darrein-desktop kernel: [   27.233738] input,hidraw1: USB HID v1.10 Keyboard [Silitek USB Multimedia Keyboard ] on usb-0000:00:1d.0-2
Jul 18 07:18:38 darrein-desktop kernel: [   27.261147] input: Silitek USB Multimedia Keyboard  as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input3
Jul 18 07:18:38 darrein-desktop kernel: [   27.269693] input,hiddev96,hidraw2: USB HID v1.10 Device [Silitek USB Multimedia Keyboard ] on usb-0000:00:1d.0-2
Jul 18 07:18:38 darrein-desktop kernel: [   27.269724] usbcore: registered new interface driver usbhid
Jul 18 07:18:38 darrein-desktop kernel: [   27.269731] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jul 18 07:18:38 darrein-desktop kernel: [   28.329326]  sdb1 sdb2 < sdb5 >
Jul 18 07:18:38 darrein-desktop kernel: [   28.353727] sd 1:0:1:0: [sdb] Attached SCSI disk
Jul 18 07:18:38 darrein-desktop kernel: [   28.361199] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 18 07:18:38 darrein-desktop kernel: [   28.361239] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 18 07:18:38 darrein-desktop kernel: [   28.361272] sd 1:0:1:0: Attached scsi generic sg2 type 0
Jul 18 07:18:38 darrein-desktop kernel: [   28.361818] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 18 07:18:38 darrein-desktop kernel: [   28.361826] Uniform CD-ROM driver Revision: 3.20
Jul 18 07:18:38 darrein-desktop kernel: [   28.615141] Attempting manual resume
Jul 18 07:18:38 darrein-desktop kernel: [   28.665190] kjournald starting.  Commit interval 5 seconds
Jul 18 07:18:38 darrein-desktop kernel: [   28.665196] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
Jul 18 07:18:38 darrein-desktop kernel: [   28.665206] EXT3-fs warning (device sdb1): ext3_clear_journal_err: Marking fs in need of filesystem check.
Jul 18 07:18:38 darrein-desktop kernel: [   28.669936] EXT3-fs: mounted filesystem with ordered data mode.
Jul 18 07:18:38 darrein-desktop kernel: [   43.629012] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jul 18 07:18:38 darrein-desktop kernel: [   44.088124] parport_pc 00:08: reported by Plug and Play ACPI
Jul 18 07:18:38 darrein-desktop kernel: [   44.088174] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 18 07:18:38 darrein-desktop kernel: [   44.104671] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 18 07:18:38 darrein-desktop kernel: [   44.207459] input: Power Button (FF) as /devices/virtual/input/input5
Jul 18 07:18:38 darrein-desktop kernel: [   44.227132] ACPI: Power Button (FF) [PWRF]
Jul 18 07:18:38 darrein-desktop kernel: [   44.227260] input: Power Button (CM) as /devices/virtual/input/input6
Jul 18 07:18:38 darrein-desktop kernel: [   44.249325] Linux agpgart interface v0.102
Jul 18 07:18:38 darrein-desktop kernel: [   44.259020] ACPI: Power Button (CM) [PWRB]
Jul 18 07:18:38 darrein-desktop kernel: [   44.259144] input: Sleep Button (CM) as /devices/virtual/input/input7
Jul 18 07:18:38 darrein-desktop kernel: [   44.291731] ACPI: Sleep Button (CM) [SLPB]
Jul 18 07:18:38 darrein-desktop kernel: [   44.293541] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 18 07:18:38 darrein-desktop kernel: [   44.434729] agpgart: Detected an Intel 865 Chipset.
Jul 18 07:18:38 darrein-desktop kernel: [   44.445768] agpgart: AGP aperture is 256M @ 0xc0000000
Jul 18 07:18:38 darrein-desktop kernel: [   44.562493] iTCO_vendor_support: vendor-support=0
Jul 18 07:18:38 darrein-desktop kernel: [   44.594213] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jul 18 07:18:38 darrein-desktop kernel: [   44.594351] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
Jul 18 07:18:38 darrein-desktop kernel: [   44.594399] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jul 18 07:18:38 darrein-desktop kernel: [   46.488755] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 18 07:18:38 darrein-desktop kernel: [   46.568633] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Jul 18 07:18:38 darrein-desktop kernel: [   46.568683] [fglrx] ASYNCIO init succeed!
Jul 18 07:18:38 darrein-desktop kernel: [   46.568904] [fglrx] PAT is enabled successfully!
Jul 18 07:18:38 darrein-desktop kernel: [   46.569557] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Jul 18 07:18:38 darrein-desktop kernel: [   46.760442] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 18 07:18:38 darrein-desktop kernel: [   46.760484] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1x.c:949: Model 1001 Rev 00000000 Serial 10011102
Jul 18 07:18:38 darrein-desktop kernel: [   48.481256] lp0: using parport0 (interrupt-driven).
Jul 18 07:18:38 darrein-desktop kernel: [   48.578156] Adding 1694816k swap on /dev/sdb5.  Priority:-1 extents:1 across:1694816k
Jul 18 07:18:38 darrein-desktop kernel: [   63.965952]          res 51/40:00:48:10:64/00:00:00:00:00/f1 Emask 0x9 (media error)
Jul 18 07:18:38 darrein-desktop kernel: [   64.143532] ata2.00: configured for UDMA/33
Jul 18 07:18:38 darrein-desktop kernel: [   64.159649] ata2.01: configured for UDMA/33
Jul 18 07:18:38 darrein-desktop kernel: [   64.159668] ata2: EH complete
Jul 18 07:18:38 darrein-desktop kernel: [   65.010952] sd 1:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
Jul 18 07:18:38 darrein-desktop kernel: [   65.014880] sd 1:0:1:0: [sdb] Write Protect is off
Jul 18 07:18:38 darrein-desktop kernel: [   65.017920] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 18 07:18:38 darrein-desktop kernel: [  218.381064] EXT3 FS on sdb1, internal journal
Jul 18 07:18:38 darrein-desktop kernel: [  219.453271] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 18 07:18:38 darrein-desktop kernel: [  220.045870] No dock devices found.
Jul 18 07:18:39 darrein-desktop kernel: [  220.849455] ppdev: user-space parallel port driver
Jul 18 07:18:39 darrein-desktop kernel: [  221.061856] audit(1216336719.237:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6777 profile="/usr/sbin/cupsd" namespace="default"
Jul 18 07:18:39 darrein-desktop kernel: [  221.183119] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul 18 07:18:39 darrein-desktop kernel: [  221.183130] apm: disabled - APM is not SMP safe.
Jul 18 07:18:39 darrein-desktop dhcdbd: Started up.
Jul 18 07:18:41 darrein-desktop kernel: [  223.259863] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 18 07:18:42 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 18 07:18:44 darrein-desktop kernel: [  226.221461] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 18 07:18:44 darrein-desktop kernel: [  226.630582] NET: Registered protocol family 17
Jul 18 07:18:47 darrein-desktop kernel: [  228.944397] [fglrx] Internal AGP support requested, but kernel AGP support active.
Jul 18 07:18:47 darrein-desktop kernel: [  228.944407] [fglrx] Have to use kernel AGP support to avoid conflicts.
Jul 18 07:18:47 darrein-desktop kernel: [  228.944415] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Jul 18 07:18:47 darrein-desktop kernel: [  228.944581] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 18 07:18:47 darrein-desktop kernel: [  228.944602] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 18 07:18:47 darrein-desktop kernel: [  228.944632] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 18 07:18:47 darrein-desktop kernel: [  228.944660] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Jul 18 07:18:47 darrein-desktop kernel: [  228.950589] [fglrx] GART Table is not in FRAME_BUFFER range 
Jul 18 07:18:47 darrein-desktop kernel: [  228.950606] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jul 18 07:18:47 darrein-desktop kernel: [  228.950610] [fglrx] Reserve Block - 1 offset =  0Xffff000 length = 0X1000
Jul 18 07:18:47 darrein-desktop kernel: [  229.125654] [fglrx] interrupt source 20008000 successfully enabled
Jul 18 07:18:47 darrein-desktop kernel: [  229.125666] [fglrx] enable ID = 0x00000004
Jul 18 07:18:47 darrein-desktop kernel: [  229.125681] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Jul 18 07:18:47 darrein-desktop kernel: [  229.125878] [fglrx] interrupt source 10000000 successfully enabled
Jul 18 07:18:47 darrein-desktop kernel: [  229.125885] [fglrx] enable ID = 0x00000005
Jul 18 07:18:47 darrein-desktop kernel: [  229.125891] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jul 18 07:18:48 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 18 07:18:48 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 18 07:18:48 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 18 07:18:48 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 18 07:18:48 darrein-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 18 07:18:49 darrein-desktop kernel: [  231.174109] NET: Registered protocol family 10
Jul 18 07:18:49 darrein-desktop kernel: [  231.174691] lo: Disabled Privacy Extensions
Jul 18 07:19:04 darrein-desktop pulseaudio[7464]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 18 07:19:04 darrein-desktop pulseaudio[7464]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.

```

---

### Post by unutbu on 2008-07-17
oliviacond, I'm sorry. This problem is beyond me.
I noticed in your dmesg 

```

res 51/40:00:48:10:64/00:00:00:00:00/f1 Emask 0x9 (media error)
ata2.01: status: { DRDY ERR }
ata2.01: error: { UNC }
```

I tried googling for these things as well as searching 
[https://bugs.launchpad.net/bugs/](https://bugs.launchpad.net/bugs/) but did not come up with anything definitive.

The only post which looked mildly useful was this:
[http://ubuntuforums.org/showpost.php?p=4960698&postcount=10](http://ubuntuforums.org/showpost.php?p=4960698&postcount=10)
and note that that was for a somewhat different set of error messages. 

The only suggestion I can come up with is try a different kernel (by compiling) or distro.

---

### Post by okdok on 2008-07-28
I came across this post while searching for a solution to the same error message.

Recently, I have had to manually fsck my root partition several times and was concerned that maybe I was on the verge of a drive failure on relatively new hardware.

After changing my bios to disable native SATA, the errors went away.

Hope this helps.

---

### Post by okdok on 2008-07-28
um.. it looks like i was a little to eager. The error is back. :(

---

### Post by okdok on 2008-07-30
In my case the, the  hard drive was the problem. It has not failed yet but I suspect that it may soon. I swapped it for another and the error went away.

-cheers

---

### Post by scorp123 on 2008-07-30
> **unutbu said:**
>  ```

res 51/40:00:48:10:64/00:00:00:00:00/f1 Emask 0x9 (media error)
ata2.01: status: { DRDY ERR }
ata2.01: error: { UNC }
``` That's a soon-to-be-dead hard drive. There is no fix for this. The only thing OP can do is throw that disk away and buy a new healthy one.

---

### Post by oliviacond on 2008-08-18
> **scorp123 said:**
> That's a soon-to-be-dead hard drive. There is no fix for this. The only thing OP can do is throw that disk away and buy a new healthy one.

:(

---

