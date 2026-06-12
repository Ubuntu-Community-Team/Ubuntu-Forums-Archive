---
title: "CDRecord Error With k3B"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Headstand on 2008-11-20
I've been trying to burn an .iso image but everytime it initializes, i get the same error nearly 12 seconds in: 
unable to fixate disc. 
cdrecord has no permission to open device.

Ive been trying to fix this for a day now to no avail. The debug report is as follows

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-8-generic
Devices
-----------------------
HP CD-Writer+ 9300 1.0c (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

TOSHIBA DVD-ROM SD-M1612 1004 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'CD-Writer+ 9300 '
Revision       : '1.0c'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 22322 kB/s 126x CD 16x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data     0 MB         padsize:  236 KB
Track 02: data   589 MB        
Total size:      677 MB (67:07.89) = 302092 sectors
Lout start:      677 MB (67:09/67) = 302092 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 57756
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
Speed set to 706 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of    0 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.025s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:    5.104s
Average write speed 798.9x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.009s timeout 480s
cmd finished after 0.009s timeout 480s
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    0.011s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=10 -tao -eject /usr/bin/cdrecord -data -tsize=301638s - 

SOMEONE HELP!!!

---

### Post by Keen101 on 2008-11-20
i don't use kde, so i can't help much. But, you could try a different program.

here is just one option. there are more.

```
sudo apt-get install brasero
```

---

### Post by David Canarias on 2008-11-21
I am having the same problems as you more or less. Did you manage to solve it as I haven't. Sometimes when I go to record a normal mp3 music Data CD I have no problems. Then all of the sudden up pops these errors. It is a case of using the same new discs and the same music file which I am trying to record 20 copies for friends. It's taking forever and driving me bananas.
As for Brasero, well this too is giving many problems so didn't work for me!
Best of luck to all of us and hope someone has a solution or suggestion.

---

### Post by Headstand on 2008-11-21
K3B: Image Burn w/TAO
unable to fixate
cdrecord has no permission to open the device

K3B: Music Disc w/TAO
unable to fixate
cdrecord has no permission to open the device


Brasero: Image Burn
The image does not seem to be a proper iso9660 file system.

Brasero: Music Disc
Program freezes when I try to add mp3 file

Im tearing my hair out!!!

---

### Post by eivind on 2008-12-09
Have you tried simply adding the user to burn the cd to the "disk" group?

sudo useradd -G disk your_username

---

### Post by gsocker on 2008-12-09
The real problem has nothing to do with permissions. From the error messages:
> Sense Code: 0x30 Qual 0x05 **(cannot write medium - incompatible format)** Fru 0x0
The fixation error contains the same text.
It appears that the drive does not like the disc for some reason.
Looking at the debug info, you are trying to write to  a CD-RW disc:
> 
Disk sub type: High speed Rewritable (CAV) media (1)
. 
Have you tried this with a plain CD-R?
If so, and it works, consider trying again with a different disc brand. Also make sure you are using the correct CD-RW version; the "high speed" discs usually cannot be written by drives lacking "high speed" or greater ratings on the CD-RW logo on the drive.

---

### Post by SonicSteve on 2009-01-02
For those who come across this thread I had the same issue. 
I found that I needed to 
sudo chmod 777 /media/cdrom
I then did the same to /media/cdrom0 and /media/cdrom1 
these are the filesystem mount points that the cd/dvd drives use. 
I did everything I could think of to /dev/scd0 and /dev/scd1 but the device listings seemed to be fine. It seemed to be a permissions problem with the automount of CD/DVD

---

