---
title: "blank DVD's not recognized"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Craigupdegrove on 2008-05-01
I can't get my blank DVD's to mount, so i can write to them. I can use dvd'salready written to. I can also watch movies I am at a loss. please help me

---

### Post by cubeist on 2008-05-01
> **Craigupdegrove said:**
> I can't get my blank DVD's to mount, so i can write to them. I can use dvd'salready written to. I can also watch movies I am at a loss. please help me

What if you try a program like brasero... or another dvd writing application... do you see the dvd there?

---

### Post by warbread on 2008-05-01
Blank media isn't supposed to mount.  Do you mean that it doesn't show up at all?  Also, what version of Ubuntu are you using?

---

### Post by Craigupdegrove on 2008-05-02
Answer ro both the replies brasero doesn't see the DVD because it just sits in the drive and seeks and then says no media inserted I am using hardy heron 8.04

---

### Post by aeiah on 2008-05-02
did this work in previous versions of ubuntu? i know i always had problems with my girlfriends pc because the dvd drive couldnt understand dvd+r, only dvd-r

---

### Post by Craigupdegrove on 2008-05-02
This is the first version of Ubuntu I used, never tried DVD-R

---

### Post by Craigupdegrove on 2008-05-02
It is in my laptop it works with DVD+R in Vista

---

### Post by drumour on 2008-05-03
Same problem, 2 similar pc's both running 8.04 patched up to date. When I insert a blank dvd or cd nothing happens. If I try and burn using Brasero for e.g. it reports "no disc" in drive. 
fstab gives following for cd/dvd:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

other commands tried and their results:

1)  with blank dvd in drive: sudo mount /dev/scd0 /media/cdrom0
mount: No medium found

2)  with blank dvd in drive: sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: DVD+-RW ND-3570A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 104B
       serial: [Optiarc DVD+-RW ND-3570A104B06031000
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

3)  with blank dvd in drive:/usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:			DVD+-RW ND-3570A
  device:		/dev/scd0
  door:			open
  type:			CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		FALSE
  max read speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  write speeds:		8467 KiB/s (CD 56.4x, DVD 6.2x)
			7056 KiB/s (CD 47.0x, DVD 5.2x)
			5645 KiB/s (CD 37.6x, DVD 4.1x)
			4234 KiB/s (CD 28.2x, DVD 3.1x)
			2822 KiB/s (CD 18.8x, DVD 2.0x)
			1411 KiB/s (CD 9.4x, DVD 1.0x)
			
Media:
  label:		''
  type:			Couldn't open media
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			Could not be determined

---

### Post by JohnnyC44 on 2008-05-03
I have the same problem in Gutsy, and was hoping it would be fixed in Hardy.  No problems with CDs, but DVDs of any flavor aren't recognized.  Here's the tread: [http://ubuntuforums.org/showthread.php?t=635433]("http://ubuntuforums.org/showthread.php?t=635433")

---

### Post by halitech on 2008-05-03
I had a dvd burner act about the same a year ago, would read anything tossed at it but wouldn't burn anything. turned out the drive was dying after a year. replaced it and everything was fine after that.

---

### Post by billgoldberg on 2008-05-03
I had a similar problem a few months ago with gutsy.

It was a hardware issue.

But on topic:

try using another burner like **k3b**. It *might* do the trick.

---

### Post by drumour on 2008-05-03
JohnnyC44: Thanks for link to other thread, seems the same problem, maybe a mod could merge threads? 

Have appended to Bug #220957 in linux (Ubuntu) on launchpad.

billgoldberg: K3b did'nt work, at least its another bit of confirmation it gives:no medium present

---

### Post by JohnnyC44 on 2008-05-05
So if this is a hardware issue, how can I test it within Ubuntu since I don't have dual boot capability with Windows?  I'm using a Dell E1505n laptop preloaded with Ubuntu.  Hardware is warranted, but there is no software support.  I know how these things work: if I call Dell and tell them that the smart money is betting that I have a hardware problem, they'll just tell me that it's a software problem and to deal with it myself.  Obviously their Windows diagnostic tools will not work on my box.  Thanks in advance!  John

---

### Post by arch stanton on 2008-05-05
having the same problem (i guess..)  can't burn dvd's , can burn cd 's though data and audio.. 
also can not  format dvd rw 
likely culprit is dvd being detected as /dev/scd0 (ssci) instead of /dev/hdd as before .. stumped so far .. will continue googling


Maybe I need to ln /dev/scd0 to /media/cdrom or something??


here are some errors for y'all

arch@arch-01:~$ cdrecord dev=/dev/cdrom blank=fast
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
arch@arch-01:~$ sudo cdrecord dev=/dev/cdrom blank=fast
[sudo] password for arch: 
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

arch@arch-01:~$ sudo cdrecord dev=/dev/scd0 blank=fast
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... giving up.
WARNING: /dev/scd0 seems to be mounted!
wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

arch@arch-01:~$ umount /dev/scd0
arch@arch-01:~$ sudo cdrecord dev=/dev/scd0 blank=fast
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 420n '
Revision       : '1.33'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Speed set to 5645 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.

arch@arch-01:~$ sudo wodim blank=all
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 420n '
Revision       : '1.33'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Speed set to 5645 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
wodim: Cannot blank disk, aborting.
arch@arch-01:~$

---

### Post by JohnnyC44 on 2008-05-20
Well, this issue has now been resolved for me after posting to the Dell Linux forums, and it was a d'oh moment!!!

PhillyFloyd over at Dell had me type this command in a terminal window:

**sudo cdrecord -scanbus**

The relevant output for this purpose is:

[I]scsibus1:
        1,0,0   100) 'SONY    ' 'CDRWDVD CRX880A ' 'KD09' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *[/I]

My optical drive is a CD-RW/DVD -- NOT a burner as I had assumed!
My apologies for wasting anyone's time here.  And thanks again for all the support you've given me over the past year.

---

### Post by Xoanan on 2008-05-22
CDRW?  I was told in another thread that there wasn't much difference between a CD ReWriter and a burner.  Anyone know the difference?  I'm still a little new at this

---

### Post by JohnnyC44 on 2008-05-30
Sorry about my hasty/sloppy writing.  Reads and writes (burns) CDs fine.  Reads, but does not write (burn) DVDs.

---

