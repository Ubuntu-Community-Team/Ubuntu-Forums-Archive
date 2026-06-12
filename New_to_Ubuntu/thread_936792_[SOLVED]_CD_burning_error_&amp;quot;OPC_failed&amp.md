---
title: "[SOLVED] CD burning error &amp;quot;OPC failed&amp;quot; with K3b"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by MattThLinuxNewb on 2008-10-03
Hi,
When trying to burn an iso to a CD with K3b I get this error:
"OPC failed. Probably the writer does not like the medium"
Now the last time I burned a CD was with Dapper (ah the good old days) with the same hardware and CD-R brand, and it worked fine. (I'm using Hardy now)
After a lot of searching I came across a guide to replacing wodim with the original cdrtools (here's the post: [http://ubuntuforums.org/showpost.php?p=5552555&postcount=5](http://ubuntuforums.org/showpost.php?p=5552555&postcount=5)) which seemed to work for some people.
Unfortunately I still get the same error :(
Here's the error log:
```

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
TSSTcorp CD-R/RW SH-R522C TS01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a50

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
Cdrecord-ProDVD-ProBD-Clone 2.01.01a50 (i686-pc-linux-gnu) Copyright (C) 1995-2008 Jörg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CD-R/RW SH-R522C'
Revision       : 'TS01'
Device seems to be: Generic mmc CD-RW.
Current: CD-R
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1016064 = 992 KB
FIFO size      : 4194304 = 4096 KB
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   694 MB        
Total size:      797 MB (79:01.02) = 355577 sectors
Lout start:      797 MB (79:03/02) = 355577 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
    Capacity  Blklen/Sparesz.  Format-type  Type
           0             2048         0x00  Formatted Media
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 4269
Starting to write CD/DVD/BD at speed 52 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/opt/schily/bin/cdrecord: Input/output error. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.943s timeout 200s
/opt/schily/bin/cdrecord: OPC failed.
Writing  time:    6.965s
BURN-Free was never needed.
/opt/schily/bin/cdrecord: fifo had 64 puts and 0 gets.
/opt/schily/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/opt/schily/bin/cdrecord -v gracetime=2 dev=/dev/scd0 speed=52 -dao driveropts=burnfree -overburn -data -tsize=355577s - 

```

Any help would be great, I'm trying to burn an ubuntu iso image for a friend.
Thanks, Matt

---

### Post by NewJack on 2008-10-03
What version of K3b are you using? Are you sure you have all of the dependencies satisfied?  Here is a link to the K3b site showing the requirements:

[http://k3b.plainblack.com/requirements](http://k3b.plainblack.com/requirements)

Hope that helps!

Joe

---

### Post by MattThLinuxNewb on 2008-10-03
Hi,
I'm using version 1.0.4 and the dependencies are satisfied as far as I can tell. I don't think the problem is with k3b, it's just a front-end for cdrecord... I get the same error using Brasero and Gnome-Baker as well.
Matt

---

### Post by MattThLinuxNewb on 2008-10-04
Update: After some more frustration I eventually copied the image to our windows PC (which burns CDs fine) and tried burning to the same disk, and the same error occured - that the medium wasn't acceptable. The next disk I tried worked however.
I haven't tried burning again with my linux machine yet (the coasters are piling up), but I'd say the error message was legit afterall.
They were TDK CD-Rs btw. Won't be buying them again :)
Cheers,
Matt

---

### Post by NewJack on 2008-10-04
I would say when you buy another brand of CD, give it a shot again with either Brasero or K3b

---

