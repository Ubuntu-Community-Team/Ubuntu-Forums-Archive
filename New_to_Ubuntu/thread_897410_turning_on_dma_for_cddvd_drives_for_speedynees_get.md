---
title: "turning on dma for cd/dvd drives for speedynees gets error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-22
i have found this article on the net

[http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/](http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/)

have tried to do  a 

 sudo hdparm /dev/scd0


on my dvd writer and i get this

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

and my /ect/fstab says that my dvd is at /dev/scd0

any ideas why im getting this error?

---

### Post by mc4man on 2008-08-22
At this point (using sdx, scdx) hdparm is of very little value except for reporting some info.
sudo hdparm -i /dev/scd[COLOR="Red"]0[/COLOR]  will show you the drive capabilities and what it is set at. (as far as dma

---

### Post by stinger30au on 2008-08-22
ok did that and i get this


/dev/scd0:

 Model=PIONEER DVD-RW  DVR-111D                , FwRev=1.23    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode






is this good or bad??? i woudl assume bad as PIO mode has no * next to it and dma has no * next to it

only UDMA has a * next to udma4

any ideas?
thanks

---

### Post by stinger30au on 2008-08-23
*bump*

---

### Post by unutbu on 2008-08-23
From [http://en.kioskea.net/pc/ide-ata.php3:](http://en.kioskea.net/pc/ide-ata.php3:)

```
PIO Mode   		Throughput (Mb/s)
Mode 0 	   		3.3
Mode 1 	   		5.2
Mode 2 	   		8.3                 ATA-1
Mode 3 	   		11.1
Mode 4 	   		16.7         

DMA Mode  	 	Throughput (Mb/s)
0 (Single word)  	2.1
1 (Single word)  	4.2
2 (Single word)  	8.3
0 (Multi-word) 	 	4.2
1 (Multi-word) 	 	13.3
2 (Multi-word) 	 	16.7                ATA-2, ATA-3

Ultra DMA Mode		Throughput (Mb/s)
UDMA 0			16.7
UDMA 1			25.0    
UDMA 2 (Ultra-ATA/33)	33.3                ATA-4
UDMA 3	                44.4
UDMA 4 (Ultra-ATA/66)	66.7                ATA-5
UDMA 5 (Ultra-ATA/100)	100                 ATA-6
UDMA 6 (Ultra-ATA/133)	133                 ATA-7

```
Having your DVD-RW drive in UDMA4 mode is better than any PIO and DMA mode.
It looks to me like your DVD-RW drive is operating at top speed.

---

