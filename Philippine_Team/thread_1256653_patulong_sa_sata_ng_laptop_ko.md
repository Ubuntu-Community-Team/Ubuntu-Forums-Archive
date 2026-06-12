---
title: "patulong sa sata ng laptop ko"
date: 2009-09-02
forum: Philippine Team
---

### Post by adonis827 on 2009-09-02
hindi kasi ako makapag post sa main ubuntu forum e

eto problem ko. sana may makatulong. kung ot pag pasensyahan na lang sana. 

paminsan minsan humihinto ang mga apps na ginagamit ko- firefox, terminal etc at magiging responsive na lang ulit kung umilaw na yung LED ng hard drive (after at least 30 seconds na freeze) kaya naisipan kong related ito sa sata nito.

sa tingin ko mabilis naman ang write speed etc ng hard drive ang problema lang minsan mabagal mag simulang mag respond. 


sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9729/255/63, sectors = 156301488, start = 0


sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2382 MB in  2.00 seconds = 1192.09 MB/sec
 Timing buffered disk reads:  108 MB in  3.05 seconds =  35.44 MB/sec



sudo hdparm -i /dev/sda 

/dev/sda:

 Model=ST98823A                                , FwRev=3.06    , SerialNo=            5PK1H7TB
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode




laptop ko ay asus a8j at naka jaunty na ito. salamat sa makakatulong

---

### Post by kiminaiseah on 2009-09-03
pa tingin ako ng dmesg report, forsure hindi yan sa hardisk mo,

---

### Post by adonis827 on 2009-09-04
thanks for the help sir

i found out nasa dvdrw ko ang problema. kung walang laman na cd paminsan minsan may delay. pero kung may nakasaksak na cd walang ganitong problem.

nag update na lang ako ng firmware at mukhang wala nang ganoong nangyayari


[http://forums.fedoraforum.org/archive/index.php/t-188596.html](http://forums.fedoraforum.org/archive/index.php/t-188596.html)
[http://club.cdfreaks.com/f36/acer-aspire-tsst-ts-l632d-cross-flashed-firmware-sc04-228563/](http://club.cdfreaks.com/f36/acer-aspire-tsst-ts-l632d-cross-flashed-firmware-sc04-228563/)

---

