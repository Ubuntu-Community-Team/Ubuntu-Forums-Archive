---
title: "CD/DVD drive won't mount"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by CTolley on 2013-04-02
I've searched and searched, and I've tried everything I have found.  Nothing is working.  Possible busted unit, but I want to get the fine minds here direct input first.

My DVD drive isn't mounting.  At all.  When I try mounting, it tells me the location doesn't exist.  If a CD/DVD is inserted, it spins up and then stops.  Nothing pops on the screen.  I typed in some code or another, and it does see the drive.  My mounting efforts have just failed me.

Ubuntu 12.04
ASUS laptop

---

### Post by CTolley on 2013-04-02
I am now using Ubuntu 12.10.  I guess I screwed the pooch pretty good while trying to fix the DVD mount issue.  I rebooted, and could no longer mount my hdd.  All efforts through safe mode failed that as well.  I couldn't even mount it from the live disk.  All well, the upgrade went surprisingly smooth, and it seems that I didn't lose any data.  

I still can't mount CD/DVD drive.

---

### Post by CTolley on 2013-04-03
```
[COLOR="#FF0000"]ctolley@ctolley:~$ sudo mount /dev/sr0 /media/cdrom0[/COLOR]
[sudo] password for ctolley: 
mount: no medium found on /dev/sr0
[COLOR="#FF0000"]ctolley@ctolley:~$ dmesg | grep sr0[/COLOR]
[    0.888755] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    0.888844] sr 1:0:0:0: >Attached scsi CD-ROM sr0
ctolley@ctolley:~$ 
```

```
[COLOR="#FF0000"]ctolley@ctolley:~$ lshal | egrep cdrom[/COLOR]
  scsi.type = 'cdrom'  (string)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 1412  (0x584)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.drive_type = 'cdrom'  (string)
[COLOR="#FF0000"]ctolley@ctolley:~$ ls -l /dev/{cd,dvd}*[/COLOR]
lrwxrwxrwx 1 root root 3 Apr  2 22:36 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 Apr  2 22:36 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 Apr  2 22:36 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 Apr  2 22:36 /dev/dvdrw -> sr0
[COLOR="#FF0000"]ctolley@ctolley:~$ sudo hdparm -I /dev/sr0[/COLOR]

/dev/sr0:

ATAPI CD-ROM, with removable media
	Model Number:       Slimtype DVD A  DS8A3S                  
	Serial Number:      910290092906
	Firmware Revision:  HA28    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	PACKET command feature set
	   *	DEVICE_RESET command
	   *	Mandatory FLUSH_CACHE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation
ctolley@ctolley:~$ 

```

---

### Post by Doug S on 2013-04-03
To clarify, for us reading the posts: When you try to mount, there is a written CD or DVD already installed? Example (first with no DVD installed, seond with a DVD installed):```
doug@s15:~/c$ sudo mount /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0
doug@s15:~/c$ sudo mount /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
doug@s15:~/c$ ls -l /media/cdrom
total 4194304
-r--r--r-- 1 4294967295 4294967295 4294967296 Jan 22 15:15 big
```

---

### Post by CTolley on 2013-04-03
DVD was in for all of the info up top.  Just ran mount with and without disk.

```
ctolley@ctolley:~$ sudo mount /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0

```

---

### Post by Doug S on 2013-04-03
Does this:>  I couldn't even mount it from the live disk.mean that the drive worked when booting from a live CD? If yes, that would rule out a broken unit.

---

### Post by CTolley on 2013-04-03
No Sir.  Apologies for terminology.  I used a USB stick.  Stand by and I'll try an actual boot disk right quick.

---

### Post by CTolley on 2013-04-03
And negative on the boot.  BIOS recognizes it's there, so it must be a busted drive.

---

### Post by Doug S on 2013-04-03
Yes, at this point I am thinking busted unit also. Let us know how this turns out. (I realize, it might be days or even weeks.)

---

### Post by CTolley on 2013-04-03
It likely won't get replaced.  It quite working right a couple years ago, just yesterday I had a reason to use it.  I have other options though, and I likely won't need it again for years to come, at which point I'll have a new computer.  

I appreciate you taking the time to assist, even if it didn't work out in my favor.

---

