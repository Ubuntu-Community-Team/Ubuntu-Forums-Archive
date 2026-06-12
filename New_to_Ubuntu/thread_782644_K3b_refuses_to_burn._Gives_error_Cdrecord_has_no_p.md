---
title: "K3b refuses to burn. Gives error: Cdrecord has no permission to open device"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by applegrew on 2008-05-05
I am using **Kubuntu** since its Feisty version. I am currently using **Gutsy**. K3b was working great all this period but after the last system upgrade (on 2-April-2008 I guess), my K3b is refusing to burn the iso (of kubunut-hardy alternate CD). I get the error: **Cdrecord has no permission to open device**, just after after *Starting Disc write* message is shown.

I have an **internal dvd writer drive (PIONEER DVDRW DVR-K16, system device name: _/dev/scd0_)**. I have gone through many many threads in this forum and over the internet in general but nothing works. Below I am posting some of the messages to help you to help me.

Also note that **my user is member of cdrom group**.

*cdrecord -version* output:-
```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 Jörg Schilling
```

*wodim -version* output:-
```
Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd
Wodim 1.1.6
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling
```

*mkisofs -version* output:-
```
mkisofs 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2007 Jörg Schilling
```

*uname -a* output:-
```
Linux APPLEGREW 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
```

*ls -l /dev/scd0* output:-
```
brw-rw---- 1 root cdrom 11, 0 2008-05-05 18:25 /dev/scd0
```

*ls -l ls -l /usr/bin/wodim* output:-
```
-rwxr-xr-x 1 root root 359116 2007-09-17 03:47 /usr/bin/wodim
```

K3b debug log:-
```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PIONEER DVDRW   DVR-K16 1.15 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVDRW   DVR-K16 '
Revision       : '1.15'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0002 (Removable disk) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 3528 KB/s
Track 01: data   697 MB        
Total size:      801 MB (79:22.14) = 357161 sectors
Lout start:      801 MB (79:24/11) = 357161 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2688
Starting to write CD/DVD at speed  20.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  697 MB written.
Track 01:    1 of  697 MB written (fifo 100%) [buf  99%]   0.4x.
Track 01:    2 of  697 MB written (fifo 100%) [buf  99%]  10.3x.
Track 01:    3 of  697 MB written (fifo 100%) [buf  99%]  10.7x.
Track 01:    4 of  697 MB written (fifo  99%) [buf  27%]   5.3x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 09 B0 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 27 34 0E 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 10036 (not valid) 
cmd finished after 0.797s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 5079040 bytes
Writing  time:   45.282s
Average write speed 180.6x.
Min drive buffer fill was 27%
Fixating...
Fixating time:    0.012s
/usr/bin/wodim: fifo had 272 puts and 81 gets.
/usr/bin/wodim: fifo was 0 times empty and 54 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=20 -dao driveropts=burnfree -overburn -data -tsize=357161s - 
```


Any idea what is going on??? :confused:

---

### Post by applegrew on 2008-05-05
bumping up

---

### Post by applegrew on 2008-05-05
pls help.

---

### Post by sailor2001 on 2008-05-05
try gnomeburner fom synaptics.. I've had better luck with that in Hardy.

---

### Post by rogerp1 on 2008-05-05
I had the same error message when burning. It was because I was listening to mp3's at the same time and it was as if the mp3 player took control of the harddisk and wouldnt let K3B use it. If I burnt the image without anything else running it was OK

---

### Post by applegrew on 2008-05-05
That's weird. I have done that many times. Anyway this time wasn't listening to music anyway. Any more ideas?

---

### Post by applegrew on 2008-05-05
any more ideas?

---

### Post by applegrew on 2008-05-05
Bump!

---

### Post by Periswell on 2008-05-05
run in sudo

goto terminal, do the 'sudo su' thing and run it then?

im just having a guess at your problem.

-josh

---

### Post by applegrew on 2008-05-05
Didn't help. It is now giving new and unique errors like "Cdrecord unknown error, using TAO might help". Using TAO gives "Unable to fixate the disk error try DAO mode". What's goind on. The last update has ****** up my system. K3b now sucks and Kaffeince says that divx codecs are not installed (I have w32codec installed). Thanks ubuntu. Nice work!

---

### Post by Periswell on 2008-05-05
ok dont get angry with ubuntu, try going into synaptic and search CDrecord and install anything that looks like it could help. also try the same with divx.

---

### Post by RJARRRPCGP on 2008-05-05
> Didn't help. It is now giving new and unique errors like "Cdrecord unknown error, using TAO might help". Using TAO gives "Unable to fixate the disk error try DAO mode".

Your new errors remind me of when my first CD drive failed, because it was faulty. 

The new errors likely are because of a bad CD drive. Sorry. 

Even more so if you get errors to the same effect or a similar effect in Windows.

---

### Post by applegrew on 2008-05-05
> **Periswell said:**
> ok dont get angry with ubuntu, try going into synaptic and search CDrecord and install anything that looks like it could help. also try the same with divx.
My videos that were running previously not don't run in kaffeine (I also now no longer get their previews). This happended suddenly. Don't I have a reason to get angry.

---

### Post by applegrew on 2008-05-05
> **RJARRRPCGP said:**
> Your new errors remind me of when my first CD drive failed, because it was faulty. 

The new errors likely are because of a bad CD drive. Sorry. 

Even more so if you get errors to the same effect or a similar effect in Windows.
Ok. But it reads fine. I will verufy this once my Windows partition is recovered.

---

### Post by graben3 on 2008-05-05
> **applegrew said:**
> Ok. But it reads fine. I will verufy this once my Windows partition is recovered.

I agree, seems more like a faulty cd rom drive than anything else. I had weird errors too when mine broke but he, that's nice, it just cost about 30$ to get a brand new one !

---

### Post by applegrew on 2008-05-05
> **applegrew said:**
> My videos that were running previously not don't run in kaffeine (I also now no longer get their previews). This happended suddenly. Don't I have a reason to get angry.
Just reinstalled (purged and installed) Kaffeine and now the video r playing. :) Tried the same with k3b, cdrecord and wodim, but it still doesn't work. :(

---

### Post by applegrew on 2008-05-05
This time tried with another CD and now it progressed to 7% and then this god damn error again. Help. Any suggestions?

---

### Post by greatshape on 2008-07-26
> **applegrew said:**
> This time tried with another CD and now it progressed to 7% and then this god damn error again. Help. Any suggestions?

I'm having the same problem for a long time now, this is getting annoying. 
Why can't the original cdrecord be implemented in (k)ububntu instead of the wodim garbage.

Hope someone comes with a quick solution though.

---

### Post by oldos2er on 2008-07-26
In K3b, go to Settings, Setup System Permissions.

---

### Post by greatshape on 2008-07-27
> **oldos2er said:**
> In K3b, go to Settings, Setup System Permissions.

Hi Ann,

Sorry, I can find K3B, settings, but not "setup system permissions" ?
using K3B 1.0.4 and KDE 3.5.9

Kind regards

---

### Post by diablo75 on 2008-07-27
> This time tried with another CD and now it progressed to 7% and then this god damn error again. Help. Any suggestions?

I'm just gonna bet your drive is failing.  They act funny for about a month while you arm wrestle with the horrendous thought of spending a whole 25 to 30 dollars on a brand new DVD burner.  :roll:

---

### Post by Yannick Le Saint kyncani on 2008-07-27
> **greatshape said:**
> Why can't the original cdrecord be implemented in (k)ububntu instead of the wodim garbage.

I think there's a licensing issue [http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html](http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html)

---

### Post by greatshape on 2008-07-27
> **Yannick Le Saint kyncani said:**
> I think there's a licensing issue [http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html](http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html)

Yes I know, but still the fork is just garbage givng many people headaches or even make people return to windows coz they just can't burn cd's / dvd's. 
Also see: [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html) 

I just can't get cd's to burn succesfully anymore. (already trashed a lot)
Can someone tell me how to solve this the right way? 
I did not have this problem before I upgraded to hardy. 

Kind regards

---

### Post by oldos2er on 2008-07-27
> **greatshape said:**
> Hi Ann,

Sorry, I can find K3B, settings, but not "setup system permissions" ?
using K3B 1.0.4 and KDE 3.5.9

Kind regards

 I'm using K3b 1.0.5, so I guess this has changed. Look in Settings and see if you can find anything relating to permissions; it must be there somewhere.

---

### Post by mdraicch on 2008-11-28
Hi to all,

applegrew, I feel for you, I have exactly the same problem and just can't work out what it is.

It all started with the last upgrade i got with 8.04 and I have never been able to write cd's again, with the exception of brasero which wrote 2 cds very very slowly.

I then tried writing in windows and I got a track following error with nero,
I then loaded 8.10 and no luck, i also tried suse 11, knoppix 5.3.1 and ubuntu 7.10 in live mode with no luck at all.

I can write dvds ok, but not cd's.  I am going to get a new drive today and see if that works.

I can only come to the conclusion that the drive is RS.

Although, I cannot help but wonder, if it is possible for software to damage a drive??

I will let you know what happens.

Regards
Muzza

---

### Post by mdraicch on 2008-11-28
OOPS, didn't realise how old this thread was, never mind, if anyone else googles it at least they will know what happened.

I have replaced my LG gsa-h55n with a pioneer dvr-215, this is a sata drive and everything works ok, all my problems have disappeared.

Windows and ubuntu 8.10 using k3b work OK.

Regards
muzza

---

### Post by SonicSteve on 2009-01-02
Sorry for jumping in, 
I know this thread is bit old and semi-solved. In the hopes that this may help someone else, and since I found a great number of threads about this issue with little success in solving it I want to add this.

For those who come across this thread I had the same issue. 
I found that I needed to 
sudo chmod 777 /media/cdrom
I then did the same to /media/cdrom0 and /media/cdrom1 
these are the filesystem mount points that the cd/dvd drives use. 
I did everything I could think of to /dev/scd0 and /dev/scd1 but the device listings seemed to be fine. It seemed to be a permissions problem with the automount of CD/DVD

---

### Post by gigaferz on 2009-01-04
ill try that, but, I found a solution (not perfect, complains about some mds files)

wine doors (wine) + imgburn

Only for iso burning.

However im still stuck at music burning, and "client" is a common folk that cant burn music, Ughh!.

anyways thx for that post

---

### Post by SonicSteve on 2009-01-31
OK so this doesn't work for me anymore! ARGH!
This is such a silly problem. That seemingly has no fix.

---

### Post by SonicSteve on 2009-02-04
For the record, Just like the OP I too have a Pioneer burner. I don't know for sure if that is significant. 

I noticed that Intrepid 8.10 uses Wodim 1.1.8 and Hardy is using 1.1.6 so I gave Intrepid  try and it works well again. I tried to find a way to install 1.1.8 in hardy 8.04 but found nothing. So it's fixed, at least for now. 

During my travels I found a lot of info about how wodim is a fork of cdrtools and that it is buggy and inferior. The fork had something to do with licensing which the creator of cdrtools claims is hogwash. Just thought I would throw that out there. Don't let that de-rail this thread.

---

### Post by SonicSteve on 2009-03-06
NEW info,

After upgrading to 8.10 intrepid the burning initially worked. Then somewhere along the way it stopped again. Since burners are quite cheap I picked up an LG sata 20x burner. I tested it and it works well. If this changes I'll let you know. 

For the record as far as I know the other burner is still functional also. There may be some DVD firmware issues that are causing this. Updating the firmware may solve this. I know under windows LG offers a firmware update tool, I'm not aware of any such tool for Linux though there is probably a way.

---

### Post by vapor0 on 2009-04-26
My cd-burner had no issues, until I "upgraded" to jaunty. Now I am suffering the same BS as everybody else in this thread. "Cdrecord has no permissions".

Ubuntu devs, would you please offer cdrecord as a package? This wodim sucks a$$...

---

### Post by vapor0 on 2009-04-26
This apparently is because Debian won't let cdrecord be packaged for apt, and uses wodim instead. All my cd burning apps are broken in jaunty.

---

### Post by hpp3 on 2009-04-30
OK, I've solved this.
The first clue is this line in the error log:
```
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.

```
This means that it is trying to lock memory for the burning operation and doesn't have permission. 
There are two ways to deal with this:

**1 -** Set permissions for the CDROM group through the PAM security module.

Open a terminal and type:
```
sudo nano /etc/security/limits.conf
```
and enter this line:
```
@cdrom     -     memlock     unlimited
```
Restart and it should work.

**2 -** Give wodim the root SUID so wodim has root privileges no matter who runs it. 
[[COLOR="Red"]WARNING:[/COLOR] This is the simplest solution, but is a potential security risk]

Open a terminal and type:
```
sudo chmod u+s /usr/bin/wodim
```
Run K3b as usual.

Hope this helps...

---

### Post by DesertEagle on 2009-10-22
> **hpp3 said:**
> OK, I've solved this.
The first clue is this line in the error log:
```
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.

```
This means that it is trying to lock memory for the burning operation and doesn't have permission. 
There are two ways to deal with this:

**1 -** Set permissions for the CDROM group through the PAM security module.

Open a terminal and type:
```
sudo nano /etc/security/limits.conf
```
and enter this line:
```
@cdrom     -     memlock     unlimited
```
Restart and it should work.

**2 -** Give wodim the root SUID so wodim has root privileges no matter who runs it. 
[[COLOR="Red"]WARNING:[/COLOR] This is the simplest solution, but is a potential security risk]

Open a terminal and type:
```
sudo chmod u+s /usr/bin/wodim
```
Run K3b as usual.

Hope this helps...

Thank you so much! This did in fact eliminate the permissions issue (I tried method 1, didn't verify method 2)

You rock!

( On a side note, I burned 2 more coasters after using your method, but I'm pretty sure it has to do with my burner not liking others methods besides TAO, since it reported the same error as on previous runs. )

---

### Post by HeadHunter00 on 2009-11-22
chmod it

---

