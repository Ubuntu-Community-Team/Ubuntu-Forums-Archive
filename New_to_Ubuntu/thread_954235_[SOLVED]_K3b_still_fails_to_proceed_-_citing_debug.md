---
title: "[SOLVED] K3b still fails to proceed - citing debugging output"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by simontaylor on 2008-10-21
back in beginner land again to update on my ongoing travails with K3b & Hardy Heron. Here is debugging output (apologies for length - did not edit, in hope that something might be hidden in the smallprint):

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 2.1.1a41

cdrecord
-----------------------
/opt/schily/bin/cdrecord: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits./opt/schily/bin/cdrecord: Cannot allocate memory. WARNING: Cannot do mlockall(2).
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 2.01.01a41 (i686-pc-linux-gnu) Copyright (C) 1995-2008 Jörg Schilling
TOC Type: 0 = CD-DA
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   50 MB (04:59.54) no preemp swab copy
Track 02: audio   55 MB (05:28.02) no preemp swab copy
Track 03: audio   47 MB (04:39.48) no preemp swab copy
Track 04: audio   74 MB (07:24.22) no preemp swab copy
Track 05: audio   53 MB (05:19.73) no preemp swab copy
Track 06: audio   44 MB (04:23.65) no preemp swab copy
Track 07: audio   65 MB (06:31.88) no preemp swab copy
Track 08: audio   48 MB (04:49.25) no preemp swab copy
Track 09: audio   54 MB (05:24.38) no preemp swab copy
Track 10: audio   36 MB (03:34.58) no preemp swab copy
Track 11: audio   43 MB (04:17.56) no preemp swab copy
Track 12: audio   33 MB (03:21.09) no preemp swab copy
Track 13: audio  110 MB (10:55.42) no preemp swab copy
Track 14: audio    3 MB (00:21.42) no preemp swab copy
Total size:      721 MB (71:30.28) = 321771 sectors
Lout start:      722 MB (71:32/21) = 321771 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
    Capacity  Blklen/Sparesz.  Format-type  Type
           0             2048         0x00  Unformated or Blank Media
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 38075
Starting to write CD/DVD/BD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   50 MB written.
/opt/schily/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 01 95 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
/opt/schily/bin/cdrecord: A write error occured.
/opt/schily/bin/cdrecord: Please properly read the error message above.
write track data: error after 952560 bytes
Writing  time:   29.832s
Average write speed 203.7x.
Fixating...
Fixating time:    1.134s
/opt/schily/bin/cdrecord: fifo had 79 puts and 16 gets.
/opt/schily/bin/cdrecord: fifo was 0 times empty and 1 times full, min fill was 81%.

cdrecord command:
-----------------------
/opt/schily/bin/cdrecord -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-simon/k3b_audio_0_01.inf /tmp/kde-simon/k3b_audio_0_02.inf /tmp/kde-simon/k3b_audio_0_03.inf /tmp/kde-simon/k3b_audio_0_04.inf /tmp/kde-simon/k3b_audio_0_05.inf /tmp/kde-simon/k3b_audio_0_06.inf /tmp/kde-simon/k3b_audio_0_07.inf /tmp/kde-simon/k3b_audio_0_08.inf /tmp/kde-simon/k3b_audio_0_09.inf /tmp/kde-simon/k3b_audio_0_10.inf /tmp/kde-simon/k3b_audio_0_11.inf /tmp/kde-simon/k3b_audio_0_12.inf /tmp/kde-simon/k3b_audio_0_13.inf /tmp/kde-simon/k3b_audio_0_14.inf 

my only thought is that the devil is but in one small and recurring detail: 

> Warning: Cannot raise RLIMIT_MEMLOCK limits.

Yours, in the hope that there is hope,

Simon Taylor

---

### Post by simontaylor on 2008-11-09
K3b working now with 8.10 upgrade. . . . although some suspicious glitches in acoustic playback . . . .

---

