---
title: "Burning problems in Hardy"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Orographic on 2008-11-05
I'm having burning issues in Hardy no matter what software I use. It seems to read CDs and DVDs fine but there are problems burning data to DVD RW and CD RW. The system freezes and I have to do a forced shutdown.

I have an Intel dual core 1.8mhz system with 2 gig of DDR2 ram and a Gigabyte 945 GZM-S2 motherboard, I think. Its a LG DVD dual layer, Sata drive that works fine in XP.

I'm new to Linux but really like it and would like to resolve this issue if possible. Any thoughts?

---

### Post by Cypher on 2008-11-05
What software have you used? Have you tried burning a slower speed to see if things are any better? If the physical drive is OK in XP, then there should be no reason for it not work in Ubuntu..

---

### Post by Orographic on 2008-11-05
K3B and Brasero. It burns fine in XP, I've just done more tests there with a CD RW as well as a DVD RW (high quality disks). 

I can read CDs fine but burning is problematic and freezes the system completely. Would Intrepid improve my chances of my sata drive being recognised properly? I also had this problem in Linux Mint where the whole computer just froze during a burn and I couldn't shut down. XP is running fine on another internal drive and also ran fine on this drive before I installed Ubuntu.

Yeah, have tried to burn slower speeds as well. It will start the burn but then freeze halfway through the process.

---

### Post by Cypher on 2008-11-05
If Brasero detects your drive OK and freezes during the write, I wouldn't think Intrepid would handle that any better. The Kernels beween Hardy and Intrepid are close enough that the functionality as far as SATA goes should be essentially the same.

I wouldn't imagine that the medium (CD-RW or DVD-RW) would necessarily cause things to freeze up, and most definetly not the whole system requiring a hard shutdown.

I also don't think it would matter which software you used if the issue was such that the system was freezing. 

Are you up to date on your Ubuntu? With Linux freezing, that's usually related to memory problems, but if XP is happy and your Ubuntu is happy doing everything else but freezes only during disc burning, that's a little strange..

I'm sorry..I'm fresh out of ideas..

---

### Post by Orographic on 2008-11-05
Yeah, me too. Its perhaps the only thing stopping me moving over to Ubuntu pretty much full-time. I've got Wine loading PS7 fine, GThumb is good for quick image work, UFraw for Raw etc but this Cd burning issue is a hassle...

My Ubuntu system runs pretty much perfectly until I try to burn...

---

### Post by xerman on 2008-11-06
Hello there,

I've been having those issues too. I tried the following:

GnomeBaker
Brasero
K3b
Nautilus Burn To

to try to record a data DVD for backup. I've tried different media, and also at slower speed than set by dvd recorder (LG super multi burner). 

Recording CD is not an issue. Just recording DVD. Most media used is Verbatim, so should not be an issue in here.

It is very annoying as this computer is used for work, and should not waste 10 DVD and the time of wasting those 10 DVD. This is why i can not recommend yet others to use ubuntu for work (i use it myself). Newbies will not stand this issues.

here is the error provided by k3b, brasero, gnomebaker. The only difference among them is the time spent before crash. 

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H42N RL00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW] [SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobrescritura restringida, Salto de capa]

Burned media
-----------------------
DVD-R secuencial

K3bIsoImager
-----------------------
mkisofs print size result: 2277181 (4663666688 bytes)
Pipe throughput: 4663666688 bytes read, 4663666688 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 8.2x1352KBps.
    5701632/4663666688 ( 0.1%) @1.2x, remaining 68:04 RBU 100.0% UBU   2.9%
   33521664/4663666688 ( 0.7%) @6.0x, remaining 18:24 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=7130h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing disc
```

Seems many others have this issue too. I will check in intrepid soon to see if this "bug" has been removed.
In the meantime, any help would be much apreciated.

Regards,
Xermán

---

### Post by Orographic on 2008-11-06
hi there,

Well, this is interesting. I've just installed Intrepid and it appears the issue is resolved, at least for now. I will experiment more later but it burned a CD/RW no problem in Brasero. I also had the options to slow the burn speed down but didn't in Hardy. Will post again later as I am busy for a few hours here in Australia.

---

### Post by Orographic on 2008-11-06
Hmm, I'm sorry to say that the problem continued with DVD/RW disks - high quality ones at that. I even installed K3B and it did the same thing. Will format the DVD/RW but it wont copy properly and then the system freezes and a forced shutdown is required.

I've tested my memory and done more burns in XP with no problems at all. This seems to be a real issue in Ubuntu and will keep newbies away, IMHO, if it is too pervasive. 

I'm sorry to say that I can't move to Linux yet which is sad as I have everything just about working perfectly but if I can't burn to DVD (CDs are no problem now) its just too much of a hassle.

Will keep fiddling around for a bit but its taking a lot of time with no resolution as yet...

---

### Post by xerman on 2008-11-07
Hello there again:

I have to note that now the issue keeps taking place even with CD's. The output for K3b is the following:

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H42N RL00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW] [SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobrescritura restringida, Salto de capa]

K3bIsoImager
-----------------------
mkisofs print size result: 347541 (711763968 bytes)
Pipe throughput: 21900032 bytes read, 21895680 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42N '
Revision       : 'RL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 17969 kB/s 102x CD 12x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data   678 MB        
Total size:      779 MB (77:13.88) = 347541 sectors
Lout start:      779 MB (77:15/66) = 347541 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 12308
Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 8468 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  678 MB written.
Track 01:    1 of  678 MB written (fifo 100%) [buf  99%]  20.1x.
Track 01:    2 of  678 MB written (fifo 100%) [buf  99%]  21.6x.
Track 01:    3 of  678 MB written (fifo 100%) [buf  99%]  22.5x.
Track 01:    4 of  678 MB written (fifo 100%) [buf  99%]  21.9x.
Track 01:    5 of  678 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:    6 of  678 MB written (fifo 100%) [buf  99%]  21.8x.
Track 01:    7 of  678 MB written (fifo 100%) [buf  99%]  22.7x.
Track 01:    8 of  678 MB written (fifo 100%) [buf 100%]  22.1x.
Track 01:    9 of  678 MB written (fifo 100%) [buf  99%]  22.6x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 12 49 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A E1 D8 C0 80 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.020s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 9586688 bytes
Writing  time:   22.234s
Average write speed 208.8x.
Min drive buffer fill was 99%
Fixating...
Fixating time:    5.375s
/usr/bin/wodim: fifo had 343 puts and 152 gets.
/usr/bin/wodim: fifo was 0 times empty and 135 times full, min fill was 95%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=48 -dao driveropts=burnfree -eject -data -tsize=347541s - 

mkisofs
-----------------------
347541
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.15% done, estimate finish Fri Nov  7 19:10:49 2008
  0.29% done, estimate finish Fri Nov  7 19:10:49 2008
  0.43% done, estimate finish Fri Nov  7 19:10:49 2008
  0.58% done, estimate finish Fri Nov  7 19:10:49 2008
  0.72% done, estimate finish Fri Nov  7 19:10:49 2008
  0.87% done, estimate finish Fri Nov  7 19:10:49 2008
  1.01% done, estimate finish Fri Nov  7 19:12:28 2008
  1.15% done, estimate finish Fri Nov  7 19:12:15 2008
  1.30% done, estimate finish Fri Nov  7 19:12:06 2008
  1.44% done, estimate finish Fri Nov  7 19:11:58 2008
  1.59% done, estimate finish Fri Nov  7 19:11:52 2008
  1.73% done, estimate finish Fri Nov  7 19:11:46 2008
  1.87% done, estimate finish Fri Nov  7 19:25:57 2008
  2.01% done, estimate finish Fri Nov  7 19:24:52 2008
  2.16% done, estimate finish Fri Nov  7 19:24:41 2008
  2.30% done, estimate finish Fri Nov  7 19:23:50 2008
  2.45% done, estimate finish Fri Nov  7 19:23:04 2008
  2.59% done, estimate finish Fri Nov  7 19:23:01 2008
  2.73% done, estimate finish Fri Nov  7 19:22:23 2008
  2.88% done, estimate finish Fri Nov  7 19:21:48 2008
  3.02% done, estimate finish Fri Nov  7 19:21:50 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid 20080126Trasmonte -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-xer/k3bZUEqgc.tmp -rational-rock -hide-list /tmp/kde-xer/k3bJEUI5b.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-xer/k3bdaQMSa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-xer/k3bWKvkZb.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid 20080126Trasmonte -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-xer/k3b556DGb.tmp -rational-rock -hide-list /tmp/kde-xer/k3blaUtkb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-xer/k3biQSxKa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-xer/k3bB2Jn5a.tmp 

```

So seems when it works it is just luck. Does not matter select low write speed. This seems to happen in SATA DVD Burner. I will check this weekend as i remember to have PATA DVD burner.

Regards
Xermán

---

### Post by mauud777 on 2008-11-07
I have a lot of problem with brasero just like but when i tried xfburn all the problem goes away 

xfburn rocks

ps : sorry for my bad English

---

