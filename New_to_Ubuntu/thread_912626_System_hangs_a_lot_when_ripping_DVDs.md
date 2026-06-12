---
title: "System hangs a lot when ripping DVDs"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by klemperal on 2008-09-06
I'm not really sure why, but my system hangs, runs slow, and is unresponsive when I'm ripping DVDs.  I have plenty of space on my drive and 2 gigs of ram so I don't think thats the issue--especially since it doesn't happen on my XP partition.  Any ideas on how I could speed things up or what the problem could be?

---

### Post by cwsnyder on 2008-09-06
I have an idea as to what the problem could be, but not how to fix it: My guess is the DVD ripping software under Linux does not work as well as the Windows ripper.

---

### Post by klemperal on 2008-09-06
I thought it might have been an issue with the windows ripper I was running under wine so I used a Linux ripper and I still have the same problem.

---

### Post by mc4man on 2008-09-06
What are you using to rip?
Ripping isn't very cpu or ram intensive (or hdd 

Can you describe your hardware setup (hdd('s), dvd drives('s) and how they're connected.

For instance i was testing a little script to autorip from multiple drives simultaneously and there was no loss of functionality when ripping from 2 drives at the same time. (older p4, 1 gig ram

---

### Post by klemperal on 2008-09-06
I used a lot of different programs to determine that I don't think it's an issue with the programs (Ripit4Me, DVdFab, Vobcopy and K9copy).  My hardware set up is 1 SATA HD, 1 cd/dvd-rw (IDE) and 1 DVD-ram drive (IDE).

---

### Post by mc4man on 2008-09-07
that's similar to me (2 sata hdd's, but that's irrelevant for this use).

Is there any difference between when ripping from one dvd drive or the other?

Are the dvd drives on separate controllers (ide cable) or the same one?

If you have a lot of open applications at once (not referring to ripping) do you notice any performance issues other than maybe application open time?

What's an average time for typical dvd9 rip?

---

### Post by klemperal on 2008-09-07
I'm pretty sure they are on separate controllers.  I'm gonna check my other drive's ripping speed but since it's older it doesn't read or rip as fast--I'm still gonna check though.  As far as application performance firefox runs pretty slow when ripping--sometimes it hangs and darkens up, there is lag when switching tabs or even when typing sometimes.  I would say that the average rip time for a DVD9 would be about 15+minutes in linux.

---

### Post by klemperal on 2008-09-07
Ok, my other drive isn't ripping as fast but everything else seems to be a lot more stable.  I'm assuming that there is some issue with Linux and my other DVD-Ram drive.  Any idea on how to fix this?  I'm still pretty new to Linux so please bear with me.

---

### Post by mc4man on 2008-09-07
sorry i was trying to see what would choke the system while ripping and it was a lot.
Vobcopy ripping from both drives, 4 firefoxes running on each cube side, vlc playing a movie from hdd, system monitor running, and me typing a text didn't faze that much.
When I had one firefox open 32 tabs at once things did choke up quite a bit. 

Anyway while I'm not sure this is an issue run this on your drives (I'm assuming dvd drives are scd0 and scd1 (if your not sure of device node run sudo lshw -C disk and you'll see a /dev/scdx for each *cdrom listing

```
sudo hdparm -i /dev/scd0 
```and the same for ....../dev/scd1 and also /dev/sda (hdd I'll presume

Did you ck. your ide controller setup?

Edit: actually post the lshw for info's sake

---

### Post by klemperal on 2008-09-07
Alright I'm back on.  It got late last night and I went to sleep.  Anyway, here is the ishw and the other commands.  Let me know what you think.  And as for the IDE the ATAPI is set as master and the Compaq is set as slave.  

 sudo lshw -C disk
  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8160B
       vendor: COMPAQ
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0012
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: SAMSUNG HD403LJ
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda
       version: CT10
       serial: S0NFJ1KP103770
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=19bf19be
--------------------------------------------------------------------------
/dev/sda:

 Model=SAMSUNG HD403LJ                         , FwRev=CT100-10, SerialNo=S0NFJ1KP103770      
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=781422768
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode
--------------------------------------------------------------------------
/dev/scd0:

 Model=ATAPI   DVD A  DH20A4P                  , FwRev=9P59    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
--------------------------------------------------------------------------
/dev/scd1:

 Model=COMPAQ  DVD-ROM GDR8160B                , FwRev=0012    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 
 AdvancedPM=no

 * signifies the current active mode

---

### Post by mc4man on 2008-09-07
Run this
```
grep 'DMA' /var/log/kern.log
```

You'll probably get a line about 80 wire
it can be ignored if you have an 80 wire ide cable
If your using a 40 wire then you should get an 80 wire ide cable and replace

If replacing also take opportunity to ck. jumper setting on the drive. The drive on the end connector should be jumpered to master.
The one on the middle should be jumpered to slave

You can tell an 80 wire from a 40 wire by looking at. The 80 wire is almost smooth, on the 40 wire you can clearly see the wires.

Does your mobo have a 2nd ide controller interface? If so it's much better to have each dvd drive as master (end connector) on a separate ide cable

edit; while I don't have any here if the ide cable is split into sections then iirc it's a cable select type. In that case it's better to either replace with an 80 wire or have jumpers on both drives set to cs (cable select

---

### Post by Shampyon on 2008-12-13
I'm having RAM problems with DVD backup as well, but I don't think it's the same thing. I figured it's probably best to post in here than create an all-new thread.

Despite having always worked before, k9copy refused to start backing up one of my discs today. I used k3b to rip an ISO to my hard drive, then opened the ISO with k9copy. It made no difference - k9copy still refuses to start encoding it, and it's taking up almost all of my 3GB of RAM. I tried using DVD:RIP and DVD95, and the exact same thing happens. Whether I try backing up from the disc or ISO, no matter what app I use, it takes up almost all of my RAM. Half the time the app crashes after freezing my system for a few minutes.

---

### Post by Shampyon on 2008-12-14
After posting the above message I started to have a suspicion of what might be stopping k9Copy and the other DVD apps from backing up the disc (The Dark Knight), so I took it over to my brother and ran it through his DVDFab app. Suspicion confirmed: It was a form of copy protection Linux hasn't caught up to yet. I don't know why that caused it to chew up RAM the way it did, but the de-DRM'd files are running perfectly through all the DVD apps, so that has to be it.

Seeing as most commercial apps can crack it, and those apps are legal in just about every country on the planet, it's as though copy protection only exists to prop up the ripping software industry. Wierd.

---

