---
title: "How to burn .bin/.cue files with K3B for absolute Newbies."
date: 2006-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by ninjahelperbot on 2006-07-05
Hi,

If your like me and often need to burn .bin/.cue files to CD this is how to do it.

1. You will need K3B (a great CD burning tool).  To get this all you need to do is move you mouse up to SYSTEM in the drop down menu select ADMINISTRATION and then click on SYNAPTIC PACKAGE MANAGER (this contains lots of free software).  A box will open asking for your root password enter this now.  In the SYNAPTIC PACKAGE MANAGER WINDOW select search and write K3B in the search box then push return.  You should get a few results but what is important is that K3B will be in the list.  Select this and right click.  Now select mark for installation (in the menu that appeared when you right clicked on K3B).  Now push apply.  The software should install (it is downloaded from the package server then installed onto your computer).  

2. Now confirm that K3B has been installed by checking in applications (top left of screen in drop down menus, just point and click).  Its there?  If not got to Add/Remove... and use the window that opens to find and install K3B (If you figured out Package manager you will find this easy, search, point click, apply).

3.  Open the K3B CD burner.  You should get in program window (graphics and all).  Now select BURN CD IMAGE.  In the new window Click on the little blue folder in the top left.  This opens another window that allows you to find your .bin/.cue file.  Assuming you know were it is, select it and push ok.  Now it is important to mention that you will only see a .cue file only in the open file window don't worry this is ok just click on the .cue file and it will automaticly load the .bin as well.

4.  Now your ready, CD in drive push start and wrrrrrr....  You now have a CD with your .bin files on. Now use them for whatever purpose you had for them.  Wasn't That was simple. Well done and Enjoy.=D> 

NINJAHELPERBOT

Keywords: K3B, CD, BURNING, IMAGE, BIN, CUE, .BIN, .CUE. .BIN/.CUE, 

Other useful stuff: Look into Bchunk (BIN TO ISO), NERO for Linux. Gnome Baker.  Synaptics Package Manager.

---

### Post by gorilla_king on 2006-07-06
wow, u wernt kidding, real noob stuff, but it's always good to know how to burn .bin and .cue

But when i'm not wanting to burn them and only watch them on the computer, i usually use vlc media player. Only because most player can't read the format. Well, i didn't really mean for that to be helpful, i meant it mearly as a statement, but hey, maybe it will be helpful to someone.

---

### Post by SimpleKnowledge on 2006-07-08
I am an absolute newbie wondering what to do with this .bin file I just downloaded.  This really did help me.  Thank you.

---

### Post by gorilla_king on 2006-07-08
> **SimpleKnowledge said:**
> I am an absolute newbie wondering what to do with this .bin file I just downloaded.  This really did help me.  Thank you.

it should have come with a .cue as well. so if ur trying to watch it, i'd suggest you get VLC media player (in synaptic) and once you have it running just open the .bin file. If your going to burn it to a cd or dvd so u can watch it on your tv, use the above instructions.

---

### Post by Scoobstcb on 2006-07-21
Cheers Mate

I am an absolute noob and this has been bugging me for months

Cheers

---

### Post by IrishGangsta on 2006-07-31
you said we can burn the .cue and .bin files to a CD right?
Or do i have to use  DVD?

IF i can use a cd, and i followed ur instructions correct, when i push start i got an error message saying cdrecord has no permission to open the device.
And it tells me i can use k3bsetup2 to solve this problem. 

Then i clicked on debugging report and got this:
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
_NEC DVD+-RW ND-6650A 102C (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=24 -dao driveropts=burnfree cuefile=/home/mike/Pirates of the Caribbean Dead Man's Chest (2006) PuKKa Telesync KvCD by Hockney(TUS Release)/dmc (2006) PuKKa Telesync KVCD by Hockney.cue -eject

---

### Post by fakie_flip on 2006-08-27
> **gorilla_king said:**
> i usually use vlc media player. Only because most player can't read the format.

If that's the only reason, try Mplayer. It's great. The user interface is much better. It supports many formats as well including these bin and cue files. You can tell I am using it.

---

### Post by Ausus on 2006-08-27
HiIrishGangsta,
This is what I get using gnomebaker.
Look nearly the same.
Part of knomebaker messages:
[HTML]cdrecord: Warning: Running on Linux-2.6.15-26-amd64-k8
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.[/HTML]

This is only small portion which i did cut and past, to show

regards

---

### Post by kpkeerthi on 2006-08-27
You may follow this guide to fix the permission denied problem...

[http://ubuntuforums.org/showthread.php?t=217472](http://ubuntuforums.org/showthread.php?t=217472)

---

### Post by fakie_flip on 2006-08-28
By following your directions, I have this problem. K3b fails when it tries to send cue sheet. I'm not sure what the meaning is. Here is the debugging output. I did try burning at a slower speed. I still get the same message about unable to send cue sheet. Any ideas?

```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
PIONEER DVD-RW  DVR-105 1.30 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-105 '
Revision       : '1.30'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data     1 MB        
Track 02: data   802 MB        
Total size:      803 MB (79:35.25) = 358144 sectors
Lout start:      803 MB (79:37/19) = 358144 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 1701
Starting to write CD/DVD at speed 16 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
/usr/bin/X11/cdrecord: Success. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 30 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 26 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 48
cmd finished after 0.014s timeout 200s
/usr/bin/X11/cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/X11/cdrecord: Cannot send CUE sheet.
/usr/bin/X11/cdrecord: Could not write Lead-in.
Writing  time:    7.487s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=16 -dao driveropts=burnfree cuefile=/home/veronica/Movie.cue -eject 


```

---

### Post by gary4gar on 2006-08-29
guys when i burn a cu/bim image file & select a cue file and then it show bin file not found.also i virifies the MD5 check sums. i am posting my error msg here.**pls help out!**

> 
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
SONY CD-RW  CRX320E NYK5 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+R DL] [DVD-ROM; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrdao: 1.2.1

cdrdao
-----------------------
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
ERROR: Could not find input file "Microsoft.Windows.XP.Media.Center.Edition.2005.CD1.[WwW.LiMiTeDiVx.CoM].BIN".

cdrdao command:
-----------------------
/usr/bin/X11/cdrdao write --device /dev/hdd --speed 40 -n -v 2 --force --eject --remote 16 /media/windows/Microsoft.Windows.XP.Media.Center.Edition.2005.2CDs.[[WwW.LiMiTeDiVx.CoM]/Microsoft.Windows.XP.Media.Center.Edition.2005.CD1](WwW.LiMiTeDiVx.CoM]/Microsoft.Windows.XP.Media.Center.Edition.2005.CD1).[[WwW.LiMiTeDiVx.CoM].cue](WwW.LiMiTeDiVx.CoM].cue) 



---

### Post by lefty.crupps on 2006-08-30
What do i do if I only have the .bin file?

---

### Post by gslo on 2006-12-31
Thanks for the quick lesson!

---

### Post by adarkmethod on 2007-03-09
what if i only have dvD disks? will clicking "Burn DVD ISO Image" and doing the same thing work?

---

### Post by fakie_flip on 2007-03-21
I used bchunk to convert my bin/cue to iso. It worked great! After that I was able to mount the iso with "sudo mount -o loop file.iso /mnt/point"

---

### Post by grahams on 2007-03-29
You can also use mencoder to re-encode to a more friendly format, then watch via xine or mplayer and/or burn to cd or dvd. The example bellow took an 800MB bin file (I didn't have an 800MB cd-r/rw) and converted it to a 550MB xvid4 file.

mencoder filename.bin -oac mp3lame -lameopts vbr=2:q=3  -ovc l
avc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2 -ffourcc DIVX:vbitrate=1054 -o filename.avi

(I'm forcing the fourcc to DIVX so my philips dvd player will play it)

---

### Post by Angelbeast on 2007-05-15
I just installed Bchunk but i can't find it in the apps menu...does it work on 64 bit Ubuntu?

---

### Post by xjgnsdof on 2007-08-20
Assuming that you have permission to modify the .bin and .cue files, all you have to do is change the filename and extension for each .bin and .cue file to upper case. Then, k3b will read the cue and burn the .bin just fine.

For example, I had three .cue and .bin pairs called "MAFIA1," "MAFIA2" and "MAFIA3" that all had lower case extensions. Once I changed the extension to upper case, the project completed successfully. I'm not sure if the entire filename also has to be upper case, but definitely the extensions should be.

---

### Post by Note360 on 2007-08-26
I am getting a real problem here...

I have been trying to burn some bin cues but every time I burn it when I go play it in my dvd player I get a rolling thing if you know what I mean... I tried it a million times by now.

---

