---
title: "Extra Poor SATA performances"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by paoletto on 2008-04-30
Hardware:

Via KT600 based motherboard (a7v600)
Wester Digital SATA hard drive 

Software: 

Ubuntu Hardy (before it was gutsy, but it was the same)
Kernel 2.6.24 from ubunty gutsy 
or
Kernel 2.6.24.4 self compiled
(same behaviour and results)


What happens:

The machine shows the signs of PIO mode on the old IDE drives.

What i mean? well, hdparm -tT shows good values, but effective operations
on the drive raise the cpu load (on top, under the voice "wait") and i can achieve performances like 5mb/sec with the machine almost frozen


Examples: 

# time cat /local/movies/Cult/Il\ nome\ della\ Rosa.avi >/dev/null

real    2m41.562s
user    0m0.040s
sys     0m3.750s

# ls -la /local/movies/Cult/Il\ nome\ della\ Rosa.avi
-rw-r--r-- 1 root root 856510464 2008-01-03 14:32 /local/movies/Cult/Il nome della Rosa.avi

(it means roughly 5Mb/sec)

in the meanwhile, "top" says:
Cpu(s):  0.3%us,  2.3%sy,  0.0%ni,  0.0%id, 97.4%wa,  0.0%hi,  0.0%si,  0.0%st


BUT:

# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   440 MB in  2.00 seconds = 220.02 MB/sec
 Timing buffered disk reads:  188 MB in  3.03 seconds =  62.14 MB/sec

so here the drive seems fast, AND dmesg says:

Apr 28 20:36:55 rivendell kernel: [   32.111204] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 28 20:36:55 rivendell kernel: [   32.111363] VP_IDE: IDE controller (0x1106:0x0571 rev 0x06) at  PCI slot 0000:00:0f.1
Apr 28 20:36:55 rivendell kernel: [   32.111415] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
Apr 28 20:36:55 rivendell kernel: [   32.111436] VP_IDE: not 100% native mode: will probe irqs later
Apr 28 20:36:55 rivendell kernel: [   32.111455] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Apr 28 20:36:55 rivendell kernel: [   32.111468]     ide0: BM-DMA at 0x7800-0x7807, BIOS settings: hda:pio, hdb:pio
Apr 28 20:36:55 rivendell kernel: [   32.111492]     ide1: BM-DMA at 0x7808-0x780f, BIOS settings: hdc:DMA, hdd:pio
Apr 28 20:36:55 rivendell kernel: [   33.336051] hdd: IRQ probe failed (0xfffffcfe)
Apr 28 20:36:55 rivendell kernel: [   33.655836] hdd: IRQ probe failed (0xfffffcfe)
Apr 28 20:36:55 rivendell kernel: [   34.635133] hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
Apr 28 20:36:55 rivendell kernel: [   34.635355] hdc: UDMA/33 mode selected
Apr 28 20:36:55 rivendell kernel: [   34.635535] ide1 at 0x170-0x177,0x376 on irq 15
Apr 28 20:36:55 rivendell kernel: [   35.245742] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Apr 28 20:36:55 rivendell kernel: [   35.245755] Uniform CD-ROM driver Revision: 3.20
Apr 28 20:36:55 rivendell kernel: [   35.248585] Driver 'sd' needs updating - please use bus_type methods
Apr 28 20:36:55 rivendell kernel: [   35.248668] Driver 'sr' needs updating - please use bus_type methods
Apr 28 20:36:55 rivendell kernel: [   35.249131] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
Apr 28 20:36:55 rivendell kernel: [   35.249203] sata_via 0000:00:0f.0: routed to hard irq line 0
Apr 28 20:36:55 rivendell kernel: [   35.249449] scsi0 : sata_via
Apr 28 20:36:55 rivendell kernel: [   35.249597] scsi1 : sata_via
Apr 28 20:36:55 rivendell kernel: [   35.252255] ata1: SATA max UDMA/133 cmd 0x9800 ctl 0x9400 bmdma 0x8400 irq 16
Apr 28 20:36:55 rivendell kernel: [   35.252263] ata2: SATA max UDMA/133 cmd 0x9000 ctl 0x8800 bmdma 0x8408 irq 16
Apr 28 20:36:55 rivendell kernel: [   35.454498] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 28 20:36:55 rivendell kernel: [   35.674349] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 28 20:36:55 rivendell kernel: [   35.880105] ata2.00: ATA-7: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
Apr 28 20:36:55 rivendell kernel: [   35.880113] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 28 20:36:55 rivendell kernel: [   35.914627] ata2.00: configured for UDMA/133
Apr 28 20:36:55 rivendell kernel: [   35.914830] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
Apr 28 20:36:55 rivendell kernel: [   35.915133] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Apr 28 20:36:55 rivendell kernel: [   35.915164] sd 1:0:0:0: [sda] Write Protect is off
Apr 28 20:36:55 rivendell kernel: [   35.915211] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 20:36:55 rivendell kernel: [   35.915319] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Apr 28 20:36:55 rivendell kernel: [   35.915344] sd 1:0:0:0: [sda] Write Protect is off
Apr 28 20:36:55 rivendell kernel: [   35.915388] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 20:36:55 rivendell kernel: [   35.915397]  sda: sda1 sda2 sda3
Apr 28 20:36:55 rivendell kernel: [   35.940362] sd 1:0:0:0: [sda] Attached SCSI disk
Apr 28 20:36:55 rivendell kernel: [   35.940553] sd 1:0:0:0: Attached scsi generic sg0 type 0


At the moment i'm trying to recompile the kernel with everything SATA or PATA or SCSI related as module, so i can see exactly which driver is getting used.

Anyways, any hint?

---

### Post by paoletto on 2008-04-30
to make a comparison:

Notebook sony vaio C1S (core2duo platform)
Ubuntu Gutsy
Kernel 2.6.20 self compiled



$ time cat /wind/movies/tFotR.mkv >/dev/null

real    1m41.843s
user    0m0.050s
sys     0m2.610s
$ ll /wind/movies/tFotR.mkv
-rwxrwx--- 1 root plugdev 2428746844 2008-02-17 13:23 /wind/movies/tFotR.mkv


and it means roughly 24Mb/sec

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1620 MB in  2.00 seconds = 810.39 MB/sec
 Timing buffered disk reads:  126 MB in  3.03 seconds =  41.54 MB/sec


(and it's a notebook hard drive!)

---

### Post by Shazaam on 2008-04-30
My WD 320gig drive has a jumper for 150 and 300mbs. Make sure your motherboard supports the faster SATA speed and check the jumper on the drive.
Here is the Western Digital support forum....
[http://websupport.wdc.com/forum/](http://websupport.wdc.com/forum/)

---

### Post by herbster on 2008-04-30
Have you checked your BIOS settings for tweaks on the SATA ports?

---

### Post by cubeist on 2008-04-30
> **Shazaam said:**
> My WD 320gig drive has a jumper for 150 and 300mbs. Make sure your motherboard supports the faster SATA speed and check the jumper on the drive.
Here is the Western Digital support forum....
[http://websupport.wdc.com/forum/](http://websupport.wdc.com/forum/)

Really?  I could not find any article on WD on how to change SATA speeds via jumpers, and my WD does not have this feature.  As far as I know, it is the MB that determines SATA I or II...

---

### Post by paoletto on 2008-04-30
Actually my mobo supports only SATA150, so i closed the jumper on the drive to enable SATA150 (not 300)

Also i enabled spread spectrum modulated option because i had issues without.

Actually i forgot to mention that in the beginning of January, just after i installed gutsy on the machine, performances were great!

Then i think after some gutsy update, it started to suck.
So i would exclude some drive related issue..

And, if you had a careful look at my tests, you will notice that the problem is not the speed of the drive, but the lack of DMA...

---

### Post by cubeist on 2008-04-30
> **paoletto said:**
> Actually my mobo supports only SATA150, so i closed the jumper on the drive to enable SATA150 (not 300)

Also i enabled spread spectrum modulated option because i had issues without.

Actually i forgot to mention that in the beginning of January, just after i installed gutsy on the machine, performances were great!

Then i think after some gutsy update, it started to suck.
So i would exclude some drive related issue..

And, if you had a careful look at my tests, you will notice that the problem is not the speed of the drive, but the lack of DMA...

if you type sudo hdparm -I /dev/sda it should tell you whether dma is on or off...

Also, here is another forum post worth reading through...It may be that your speeds are actually average for a sata I drive... Remember. hdparm -tT test the maximum throughput... not average.

[http://ubuntuforums.org/showthread.php?t=750206&highlight=slow+hard+drive+hardy&page=2](http://ubuntuforums.org/showthread.php?t=750206&highlight=slow+hard+drive+hardy&page=2)

---

### Post by cubeist on 2008-04-30
Actually, looking back through your posts, I think your speeds are just about correct... maybe a bit slow, but I am still not sure why your cpu is being maxed out... if you run system monitor in the background and sort by cpu load, can you see which process is hogging the cpu?

---

### Post by paoletto on 2008-04-30
According with hdparm -I (but also with dmesg, which output i posted before) i have dma enabled, but the point is that when i use the disk, all the cpu goes for IO operations (wait). Which should not happen with DMA.
And of coruse i see which process is, which means cat for instance, but 
it's not normal operations, but just wait. It means that cat just take few cpu % because it is getting shrinked by all the IO.

Same happens with unrar, for examples. It takes ages now because IO takes all the cpu, and it just cant do the processing.


About your opinion about SATA1, dude, honestly i think that 5Mb/s is damn slow even for my quantum fireball 1gb..

7 years ago the same cat test showed a performance of about 30mb/s on an IBM 30Gb drive connected in UDMA66.

How can be that a SATA 150 3.5" drive (it actually is a 300 but the controller is only 150) results in a throughput of 5Mb/s when even a notebook 2.5" drive beat it with a 5x performance (25Mb/s)?

Moreover, as i said before, this drive on the same machine performed very well (didnt test at that time) with a january 2008 ubuntu gutsy.

After some upgrade around february it started to suck.

Anyways, let me clarify that this "cat" test cant be like that (5Mb/s) for any modern hard drive. All drives >3gb i had performs better.

And hdparm -tT confirms it.



# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
  Model Number:       WDC WD10EACS-00ZJB0
  Serial Number:      WD-WCASJ0052263
  Firmware Revision:  01.01B01
Standards:
  Supported: 7 6 5 4
  Likely used: 8
Configuration:
  Logical       max    current
  cylinders  16383     16383
  heads      16 16
  sectors/track 63     63
  --
  CHS current addressable sectors:   16514064
  LBA    user addressable sectors:  268435455
  LBA48  user addressable sectors: 1953525168
  device size with M = 1024*1024:      953869 MBytes
  device size with M = 1000*1000:     1000204 MBytes (1000 GB)
Capabilities:
  LBA, IORDY(can be disabled)
  Queue depth: 32
  Standby timer values: spec'd by Standard, with device specific minimum
  R/W multiple sector transfer: Max = 16  Current = 16
  Recommended acoustic management value: 128, current value: 254
  DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
       Cycle time: min=120ns recommended=120ns
  PIO: pio0 pio1 pio2 pio3 pio4
       Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
  Enabled    Supported:
     *  SMART feature set
        Security Mode feature set
     *  Power Management feature set
     *  Write cache
     *  Look-ahead
     *  Host Protected Area feature set
     *  WRITE_BUFFER command
     *  READ_BUFFER command
     *  NOP cmd
     *  DOWNLOAD_MICROCODE
        Power-Up In Standby feature set
     *  SET_FEATURES required to spinup after power up
        SET_MAX security extension
        Automatic Acoustic Management feature set
     *  48-bit Address feature set
     *  Device Configuration Overlay feature set
     *  Mandatory FLUSH_CACHE
     *  FLUSH_CACHE_EXT
     *  SMART error logging
     *  SMART self-test
     *  General Purpose Logging feature set
     *  64-bit World wide name
     *  Segmented DOWNLOAD_MICROCODE
     *  SATA-I signaling speed (1.5Gb/s)
     *  Native Command Queueing (NCQ)
     *  Host-initiated interface power management
     *  Phy event counters
        DMA Setup Auto-Activate optimization
     *  Software settings preservation
     *  SMART Command Transport (SCT) feature set
     *  SCT Long Sector Access (AC1)
     *  SCT LBA Segment Access (AC2)
     *  SCT Error Recovery Control (AC3)
     *  SCT Features Control (AC4)
     *  SCT Data Tables (AC5)
        unknown 206[12] (vendor specific)
        unknown 206[13] (vendor specific)
Security:
  Master password revision code = 65534
        supported
  not   enabled
  not   locked
  not   frozen
  not   expired: security count
  not   supported: enhanced erase
  260min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee275f20
  NAA        : 5
  IEEE OUI   : 14ee
  Unique ID  : 2750f20
Checksum: correct

---

### Post by cubeist on 2008-04-30
Well if you read through the linked post, one user mentions that it depends on what you are trying to copy... 100 individual mp3's will take much longer than a 100mb file...Anyway, thats not really the point.  I agree... I take back what I said in my previous post... your speeds *are* slow for continuous drive transfer and it should not be consuming all your IO.  Unfortunately I don't know the best way to fix it... The reason I posted to your problem at all was I had an identical thing happen on a upgrade of fiesty...I tried to live with the problem, which was impossible and eventually did a clean install which fixed it.

Edit - 
Just looking through your hdparm -I ... where is your transport category?!

Here is mine... fourth line down...
Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5

I have no clue if this is related...but have not seen that omitted before.

---

### Post by cubeist on 2008-04-30
Also, you mentioned in an earlier post that you were thinking of recompiling your kernel.  A simple way to check that your current kernel has sata modules is to type in a terminal
```
locate sata
```
this should show about 13 or so modules for sata vendors (chipsets) in your kernel

---

### Post by lemming465 on 2008-04-30
> Cpu(s): 0.3%us, 2.3%sy, 0.0%ni, 0.0%id, 97.4%wa, 0.0%hi, 0.0%si, 0.0%st

97.4% I/O wait means the CPU isn't doing anything interesting except waiting for the next disk I/O completion interrupt.

---

### Post by paoletto on 2008-05-01
@cubeist:

might lack of "transport" mean that my system is using the wrong driver
(ATA SATA support instead of libata)?

actually i dont think so because dmesg talks about sata_via which should be libata, but.. i dont know..

---

### Post by paoletto on 2008-05-01
@cubeist

Now i recompiled the kernel with ata support as modules and i get:

# lsmod | grep via
snd_via82xx            28696  0
gameport               15048  1 snd_via82xx
snd_via82xx_modem      15368  0
snd_ac97_codec         99620  2 snd_via82xx,snd_via82xx_modem
snd_mpu401_uart         9088  1 snd_via82xx
snd_pcm                80004  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd                    54020  12 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10824  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro              9172  0
i2c_core               24320  1 i2c_viapro
via82cxxx               8772  0 [permanent]
ide_core              119392  1 via82cxxx
via_agp                10688  1
agpgart                34184  1 via_agp
pata_via               12420  0
sata_via               12036  3
libata                158768  4 pata_via,pata_acpi,sata_via,ata_generic


im wondering what changed to you when you reinstalled ubuntu..

---

### Post by paoletto on 2008-05-04
I actually got some answers from libata developers, which says that the ata layer is just working fine and has DMA correctly enabled.

They say that the problem has to reside on an higher layer, so they suggested to ask ubuntu engineers to understand how do they deal with the filesystem.
If they use lvm or something else..

I actually dont have a clue about something which may take so much cpu power and which place between the kernel filesystem layer and the application..

does someone have a clue?

---

### Post by paoletto on 2008-05-06
Is it possible that no ubuntu engineer ever answer to our threads?

---

