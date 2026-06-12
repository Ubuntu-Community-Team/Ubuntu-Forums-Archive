---
title: "Low performance of SATA 3.0 (6.0 Gbps) HDD"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-05
I believe the performance of SATA 3.0 (6.0 Gbits) HDD went down sometime during latest Oneiric Alpha versions.

**TEST 1: WD Black 7.200RPM _64MB_ Cache _SATA 3.0_ HDD**
```

$ sudo hdparm -i /dev/sda
/dev/sda:

 Model=WDC WD1002FAEX-00Y9A0, FwRev=05.01D05, SerialNo=WD-WCAW31781487
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   7062 MB in  2.00 seconds = _3531.69 MB/sec_
 Timing buffered disk reads: 386 MB in  3.00 seconds = _128.48 MB/sec_

```

**TEST 2: Seagate 1.5TB 7.200RPM _32MB_ Cache _SATA 2.0_ HDD**
```

$ sudo hdparm -i /dev/sda
/dev/sda:

 Model=ST31500341AS, FwRev=CC1H, SerialNo=9VS4N2BM
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=2930277168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   7834 MB in  2.00 seconds = _3918.19 MB/sec_
 Timing buffered disk reads: 364 MB in  3.00 seconds = _121.15 MB/sec_

```

**TEST 3: MDADM RAID 5  (5 x Seagate 1.5TB 7.200RPM _32MB_ Cache _SATA 2.0_ HDD**)
```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid5 sda1[0] sdc1[4] sdd1[2] sde1[3] sdb1[1]
      5860544512 blocks level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/11 pages [0KB], 65536KB chunk

unused devices: <none>
$ sudo hdparm -Tt /dev/md3

/dev/md3:
 Timing cached reads:   8370 MB in  2.00 seconds = _4185.92 MB/sec_
 Timing buffered disk reads: 538 MB in  3.01 seconds = _179.00 MB/sec_

```

So... It's quite unusual for me to see a single SATA 3.0 (6.0 Gbps) WD Black HDD with speeds lower than a single SATA 2 or lower than a RAID 5 MDADM of SATA 2 Seagate HDD with half the cache of the WD BLack. Something's definitely wrong.

Also, I'm pretty sure the numbers for single SATA 2 and RAID 5 (5x SATA2) used to be higher. The RAID feels sluggish.

I haven't changed the controller. It's AMD SB850 chipset. I am using proper SATA 3.0 cables (and have tried using new cables). I have done the above tests with a couple spare new HDD (same models) and reached the same results more or less. 

Anyone seeing something similar? If possible, it would be great if someone could run some hdparm tests in their systems, just to make sure before I post a bug report. 

Regards,
Effenberg

---

### Post by ventrical on 2011-09-06
For the past 2 days I have been trying to built a machinewith a proprietary Intell MoBo, 2.66GHz DualCore and a SATA 500GB HDD!!

 Absolutely no luck! I have tried to install Xubuntu and Lucid and the CDs keep telling me that the "installer has failed - will have to install from the desktop" and then it doesn't install.

 Oneiric Ocelot at least installs but there is NO WAY that I can get the desktop to come up. I can put a WD Caviar 7,5GB IDE and it will run Lucid from a previous install very well indeed - but I can't install nothing. I disabled fast-boot and that did nothign either. I check out another forum - followed the scripts there and still can't get Oneric to come up with desktop on that machine.

  i am just wondering if there is a certain way that the Ubuntus have to be installed on a SATA HDD? I want to set up this drive so I can  beta test more proficiently.

---

### Post by effenberg0x0 on 2011-09-06
Ventrical, I had problems installing Ubuntu too. See thread [http://ubuntuforums.org/showthread.php?t=1835503](http://ubuntuforums.org/showthread.php?t=1835503). In my case, I managed to succeed by using two methods:

1) I have wasted a lot of time with installing errors. The install problem seem to have something to do with formatting / partitioning of disks part of the process. The solution is to use use Linux (Live Distro, etc) or Windows to fully format the disk prior to attempting the installation.

2) Install using the alternate CD ISO burned to USB (the USB method is described in Ubuntu download page). Make sure your machine BIOS can boot from USB (I'm pretty sure it can). You can actually use this Live USB ISO to perform step 1 if you'd like to try. On the Live USB you can mount /dev/sda and format it using fdisk / gparted, etc.

Anyway, I don't think it has anything to do with IDE/SATA. Using SATA-II HDD is pretty much standard for the last years, for many versions of Ubuntu... since Edgy Eft I believe (not sure, probably even before it). 

Now, regarding SATA 3.0, I am pretty sure something is still not working properly. Booting to Windows gives me almost 40% more performance on this type of HDD.

Regards,
Effenberg

---

### Post by MacUntu on 2011-09-06
No problem here with an SSD on Intel z68:

[IMG]http://img.xrmb2.net/images/285484.png[/IMG]

Also, my WD Green WD20EARX isn't slower when connected via SATA-III.

You could compare speeds with live CDs from Natty and Oneiric using the Disk Utility.

---

### Post by effenberg0x0 on 2011-09-06
I just did. See the results table:

**WD Caviar Black 7.200 64MB SATA 3.0**
<html>
<table>
<tr>
<td>OS</td>
<td>Scheme</td>
<td>Read Speed</td>
</tr>
<tr>
<td>Windows 7 Enterprise 64 Bits</td>
<td>Single HDD</td>
<td>5.132,58 MB/Sec</td>
</tr>
<tr>
<td>Ubuntu Natty</td>
<td>Single HDD</td>
<td>4.362,93 MB/Sec</td>
</tr>
<tr>
<td>Ubuntu Oneiric</td>
<td>Single HDD</td>
<td>3.531.60 MB/Sec</td>
</tr>
</table>
</html>

I am gonna work on compiling a new kernel today, aimed at my CPU and with some fixes / patches. Will post results ASAP.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-06
I'll try a format with Lucid an get back here.

---

### Post by ventrical on 2011-09-06
OK .. I think what happened is that I do not have the correct video driver because no mater what I try it keeps  going back to terminal. I try 'startx' and all that other code and it tells me somthingabout Radeon and that No screens found.  

 Since I am trying toset that PC for Oneiric I think it OK to ask:

1. How to find out what type of video hardware I have from terminal.
2. How do I install the right video driver so I can get a desktop?

 Thanks

---

### Post by lucazade on 2011-09-06
> **ventrical said:**
> OK .. I think what happened is that I do not have the correct video driver because no mater what I try it keeps  going back to terminal. I try 'startx' and all that other code and it tells me somthingabout Radeon and that No screens found.  

 Since I am trying toset that PC for Oneiric I think it OK to ask:

1. How to find out what type of video hardware I have from terminal.
2. How do I install the right video driver so I can get a desktop?

 Thanks

Ventrical, try to not go OT.. this thread is about hdd performances.
I suggest to open a new one for that topic, otherwise it is difficult to follow the discussion.

---

### Post by fjgaude on 2011-09-06
```
/dev/sda:
 Timing cached reads:   10372 MB in  2.00 seconds = 5188.43 MB/sec
 Timing buffered disk reads: 366 MB in  3.02 seconds = 121.35 MB/sec
```

That's what I get from SATA 2.0 (3.0 Gbps), WD VelociRaptor 300GB, 32MB cache, drive. Disk Utility shows the same, w/ 7ms ave. seek.

---

### Post by effenberg0x0 on 2011-09-07
fjgaude, you are getting a superior performance on SATA 2 then I am getting on a faster HDD on Sata 3. This is proof enough to me that there's something very wrong here. I'll keep on trying to find the cause and will post back results. Thank you for help.

Regards,
Effenberg

---

