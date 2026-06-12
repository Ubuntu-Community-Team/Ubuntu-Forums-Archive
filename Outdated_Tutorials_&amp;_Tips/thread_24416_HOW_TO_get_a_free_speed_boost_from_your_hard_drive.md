---
title: "HOW TO: get a free speed boost from your hard drive"
date: 2005-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by jonny on 2005-04-06
Warning.  The advice contained in this How To is risky.  It might destroy your system.  You have been warned!

Many operations on a PC are I/O constrained.  In day-to-day operation, my processor rarely reaches 100%, but my hard drive is often struggling to keep up.  But, by default, Hoary doesn't use the fastest possible settings for disk access; it's a little safety conscious.  On my newish Dell laptop, these tips speed up my hard drive by 60%, noticeably improving system responsiveness.  And nothing's crashed... yet.

First find out how fast your hard drive is.  Fire up a terminal end enter```
sudo hdparm -t -T /dev/hda
```(Change hda for your own hard drive's device number; if you don't know, you're probably not yet ready for this guide).  Do this three times, and note the average result.

Now we need to understand the drive's capabilities.  Use```
sudo hdparm -i /dev/hda
```to tell you.  If you're really interested, try```
sudo hdparm -I /dev/hda
```to get more details.

First, look for two settings: MultSec and MaxMultSec.  According to the manual, "multiple sector mode, is a feature of most modern IDE hard drives, permitting the transfer of multiple sectors per I/O interrupt, rather  than  the  usual one  sector  per  interrupt.  When this feature is enabled, it typically reduces operating system overhead for disk I/O by 30-50%.  On many systems, it also provides increased data throughput of anywhere from 5% to 50%."  Despite this, you'll probably find that MultSec is off, even if it's supported by your drive, as "Some drives claim to support  multiple  mode,  but lose data at some settings.  Under rare circumstances, such failures can result in **massive filesystem corruption**.

If you're willing to risk it - remember, it may not be wise  [-X  - enter```
sudo hdparm -m <your MaxMultSec value> /dev/hda
```Check out your results again, and enjoy the free performance boost.

Now it's time to enable 32-bit I/O.  In these days of 64 bit processors, it's a shame to have bits of the system pretending they're in the 1980s - but that's what Hoary seems to do to some drives.  Establish the position with```
sudo hdparm -c /dev/hda
```If the result is 0, you're still in the dark ages.  Cross your fingers, and try this:```
sudo hdparm -c 3 /dev/hda
```It worked for me.  A final speed check showed my hard drive was 60% faster - and it felt it, too.  But if it blew away your system's brains... I did warn you.

Now all I need to do is work out which config file I have to edit to make this happen at boot time.  Does anyone know?

---

### Post by WMCoolmon on 2005-04-06
I can vouch for the second method. :)

Before:
 Timing cached reads:   2020 MB in  2.00 seconds = 1008.64 MB/sec
 Timing buffered disk reads:  130 MB in  3.03 seconds =  42.95 MB/sec

After:
 Timing cached reads:   2532 MB in  2.00 seconds = 1264.93 MB/sec
 Timing buffered disk reads:  148 MB in  3.00 seconds =  49.29 MB/sec

---

### Post by Technoviking on 2005-04-06
This had little effect on my laptop, but laptops are a different animal.

Mike

---

### Post by vnbuddy2002 on 2005-04-06
I really suggest against using HDPARM if it is not really necessary. In most of the motherboard, DMA can turn on by using the Bios settings.

The most concern about using HDPARM is the constant system lock up. If you try to copy large files, you will sometimes experience "/dev/hd* time out" and the HDPARM will return back to DMA=off (even DMA is on in your BIOS) and you will stuck with ~1.4Mb/sec. This is one of many factors that causes system lockups.

:) Good luck! if you insist to try.

---

### Post by Footfish on 2005-04-06
[QUOTE=jonny]
Now all I need to do is work out which config file I have to edit to make this happen at boot time.  Does anyone know?[/QUOTE]
Check out /etc/hdparm.conf  :smile:

---

### Post by bigzak on 2005-04-07
[QUOTE=vnbuddy2002]I really suggest against using HDPARM if it is not really necessary. In most of the motherboard, DMA can turn on by using the Bios settings.[/QUOTE]

My DVD and CD/RW have DMA enabled at boot by most distros, including Warty. Hoary has it disabled, which destroys DVD playback and limits burning to about 16x (52x drive). Quick hack of /etc/hdparm.conf fixes that problem.

---

### Post by j_baer on 2005-04-07
To have your system load hdparm commands at boot, edit the hdparm.conf file.

For the details search the forums for "hdparm.conf" to find the answer.

Cheers ...

---

### Post by xodeus on 2005-04-07
What about SATA disks?
Are there any differences?

---

### Post by HungSquirrel on 2005-04-07
[QUOTE=WMCoolmon]I can vouch for the second method. :)

Before:
 Timing cached reads:   2020 MB in  2.00 seconds = 1008.64 MB/sec
 Timing buffered disk reads:  130 MB in  3.03 seconds =  42.95 MB/sec

After:
 Timing cached reads:   2532 MB in  2.00 seconds = 1264.93 MB/sec
 Timing buffered disk reads:  148 MB in  3.00 seconds =  49.29 MB/sec[/QUOTE]
 O_O  My drives are incredibly slow compared to yours.  Is this normal?

```
$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   792 MB in  2.01 seconds = 394.68 MB/sec
 Timing buffered disk reads:  100 MB in  3.00 seconds =  33.28 MB/sec
```

---

### Post by vnbuddy2002 on 2005-04-07
[QUOTE=HungSquirrel]O_O  My drives are incredibly slow compared to yours.  Is this normal?

```
$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   792 MB in  2.01 seconds = 394.68 MB/sec
 Timing buffered disk reads:  100 MB in  3.00 seconds =  33.28 MB/sec
```[/QUOTE]

It seems normal to me. The speed also depends on the speed of your hard drive also. Average hard drive speed for IDE hard drives (7200RPM) is ~ 32.00 Mb/sec  (on Mode 2 Ultra ATA).

---

### Post by jdong on 2005-04-07
If your drive supports Ultra DMA, try **-X69** (=UDMA133, reduce number to reduce DMA level).

Consult the hdparm man page for more details.

Also, the author did a very nice job with the danger disclaimers. However, just in case you didn't hear them, here's my disclaimers:

**BACK UP ALL DATA** -- On buggy IDE chipsets, you can get massive corruption from applying seemingless harmless commands (i.e. enable 32-bit IO). Don't underestimate the damage!

**Apply good statistical methodology to your comparisons** -- hdparm is a very deceptive "benchmark". Search up "bonnie++" or "iozone" for a **REAL** disk benchmark. For example, on my IDE RAID0, hdparm reports a speed of 33MB/s, while bonnie++ can benchmark 70+MB/s speed. Take multiple samples to make sure the results are consistent.

---

### Post by Whiffle on 2005-04-07
HDParm is extremely useful, just make sure not to go too crazy with the settings or you'll lock up your computer.  It also helps to make sure you've got all the right drivers loaded, otherwise it won't work very well.

Here's where I'm at right now, on a Maxtor 160gb 8mb cache ATA133 7200 rpm hd.   (up from 51mb/s out of the box)
/dev/hda:
 Timing cached reads:   1752 MB in  2.00 seconds = 876.57 MB/sec
 Timing buffered disk reads:  172 MB in  3.03 seconds =  56.83 MB/sec

Maxtor 80gb 2 mb cache 7200 rpm ATA133, didn't get any faster by tweaking.
/dev/hdb:
 Timing cached reads:   1764 MB in  2.00 seconds = 880.81 MB/sec
 Timing buffered disk reads:  122 MB in  3.05 seconds =  40.02 MB/sec

What speeds you can get also depend alot on the hardware.

---

### Post by telmo on 2005-04-07
WOW! This really works! It's the best performance boost i've done in my laptop.
I really can see good changes. My folders open faster.
Thank you!

---

### Post by dejitarob on 2005-04-07
To save on boot edit your /etc/hdparm.conf to include:
```
/dev/hda {
	mult_sect_io = <your MaxMultSec value>
	io32_support = 3
}
```

---

### Post by remmelt on 2005-04-08
```
/dev/sda:
 Timing cached reads:   3504 MB in  2.00 seconds = 1751.39 MB/sec
 Timing buffered disk reads:  182 MB in  3.00 seconds =  60.66 MB/sec

```
that's with 32 bit access enabled. it was the same with 16 bit access, though.. no change.

about the MaxMultSec parameter, where do I see that? is that what is listed when I hdparm -i /dev/sda? because that tells me "0". which is not a lot. it doesn't list MultSec, either. maybe it is different for a SATA disk (Maxtor 200M0).

on the other hand, when I compare the speeds listed here with my own, I can't really complain, now can I? :)

---

### Post by p!=f on 2005-04-08
[QUOTE=xodeus]What about SATA disks?
Are there any differences?[/QUOTE]
Yes, SATA devices are handled using SCSI subsystem so hdparm doesn't work with them.

---

### Post by wernst on 2005-04-08
I just thought I would mention that this doesn't ALWAYS work. I have a notebook with a BX chipset and a nice, new, speedy 7200 RPM notebook drive from Hitachi. UDMA2 is enabled by default, and any alterations tried with HDPARM resulted in a minor DECREASE in speed, as measured with "bonnie" and hdparm itself.

No harm done, of course, but one should always test these sorts of things before blindly assuming that they work all on the time on all the machines tried out on...

-Warr

---

### Post by WMCoolmon on 2005-04-09
[QUOTE=HungSquirrel]O_O  My drives are incredibly slow compared to yours.  Is this normal?

```
$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   792 MB in  2.01 seconds = 394.68 MB/sec
 Timing buffered disk reads:  100 MB in  3.00 seconds =  33.28 MB/sec
```[/QUOTE]

Hmm, I've got an AMD64 2800+, one ATA-100 IDE drive, and 512MB of DDR400 ram.. are your CPU/memory/hard drive speeds significantly slower?

Make sure you're running in DMA mode, too, I've found that makes a HUGE difference.

---

### Post by seven on 2005-04-09
worked great

 Timing cached reads:   2956 MB in  2.00 seconds = 1476.75 MB/sec
 Timing buffered disk reads:  162 MB in  3.04 seconds =  53.35 MB/sec

I got P4 2.6 with 512 DDR mem and a WD SATA 80GB drive

---

### Post by Xylene on 2005-04-09
Be glad you aren't stuck on the slow POS HDD or IDE controller I have. One or the other is a pile of crap. I had a hell of a time getting it working fast in Gentoo and actually, I never succeeded now that I think about it. The Gentoo LiveCD would give me great performance, but installed.. bad news. Looks like Ubuntu is like that for me too.

I tried everything.

root@xylentium:/home/anthony # hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   252 MB in  2.00 seconds = 125.83 MB/sec
 Timing buffered disk reads:   26 MB in  3.04 seconds =   8.55 MB/sec

-----------------------------------------------------------------------------------

root@xylentium:/home/anthony # hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   252 MB in  2.00 seconds = 125.83 MB/sec
 Timing buffered disk reads:   26 MB in  3.04 seconds =   8.55 MB/sec
root@xylentium:/home/anthony # hdparm -i /dev/hda

/dev/hda:

 Model=ST320413A, FwRev=3.32, SerialNo=7ED0Y1QN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=512kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=39102336
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:  1 2 3 4

 * signifies the current active mode

-----------------------------------------------------------------------------------------------

The IDE controller seems to be "0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)"

Anyone else have this and the same problems?

---

### Post by p!=f on 2005-04-09
[QUOTE=Xylene]Be glad you aren't stuck on the slow POS HDD or IDE controller I have. One or the other is a pile of crap. I had a hell of a time getting it working fast in Gentoo and actually, I never succeeded now that I think about it. The Gentoo LiveCD would give me great performance, but installed.. bad news. Looks like Ubuntu is like that for me too.

I tried everything.

root@xylentium:/home/anthony # hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   252 MB in  2.00 seconds = 125.83 MB/sec
 Timing buffered disk reads:   26 MB in  3.04 seconds =   8.55 MB/sec

-----------------------------------------------------------------------------------

root@xylentium:/home/anthony # hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   252 MB in  2.00 seconds = 125.83 MB/sec
 Timing buffered disk reads:   26 MB in  3.04 seconds =   8.55 MB/sec
root@xylentium:/home/anthony # hdparm -i /dev/hda

/dev/hda:

 Model=ST320413A, FwRev=3.32, SerialNo=7ED0Y1QN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=512kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=39102336
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:  1 2 3 4

 * signifies the current active mode

-----------------------------------------------------------------------------------------------

The IDE controller seems to be "0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)"

Anyone else have this and the same problems?[/QUOTE]

Your performance **may** dramatically increase if you recompile the kernel with IDE compiled in the kernel instead of as a module. On the other side, your new kernel may not boot at all which is not that big deal since you have Ubuntu default one to boot. Worth a try, though.

---

### Post by Xylene on 2005-04-09
[QUOTE=p!=f]Your performance **may** dramatically increase if you recompile the kernel with IDE compiled in the kernel instead of as a module. On the other side, your new kernel may not boot at all which is not that big deal since you have Ubuntu default one to boot. Worth a try, though.[/QUOTE]
Meh. I doubt it. I had it like that in Gentoo, didn't make any difference. Seems like this device just likes a certain config that I haven't been able to figure out yet.

---

### Post by jdong on 2005-04-09
[QUOTE=p!=f]Your performance **may** dramatically increase if you recompile the kernel with IDE compiled in the kernel instead of as a module.[/QUOTE]

That doesn't make sense. After a kernel module inserts, it's exactly like a part of the kernel.

---

### Post by p!=f on 2005-04-09
[QUOTE=jdong]That doesn't make sense. After a kernel module inserts, it's exactly like a part of the kernel.[/QUOTE]
I can prove it on my machine. With IDE as a module copying large files around the system is incredibly slow.

---

### Post by Muchacho_Gasolino on 2005-04-09
none of this works for me
i have a SATA drive though, but it is also getting much slower readings than others i see here

max@Poet:~ $ sudo hdparm -t -T /dev/sda

/dev/sda:
 Timing cached reads:   1372 MB in  2.00 seconds = 685.08 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.64 MB/sec
max@Poet:~ $ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST380013AS      3.18, FwRev=3.18, SerialNo=
 Config={ }
 RawCHS=9729/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=9729/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no

 * signifies the current active mode

max@Poet:~ $ sudo hdparm -m 16 /dev/sda

/dev/sda:
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
max@Poet:~ $ sudo hdparm -m 8 /dev/sda

/dev/sda:
 setting multcount to 8
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
max@Poet:~ $ sudo hdparm -c /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
max@Poet:~ $ sudo hdparm -c 3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
max@Poet:~ $

 :-s

---

### Post by PinGzor on 2005-04-09
hdparm doesnt work well with SATA disks.

---

### Post by Muchacho_Gasolino on 2005-04-09
but hdparm gets readings from it, and says that multisect is off and it is running in 16-bit mode... or does that mean nothing because those hdparm settings arent used?
is there a different way to fix these things for SATA drives?
i have two Seagate 7200rpm drives, an 80 and a 120

---

### Post by Thorongil on 2005-04-09
Samsung SP16 8MB Cache here:

```

/dev/hda:
 Timing cached reads:   568 MB in  2.03 seconds = 280.40 MB/sec
 Timing buffered disk reads:  152 MB in  3.03 seconds =  50.24 MB/sec
root@evil-master:/etc/apt# sudo hdparm -i /dev/hda

/dev/hda:

 Model=SAMSUNG SP1614N, FwRev=TM100-24, SerialNo=0642J1FWA21964
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=65535/1/63, CurSects=4128705, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode

root@evil-master:/etc/apt# sudo hdparm -c /dev/hda

/dev/hda:
 IO_support   =  1 (32-bit)
root@evil-master:/etc/apt# sudo hdparm -m 16 /dev/hda

/dev/hda:
 setting multcount to 16
 multcount    = 16 (on)
root@evil-master:/etc/apt# hdparm -t -T /dev/hda

/dev/hda:
 Timing cached reads:   940 MB in  2.00 seconds = 469.60 MB/sec
 Timing buffered disk reads:  162 MB in  3.00 seconds =  53.94 MB/sec

```

Yeah, it boosts from 50MB/s to 53MB/s !  :^o 

32bit is on by default, UDMA-5 also, I don't enter the multsect mode to hdparm.conf .... running XFS here, I don't want to **** this up *ggg*

---

### Post by BoHu on 2005-05-01
Before:

/dev/hdb:
 Timing cached reads:   100 MB in  2.08 seconds =  48.04 MB/sec
 Timing buffered disk reads:   32 MB in  3.16 seconds =  10.12 MB/sec


After:

/dev/hdb:
 Timing cached reads:    80 MB in  2.11 seconds =  37.88 MB/sec
 Timing buffered disk reads:   24 MB in  3.05 seconds =   7.86 MB/sec

---

### Post by muzza on 2005-05-18
Didn't work for me, I actually went down slightly, from avg 163 to avg 145

---

### Post by henriquemaia on 2005-05-19
This is about tweaking your configuration in general, not about hdparm in particular. Read this:

[**Linux in Government: Optimizing Desktop Performance, Part I**](http://www.linuxjournal.com/article/8308)


Nice article, nice tips. My box is much faster now (specially after lowering swap access).

---

### Post by buildid on 2005-05-19
/dev/sda:
 Timing cached reads:   1752 MB in  2.02 seconds = 867.89 MB/sec
 Timing buffered disk reads:  164 MB in  3.26 seconds =  50.35 MB/sec


fast enough .......

---

### Post by Kyral on 2005-05-19
I think it slowed mine down....

Western Digital 300GB IDE HD

Before
[I]/dev/hda:
 Timing cached reads:   1304 MB in  2.00 seconds = 651.12 MB/sec
 Timing buffered disk reads:  166 MB in  3.03 seconds =  54.85 MB/sec[/I] 


After
[I]/dev/hda:
 Timing cached reads:   1248 MB in  2.00 seconds = 622.54 MB/sec
 Timing buffered disk reads:  ^[[A176 MB in  3.02 seconds =  58.19 MB/sec[/I]

---

### Post by hard_i on 2005-05-19
/dev/hda:
 Timing cached reads:   2068 MB in  2.00 seconds = 1032.09 MB/sec
 Timing buffered disk reads:  162 MB in  3.01 seconds =  53.90 MB/sec

hitachi deskstar , 40gb/7200rpm/2MB cache , UDMA-5
Good engough for me  :)

---

### Post by Dethread on 2005-05-19
Hitachi HTS548040M9AT00 40GB 5400RPM laptop hard drive.

Before:
/dev/hda:
 Timing cached reads:   2264 MB in  2.00 seconds = 1131.04 MB/sec
 Timing buffered disk reads:  108 MB in  3.00 seconds =  35.99 MB/sec


After:
/dev/hda:
 Timing cached reads:   2500 MB in  2.00 seconds = 1248.94 MB/sec
 Timing buffered disk reads:  110 MB in  3.03 seconds =  36.29 MB/sec

---

### Post by FrzzMan on 2005-06-24
/dev/hda:
 Timing cached reads:   3924 MB in  2.00 seconds = 1961.32 MB/sec
 Timing buffered disk reads:    8 MB in  3.69 seconds =   2.17 MB/sec

OMFG... what's that???

Please... that result is after MultSec set to 16, before that the result is worse :(

---

### Post by FrzzMan on 2005-06-24
After tweak, it goes "super fast" - nearly 100% faster :cry:

frzzman@corsair:~$ sudo hdparm -m16 -W0 -c3 /dev/hda

/dev/hda:
 setting 32-bit IO_support flag to 3
 setting multcount to 16
 setting drive write-caching to 0 (off)
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
frzzman@corsair:~$ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing cached reads:   3944 MB in  2.00 seconds = 1970.33 MB/sec
 Timing buffered disk reads:   12 MB in  3.01 seconds =   3.99 MB/sec

---

### Post by picpak on 2005-06-24
[QUOTE=HungSquirrel]O_O  My drives are incredibly slow compared to yours.  Is this normal?

```
$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   792 MB in  2.01 seconds = 394.68 MB/sec
 Timing buffered disk reads:  100 MB in  3.00 seconds =  33.28 MB/sec
```[/QUOTE]

That's nothing...

```

 Timing cached reads:   376 MB in  2.02 seconds = 186.26 MB/sec
 Timing buffered disk reads:   48 MB in  3.02 seconds =  15.89 MB/sec

```

---

### Post by virgule on 2005-06-24
[QUOTE=picpak]That's nothing...

```

 Timing cached reads:   376 MB in  2.02 seconds = 186.26 MB/sec
 Timing buffered disk reads:   48 MB in  3.02 seconds =  15.89 MB/sec

```[/QUOTE]
 ```

/dev/hdc:
 Timing cached reads:   300 MB in  2.02 seconds = 148.61 MB/sec
 Timing buffered disk reads:   34 MB in  3.16 seconds =  10.74 MB/sec
# sudo hdparm -c /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
# sudo hdparm -c 3 /dev/hdc

/dev/hdc:
 setting 32-bit IO_support flag to 3
 IO_support   =  3 (32-bit w/sync)
# sudo hdparm -t -T /dev/hdc

/dev/hdc:
 Timing cached reads:   312 MB in  2.00 seconds = 155.87 MB/sec
 Timing buffered disk reads:   34 MB in  3.09 seconds =  11.00 MB/sec

```
hmm. can't expect much more from a 300Mhz Macintosh :)

---

### Post by FrzzMan on 2005-06-24
[QUOTE=virgule]```

/dev/hdc:
 Timing cached reads:   300 MB in  2.02 seconds = 148.61 MB/sec
 Timing buffered disk reads:   34 MB in  3.16 seconds =  10.74 MB/sec
# sudo hdparm -c /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
# sudo hdparm -c 3 /dev/hdc

/dev/hdc:
 setting 32-bit IO_support flag to 3
 IO_support   =  3 (32-bit w/sync)
# sudo hdparm -t -T /dev/hdc

/dev/hdc:
 Timing cached reads:   312 MB in  2.00 seconds = 155.87 MB/sec
 Timing buffered disk reads:   34 MB in  3.09 seconds =  11.00 MB/sec

```
hmm. can't expect much more from a 300Mhz Macintosh :)[/QUOTE]
 Mine is a decent box:

Opteron 1.8GHz CPU
1GB ECC Regged Mem
Tyan AMD 8xxx Mobo
Maxtor 7200rpm 8MB cache

The result:

Timing cached reads: 3944 MB in 2.00 seconds = 1970.33 MB/sec
Timing buffered disk reads: 12 MB in 3.01 seconds = 3.99 MB/sec

God know what happenned!!!

---

### Post by mikedfrwal on 2005-06-28
```
$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   2300 MB in  2.00 seconds = 1148.45 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.40 MB/sec
```
im already good so i dont think ill risk it

---

### Post by Skel on 2005-06-29
sudo hdparm -m <16 MaxMultSec value> /dev/hda when i enter this command i get No file to open.... So what did i do wrong my max is 16 so i inserted it were u it says "your" ](*,)

---

### Post by picpak on 2005-06-29
Put 1.

---

### Post by Skel on 2005-06-29
Oh i did it woot i wasnt supposed 2 put the Stuff in <> i feel stupid.... (sigh)

---

### Post by Skel on 2005-06-29
Set it to my max which is 16 really didnt change my speeds to much but i will leave it on ... Why not :P :)

---

### Post by traherom on 2005-06-29
[QUOTE=Mike Basinger]This had little effect on my laptop, but laptops are a different animal.

Mike[/QUOTE]Yep... not much difference here. Oh well, I had fun typing. :neutral:

---

### Post by GameGod on 2005-06-29
P4 2.53ghz
ASUS P4T533-C Motherboard
512MB PC-1066 RDRAM
120GB WD1200JB (120 gig + 8 meg cache)

Mult-sect off, 16-bit
 Timing cached reads:   2864 MB in  2.00 seconds = 1430.79 MB/sec
** Timing buffered disk reads:   90 MB in  3.04 seconds =  29.59 MB/sec**

Mult-sect on, 16-bit
 Timing cached reads:   2832 MB in  2.00 seconds = 1414.80 MB/sec
 Timing buffered disk reads:  126 MB in  3.03 seconds =  41.60 MB/sec

Mult-sect on, 32-bit
 Timing cached reads:   2876 MB in  2.00 seconds = 1436.06 MB/sec
** Timing buffered disk reads:  134 MB in  3.02 seconds =  44.36 MB/sec**

 :) Thanks!
(Nautilus seems a lot snappier, starts a lot quicker too)

---

### Post by rpaller on 2005-11-09
Sorry to resurrect this one, but I figured I would share my findings.

Toshiba Satellite A40 with a Toshiba MK6021 GAS Hard Drive (device manager)

```
## Test method: sudo hdparm -t -T /dev/hda
MaxMultSect: 16
MultSect: 16
IO_Support: 3 (32 bit)

/dev/hda:
 Timing cached reads:   1872 MB in  2.00 seconds = 935.21 MB/sec
 Timing buffered disk reads:   44 MB in  3.13 seconds =  14.06 MB/sec

Default settings yield these results:
MultSect: 0
IO_Support: 0 (16-bit)

/dev/hda:
 Timing cached reads:   1884 MB in  2.00 seconds = 941.67 MB/sec
 Timing buffered disk reads:   70 MB in  3.05 seconds =  22.97 MB/sec

```

---

### Post by Protoss on 2005-12-03
Ok I just installed Ubuntu 5.10 on a 8.4gig hard drive, because I was just going to see if 5.04 was bugging my CS Source server. So I installed it and noticed a pitiful slow boot time. And when I get into the system, it is still slow. It is a 1.4ghz P4 with 128megs of ram, so it should be good for just a server. I did hdparam -i /dev/hdc and it came out with 
>  Timing cached reads:   1588 MB in  2.00 seconds = 792.54 MB/sec
 Timing buffered disk reads:    2 MB in 44.91 seconds =  45.61 kB/sec

That is slow as hell...what could be causing this? could it be the hard drive? I did the speed boost, and the cahced reads went up by 300MB/sec, but no difference in the buffered disk reads.

---

### Post by dolson on 2005-12-05
$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2392 MB in  2.00 seconds = 1196.18 MB/sec
 Timing buffered disk reads:   12 MB in  3.21 seconds =   3.74 MB/sec



What the crap?! I don't remember ever having this issue on my AMD systems.. Weird.. This is a PIV system..

---

### Post by John.Michael.Kane on 2005-12-30
How do you make this permant i guess you would have to use the comand line part listed at the bottom of the config file. however im not to sure. any help or advice on editing hdparm thanks.

---

### Post by bored2k on 2006-01-03
[QUOTE=SD-Plissken]How do you make this permant i guess you would have to use the comand line part listed at the bottom of the config file. however im not to sure. any help or advice on editing hdparm thanks.[/QUOTE]

>    4.

      You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: sudo gedit /etc/hdparm.conf

Add the following to the end of your hdparm.conf
```

    *

         /dev/hdc {
         dma = on
         }
         
```

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by Omnios on 2006-01-03
Im not shure if I should try this on my Linux drive its 40 gig Maxtor that I got back in 2001. Anyways this is my info as im relunctant to try it as I would hava a hard time replacing the drive.

```
tom@main:~$ sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=MAXTOR 6L040J2, FwRev=A93.0500, SerialNo=662201539270
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=32256, SectSize=21298, ECCbytes=4
 BuffType=DualPortCache, BuffSize=1819kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78177792
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode

```

```
tom@main:~$ sudo hdparm -I /dev/hdb

/dev/hdb:

ATA device, with non-removable media
        Model Number:       MAXTOR 6L040J2
        Serial Number:      662201539270
        Firmware Revision:  A93.0500
Standards:
        Used: ATA/ATAPI-5 T13 1321D revision 1
        Supported: 5 4 3 2 & some of 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   78177792
        device size with M = 1024*1024:       38172 MBytes
        device size with M = 1000*1000:       40027 MBytes (40 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 4      Queue depth: 1
        Standby timer values: spec'd by Vendor, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
                SMART feature set
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    Automatic Acoustic Management feature set
                SET MAX security extension
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        20min for SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 1 determined by the jumper
Checksum: correct

```

```
tom@main:~$ sudo hdparm -t -T /dev/hdb

/dev/hdb:
 Timing cached reads:   2108 MB in  2.00 seconds = 1054.16 MB/sec
 Timing buffered disk reads:   64 MB in  3.11 seconds =  20.58 MB/sec

```

 I also have a fat32 partion on my main drive but dont feel a need to tweek it.

---

### Post by brummie on 2006-03-07
I went with what it said in the first post and the results were...

/dev/hdc:

 Model=Maxtor 4R080L0, FwRev=RAMC1TU0, SerialNo=********
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160086528
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode


/dev/hdc:
 Timing cached reads:   2148 MB in  2.00 seconds = 1072.02 MB/sec** (was 1066)**
 Timing buffered disk reads:  136 MB in  3.02 seconds =  45.10 MB/sec **(was 45.08 )**


The tweak actually boosted the drive by less than 1%, is this normal??
Its an Maxtor 80GB 5200rpm EIDE drive btw.

---

