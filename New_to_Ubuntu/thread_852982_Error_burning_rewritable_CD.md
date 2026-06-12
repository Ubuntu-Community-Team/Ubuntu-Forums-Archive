---
title: "Error burning rewritable CD"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by mmasroorali on 2008-07-08
Dear All,
I am facing problem with two rewritable CD's (BASF, 650 MB, 74 min). When I try to burn data in them using k3b, everything goes well, but at the end error message is generated.

I am putting below the debugging output. Any suggestion will be appreciated.

(I have already posted to the k3b mailing list, but that is a very low volume list).

STARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTART

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-386
Devices
-----------------------
TSSTcorp CDW/DVD TS-H493A CD06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM]
[DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16,
RAW/R96P, RAW/R96R]

ASUS DRW-2014L1T 1.00 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R,
DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R
Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted
Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R,
CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R,
Restricted Overwrite, Layer Jump]
K3bIsoImager
-----------------------
mkisofs print size result: 6592 (13500416 bytes)
Pipe throughput: 13500416 bytes read, 13500416 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK
limits.
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'ASUS    '
Identification : 'DRW-2014L1T     '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0015 (DVD-R/DL sequential recording)
Profile: 0x0016 (DVD-R/DL layer jump recording)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0012 (DVD-RAM)
Profile: 0x0011 (DVD-R sequential recording)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1484032 = 1449 KB
FIFO size      : 12582912 = 12288 KB
Track 01: data    12 MB        
Total size:       14 MB (01:27.92) = 6594 sectors
Lout start:       15 MB (01:29/69) = 6594 sectors
Current Secsize: 2048
ATIP info from disk:
 Indicated writing power: 5
 Reference speed: 2
 Is not unrestricted
 Is erasable
 ATIP start of lead in:  -11625 (97:27/00)
 ATIP start of lead out: 335100 (74:30/00)
 1T speed low:  0 (reserved val  0) 1T speed high:  4
 power mult factor: 5 6
 recommended erase/write power: 3
 A1 values: 02 5C B0
Disk type:    Phase change
Manuf. index: 0
Manufacturer: Illegal Manufacturer code
Blocks total: 335100 Blocks current: 335100 Blocks remaining: 328506
RBlocks total: 353448 RBlocks current: 353448 RBlocks remaining: 346854
Starting to write CD/DVD at speed   0.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
  1 seconds.
  0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   12 MB written.
Track 01:    1 of   12 MB written (fifo  95%) [buf 100%]   7.1x.
Track 01:    2 of   12 MB written (fifo 100%) [buf 100%]   6.5x.
Track 01:    3 of   12 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    4 of   12 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    5 of   12 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    6 of   12 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    7 of   12 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    8 of   12 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    9 of   12 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   10 of   12 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   11 of   12 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   12 of   12 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01: Total bytes read/written: 13500416/13500416 (6592 sectors).
Writing  time:   26.225s
Average write speed   3.9x.
Min drive buffer fill was 100%
Fixating...

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=126 -tao driveropts=burnfree
-eject -multi -xa -tsize=6592s -

mkisofs
-----------------------
6592
I: -input-charset not specified, using utf-8 (detected in locale settings)
 7.75% done, estimate finish Tue Jul  8 14:51:39 2008
15.28% done, estimate finish Tue Jul  8 14:50:48 2008
22.80% done, estimate finish Tue Jul  8 14:50:31 2008
30.57% done, estimate finish Tue Jul  8 14:50:22 2008
38.09% done, estimate finish Tue Jul  8 14:50:17 2008
45.62% done, estimate finish Tue Jul  8 14:50:13 2008
53.14% done, estimate finish Tue Jul  8 14:50:12 2008
60.91% done, estimate finish Tue Jul  8 14:50:10 2008
68.43% done, estimate finish Tue Jul  8 14:50:09 2008
75.96% done, estimate finish Tue Jul  8 14:50:07 2008
83.48% done, estimate finish Tue Jul  8 14:50:06 2008
91.25% done, estimate finish Tue Jul  8 14:50:05 2008
Total translation table size: 0
Total rockridge attributes bytes: 265
Total directory bytes: 394
Path table size(bytes): 10
Max brk space used 0
6592 extents written (12 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid
en_ENetwork_SLM_v401 -volset  -appid K3B THE CD KREATOR (C) 1998-2006
SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX
-volset-size 1 -volset-seqno 1 -sort /tmp/kde-masroor/k3bVWEjhb.tmp
-rational-rock -hide-list /tmp/kde-masroor/k3bQIqw9b.tmp -joliet -joliet-long
-hide-joliet-list /tmp/kde-masroor/k3bm9KIfb.tmp -no-cache-inodes
-full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-masroor/k3boCL7nb.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid en_ENetwork_SLM_v401 -volset
-appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM
-publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort
/tmp/kde-masroor/k3boOdH2b.tmp -rational-rock -hide-list
/tmp/kde-masroor/k3bslVPia.tmp -joliet -joliet-long -hide-joliet-list
/tmp/kde-masroor/k3bvt8DGb.tmp -no-cache-inodes -full-iso9660-filenames
-iso-level 2 -path-list /tmp/kde-masroor/k3buwu0Ja.tmp

ENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDEND

---

### Post by DezSP on 2008-07-08
Perhaps I'm being blind, but I can't see any error message there. Could you clarify what the problem is?

---

### Post by mmasroorali on 2008-07-08
> **DezSP said:**
> Perhaps I'm being blind, but I can't see any error message there. Could you clarify what the problem is?

Sorry, I was not elaborate enough before. Attaching the screenshot. Also, the CD remains blank after this. So, I can not simply ignore this and take it to another computer.

---

