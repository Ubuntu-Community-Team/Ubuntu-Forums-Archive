---
title: "K3B Issues"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Tumpster on 2008-10-06
Hey there, dvd's are not buring in K3B for me, or any program for that matter. When I set one up to run and burn for me it errors out and with that, here's the output of the log with K3B:
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-rt
Devices
-----------------------
_NEC DVD_RW ND-3520A 1.04 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

LITE-ON DVD SOHD-167T 9S19 (/dev/scd1, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 1320159 (2703685632 bytes)
Pipe throughput: 33669120 bytes read, 33664768 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: engaging DVD-R DAO upon user request...
/dev/scd0: reserving 1320159 blocks
:-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/scd0: "Current Write Speed" is 1.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1320159 -use-the-force-luke=dao:1320159 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
1320159
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.04% done, estimate finish Mon Oct  6 17:01:31 2008
  0.08% done, estimate finish Mon Oct  6 17:23:15 2008
  0.11% done, estimate finish Mon Oct  6 17:16:06 2008
  0.15% done, estimate finish Mon Oct  6 17:12:29 2008
  0.19% done, estimate finish Mon Oct  6 17:10:19 2008
  0.23% done, estimate finish Mon Oct  6 17:08:49 2008
  0.27% done, estimate finish Mon Oct  6 17:07:47 2008
  0.30% done, estimate finish Mon Oct  6 17:07:00 2008
  0.34% done, estimate finish Mon Oct  6 17:06:24 2008
  0.38% done, estimate finish Mon Oct  6 17:05:54 2008
  0.42% done, estimate finish Mon Oct  6 17:05:30 2008
  0.45% done, estimate finish Mon Oct  6 17:05:10 2008
  0.49% done, estimate finish Mon Oct  6 17:04:54 2008
  0.53% done, estimate finish Mon Oct  6 17:04:39 2008
  0.57% done, estimate finish Mon Oct  6 17:04:26 2008
  0.61% done, estimate finish Mon Oct  6 17:04:15 2008
  0.64% done, estimate finish Mon Oct  6 17:04:06 2008
  0.68% done, estimate finish Mon Oct  6 17:03:57 2008
  0.72% done, estimate finish Mon Oct  6 17:03:49 2008
  0.76% done, estimate finish Mon Oct  6 17:03:42 2008
  0.80% done, estimate finish Mon Oct  6 17:03:36 2008
  0.83% done, estimate finish Mon Oct  6 17:03:30 2008
  0.87% done, estimate finish Mon Oct  6 17:03:25 2008
  0.91% done, estimate finish Mon Oct  6 17:03:20 2008
  0.95% done, estimate finish Mon Oct  6 17:03:16 2008
  0.99% done, estimate finish Mon Oct  6 17:03:12 2008
  1.02% done, estimate finish Mon Oct  6 17:03:08 2008
  1.06% done, estimate finish Mon Oct  6 17:03:05 2008
  1.10% done, estimate finish Mon Oct  6 17:03:02 2008
  1.14% done, estimate finish Mon Oct  6 17:02:58 2008
  1.17% done, estimate finish Mon Oct  6 17:02:56 2008
  1.21% done, estimate finish Mon Oct  6 17:04:15 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid WallE -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-craig/k3bvL8Y7b.tmp -rational-rock -hide-list /tmp/kde-craig/k3bh3OxTb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-craig/k3bVG3zPb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-craig/k3bPcrgka.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid WallE -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-craig/k3bIDDiUb.tmp -rational-rock -hide-list /tmp/kde-craig/k3bPP00nc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-craig/k3b758gcc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-craig/k3b8KcoJb.tmp 



Does anyone have any ideas on how to take care of this? Any help is appreciated! Thanks everyone!

---

### Post by nowshining on 2008-10-06
i had issues with k3b - burn at 4x or less :) the errors should go away...

---

### Post by Tumpster on 2008-10-06
> **nowshining said:**
> i had issues with k3b - burn at 4x or less :) the errors should go away...

I already tried that and I still have the same issues.

---

### Post by cariboo on 2008-10-07
Have a look at this part of the log:

> Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: engaging DVD-R DAO upon user request...
/dev/scd0: reserving 1320159 blocks
:-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/scd0: "Current Write Speed" is 1.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
media is not formatted or unsupported.
write failed: Wrong medium type


You may want to try a different brand of disks.

Jim

---

### Post by bobpur on 2008-10-07
I agree with Cariboo907. My issues with K3B cleared up as soon as I went to another brand of CD.

It's hard to remember now, but I think the 52X cd were the problem. Try another brand and something less than 52X. 

Good Luck.

---

### Post by Tumpster on 2008-10-07
See the other problem is, it's had no issue in the past burning on these dvds......


I just don't wanna buy a type and it's "not liked" by my pc and thats money wasted.....

---

