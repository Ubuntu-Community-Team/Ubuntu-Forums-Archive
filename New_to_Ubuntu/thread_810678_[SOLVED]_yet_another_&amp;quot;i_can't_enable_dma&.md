---
title: "[SOLVED] yet another &amp;quot;i can't enable dma&amp;quot; thread"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-05-28
hi,
i tried everything from every thread in every forum i found on google regarding this problem..
my device name is /dev/hdb, a dvd-cd writer..

$ sudo hdparm /dev/hdb:
/dev/hdb:
IO_support = 0 (default)
16-bit)
unmaskirq = 0 (off)
using_dma = 0 (off)
keepsettings = 0 (off)
readonly = 0 (off)
readahead = 256 (on)
HDIO_GETGEO failed: Inappropriate ioctl for device

$ sudo hdparm -d1 /dev/hdb:
/dev/hdb:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off)

i added piix and ide-code to my /etc/modules at the very top before any other module is loaded..
the weird thing is, that dma worked for a couple of times without me doing anything at all, but it didn't work again after i rebooted..
i didn't do anything to it! i swear!
what is happening to my computer? someone help me please, it just took me an hour to write a dvd :'(

---

### Post by paranoid_humanoid on 2008-05-30
hrere's my /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


piix
lp
fuse
ide-core
mousedev
psmouse
nvidia
ide-generic
ide-cd
ide-disk



# Added for Nero Linux device access
sg

---

someone please help me, i really need to burn stuff frequently :(

---

### Post by kerry_s on 2008-05-30
perhaps you didn't setup the burner right. did you check the speed setting?
might be the media type your using, some of the cheaper disks have a speed of like 4x, it should say on the disk, looks like: 4x 700mb 80min

as far as i know hdparm is not used anymore, as the new kernels work differently.
what ubuntu are you using?

---

### Post by paranoid_humanoid on 2008-05-30
the same dvd brand i've been using all the time, on windows and everywhere..
i'm sure that dma isn't enabled on for my device, whenever i start nero linux it warns me that it's not enabled. plus it's not just slow writing speed, my pc almost freezes up during the whole process...
doesn't anyone else face that problem!!
i have one ide slot on my board. my SONY DVD-CD RW is connected to it through a cable with three ends (it can support another device but i don't have any). my hard drive is on SATA and i have no problems with it.

amr@amr-ubuntu:~$ sudo hdparm -iI /dev/hdb
[sudo] password for amr: 

/dev/hdb:

 Model=SONY DVD RW DRU-810A, FwRev=1.0d, SerialNo=817062016810A00E0512
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode


ATAPI CD-ROM, with removable media
	Model Number:       SONY    DVD RW DRU-810A                 
	Serial Number:      817062016810A00E0512
	Firmware Revision:  1.0d    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
	CBLID- above Vih
	Device num = 1

---

### Post by kerry_s on 2008-05-30
okay that says your device is using *udma2, check in your /var/log/dmesg for errors. if you don't know what udma is:
[http://ourworld.compuserve.com/homepages/john_scott/](http://ourworld.compuserve.com/homepages/john_scott/)

you should see something like this(mine):
```

 hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)

```

if your not sure just post the whole thing and i'll have a look.

---

### Post by paranoid_humanoid on 2008-05-31
okay, i got it.
i had a sata hard drive, and the sata module had to be loaded first before the IDE one. i don't know why, it's really silly, but i think it's finally working now..
i've added that tip to the help wiki:
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

