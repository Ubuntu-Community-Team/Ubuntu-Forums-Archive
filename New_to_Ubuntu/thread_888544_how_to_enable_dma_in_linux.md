---
title: "how to enable dma in linux"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by usater on 2008-08-13
hai friends i've noticed heavy processor usage while copying big files

i think my dma is not on

how to enable it?

i've executed one command and got result as follows

*************************************************************

root@creations:# hdparm -d /dev/sda

/dev/sda:
 HDIO_GET_DMA failed: Inappropriate ioctl for device
root@creations:# 

*************************************************************

My hdd is segate  Model=ST3802110A (80gb)

my motherboard is genuine intel 865gsa chipset based one

please give me a remedy      :(

---

### Post by Dill on 2008-08-13
I believe if you type 

```
sudo hdparm -i /dev/sda
```

It should list some information about the drive, included the current active transfer mode. I believe the mode with the asterisk by it should be the one that's active, as the output indicates, like here:

```
dill@LAMP:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=TOSHIBA MK1032GSX                       , FwRev=AS022D  , SerialNo=           66OS6369T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=192426570
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

```

You might try running hdparm with the -i flag and see what active mode you're working in, just to make sure.

Cheers, 
Dylan

---

### Post by usater on 2008-08-13
This is my output



/dev/sda:

 Model=ST3802110A                              , FwRev=3.AAJ   , SerialNo=            5LR70N4S
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7


is this indicating that my dma is enabled...?

---

### Post by Dill on 2008-08-13
Yes, it looks as though your active mode is UDMA 5, so I don't think you've downgraded to PIO.

When you notice lags in copying big files, are you copying the files to an external drive or between directories? Do you notice any other slowness in general (i.e. navigating through directories, opening applications, etc.)?

---

### Post by usater on 2008-08-13
lag is when copying files b/w partitions

also i've seen my trancent 4gb usb work better( writing ) in windows than in linux.

there is no lag in browsing.... through folders

write speed by partitions are limited to 10-12mb/s

if my dma is enabled then why i'm getting an error message while quarrying abt dma?????


/dev/sda:
 HDIO_GET_DMA failed: Inappropriate ioctl for device

is my dma controller is not correctly detected?

---

