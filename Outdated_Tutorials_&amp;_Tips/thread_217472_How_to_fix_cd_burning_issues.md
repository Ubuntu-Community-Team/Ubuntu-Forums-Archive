---
title: "How to fix cd burning issues"
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by wilko on 2006-07-17
I've noticed a number of posts regarding different issues with this and suffered from the same problem myself - namely that I could only successfully burn when running my chosen burning app as sudo. A lot of the posts suggest problems with K3b, Gnomebaker or Ubuntu itself but the problem is present in many distros and is related to cdrecord and kernel versions.  I wouldn't expect a distro resolution anytime soon since Debian has these bugs as outstanding for over a year now.

Anyway this is what I did to fix the issues I suffered from:

_Issue 1:_
Your chosen app or if running cdrecord -scanbus in terminal gives the following or similar error:
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.

This threw me for a long time.  /dev/sg0 is a device that is created at startup.  You can change the permissions on this and burn successfully without running under sudo but the next time you start your machine the problem will simply come back again.

After much research I found that is related to udev (which replaced the previous hotplug system).  A look at 40-permissions.rules in /etc/udev/rules.d confirmed that the # SCSI devices section contained no entry for sg0.  Therefore a new rule is required.  You could simply add the necessary line in 40-permissions.rules but if there is an update to udev it will get overwritten and you'll be back where you started. So I created a new rule and called it 15-local.rules and put the following lines in the file:

# SCSI devices
BUS=="scsi", KERNEL=="sg[0-9]", NAME="%k", GROUP="cdrom"

Note: I have a SATA disk with an IDE burner and my system therefore uses SCSI emulation.  If you have a pure IDE system and have this permissions problem your fix may be slightly different but will still involve a udev rule.

Restart the pc and then, in terminal, run cdrecord -scanbus expecting permissions problems to now be resolved but no - now get:

_Issue 2:_

Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?

So now more research and a note of caution about running executables as suid root.  A regular user will be able to run a program as root if it is set to SUID root. All programs and files on your computer with the s bits appearing on its mode, have the SUID -rwsr-xr-x or SGID -r-xr-sr-x bit enabled. Because these programs grant special privileges to the user who is executing them, it is important to remove the s bits from root-owned programs that won't absolutely require such privilege. Setting a program to run as suid root can create a vulnerability which could potentially grant unauthorized root access to an attacker.

I don't believe that cdrecord will fall into this category but can't guarantee that this the case.  If this concerns you then your only alternative is to run your burning app as sudo - if Gnomebaker or K3b the easiest way is to use the Alacarte Menu Editor and, in Command, place gksudo ahead of the executable name (e.g. gksudo k3b), you'll then be prompted for the sudo password properly in a GUI interface when you run the program.  If you're happy to run cdrecord as suid root do the following:

In terminal run the following commands:

sudo chmod 4755 /usr/bin/cdrecord
sudo chmod 4755 /usr/bin/cdrecord.mmap
sudo chmod 4755 /usr/bin/X11/cdrecord.mmap
sudo chmod 4755 /usr/bin/cdrdao
sudo chmod 4755 /usr/bin/X11/cdrdao

or if preferred type sudo nautilus in terminal, browse to the above files, go to the Permissions tab and check the box Set user ID under Special flags.

That should fix all.  Gnomebaker will run without issue.  If your chosen burner app is K3b you'll get the message "System Configuration Problems - cdrecord = 2.6.8.  Since Linux kernal 2.6.8 cdrecord Solution: use K3bSetup to solve this problem."  This you mustn't do.  If you run K3bSetup it will simply reset the permissionas back again.  You can safely disable this message and K3b should work without issue.

---

### Post by yopnono on 2006-07-17
I had the same in breezy, dapper.
So I just put this in the /etc/rc.local file.

```
chown root:cdrom /dev/sg0
```

Or if you have another device that are for the cdrom just add it.

And after a reboot everything works like it should. Since the rc.local runs at startup

---

### Post by wilko on 2006-07-19
ALways more than one way to skin a rabbit - your way fixes issue 1 as well.  I went for udev because it seems it's going to affect a lot in the future and I felt it was time to get stuck in and learn about it.

---

### Post by mzilhao on 2006-07-21
i've made a fresh dapper install and i'm now having both issues.
it's strage because i don't remember having issue 2 before...
anyway, issue 1 is easily solved, but shouldn't there be another way of solving issue 2? i haven't tried the solution because i'm not able to burn cds under k3b or gnomebaker even with gksudo... 
but i can burn ISOs just fine using nautilus... and i've had no problem erasing cd-rws with k3b or gnomebaker...

---

### Post by wilko on 2006-07-25
Issue 2 is specific in that cdrecord needs root or suid root access to work.  According to the cdrecord manual ([http://www.linuxcommand.org/man_pages/cdrecord1.html](http://www.linuxcommand.org/man_pages/cdrecord1.html)) you can run cdrecord safely as suid root.  Here's a couple of relevant extracts:

"Cdrecord is completely based on SCSI commands but this is no problem as
all CD/DVD  writers ever made use SCSI commands for the communication.
 
In order to be able to use the SCSI transport subsystem of the OS, run
at highest priority and lock itself into core cdrecord either needs  to
be  run  as root, needs to be installed suid root or must be called via
RBACs pfexec mechanism.

If  you  don&#8217;t  want  to  allow  users  to  become root on your system,
cdrecord may safely be installed suid root. This allows all users or  a
group  of  users  with no root privileges to use cdrecord.  Cdrecord in
this case checks, if the real user would have been  able  to  read  the
specified files."

RBACS are role based access control lists.  All I know about them is that they're extremely difficult to set up and can cause all kinds of problems if you don't get them exactly right.  I know they're extensively used in Solaris but, if the problem is easily fixed by running cdrecord as suid root, it didn't seem necessary to go there.

You obviously have another issue that needs fixing first, if you can't burn running as sudo - maybe a broken or missing package, maybe an unsupported burner.  If in terminal you type sudo cdrecord -scanbus this should give you the info you need to track it down.

---

### Post by kecci on 2006-07-25
When i had issues like those you mentioned (typically on fresh installs) i always did

$ sudo dpkg-reconfigure cdrecord

and set it suid root. it worked like a charm ;)

---

### Post by wilko on 2006-07-25
> **kecci said:**
> When i had issues like those you mentioned (typically on fresh installs) i always did

$ sudo dpkg-reconfigure cdrecord

and set it suid root. it worked like a charm ;)

Yep.  That'll do it too.  All it does it set the suid root bit, same as changing permissions on the files.

---

### Post by mzilhao on 2006-07-25
where's what i get when i try to burn an iso with k3b:
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-15-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4160B A301 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-15-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
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
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13993 kB/s 79x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   696 MB        
Total size:      799 MB (79:15.40) = 356655 sectors
Lout start:      800 MB (79:17/30) = 356655 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -12375 (97:17/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 3194
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  696 MB written.
write track data: error after 0 bytes
Writing  time:   73.178s
Average write speed  65.0x.
Fixating...
Fixating time:    0.004s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -dao -eject -data /home/miguel/MyDownloads/SUSE-Linux-10.1-GM-i386-CD1.iso 


```

don't know what is wrong...
any ideas?

thanks in advance,
Miguel

---

### Post by yopnono on 2006-07-25
This don't work if you are using nerolinux like I do.
```
$ sudo dpkg-reconfigure cdrecord
```
I need use my rc.local file and set the permission, for the cdrom scsi device.

---

### Post by wilko on 2006-07-25
> **mzilhao said:**
> where's what i get when i try to burn an iso with k3b:
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-15-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4160B A301 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-15-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
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
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13993 kB/s 79x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   696 MB        
Total size:      799 MB (79:15.40) = 356655 sectors
Lout start:      800 MB (79:17/30) = 356655 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -12375 (97:17/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 3194
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  696 MB written.
write track data: error after 0 bytes
Writing  time:   73.178s
Average write speed  65.0x.
Fixating...
Fixating time:    0.004s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -dao -eject -data /home/miguel/MyDownloads/SUSE-Linux-10.1-GM-i386-CD1.iso 


```

don't know what is wrong...
any ideas?

thanks in advance,
Miguel


Haven't come across that particular issue before but have done an extensive web search for this.  Assuming that your output was from running k3b as sudo and that you were using a new blank cd-r, the most likely cause seems to be firmware.  If there is a firmware update for your drive that may fix it.

---

### Post by mzilhao on 2006-07-25
thanks for your help.
actually i wasn't running as sudo, but i did try as sudo and got a similar output...
i just find it strange because with nautilus i can burn ISOs and data cds just fine... tomorrow i'll try installing nerolinux.

thanks again for your help

---

### Post by deepspring on 2006-07-27
Ubuntu 6.06 seems to be a real curse for my poor DVD burner, no matter what I try, it just won't reliably burn discs.

Even when I follow you're guide, I can burn only one CD, then no more. Not only that I can't mount CD's for reading at all.

You can find the relevant program outputs attached...


Edit: I have just tried k3b with the same results...

---

### Post by deepspring on 2006-07-28
After spending two days ripping my hair out in frustration and going through no less than 20 CD's (all turned into useless coasters), I think I've narrowed down the primary issue...

I believe it has something to do with the kernel SCSI/SATA driver and this particular DVD+/-RW/RAM. Unfortunately I wasn't able to keep logs of everything (flattening and re-installing does that)...

The mainboard itself (Gigabyte GA-8I915G-MF) only has one PATA connector on the board, and 4 SATA connectors. Because of this (and the fact that my burner isn't that old), my system has a hybrid setup, with a SATA WD 250GB HDD and a PATA LG DVD+/-RW/RAM GSA-4163B.

For the past two days, I have been trying to burn CDs using every trick listed on these forums and a few that aren't, to try and burn disks with the above setup. All I got was a crap load of coasters.

So, I decided to do a quick test by replacing the SATA Drive with an old PATA WD 40GB one I had lying around and doing a fresh install of Xubuntu 6.06. 

Needless to say the burner worked flawlessly, I was able to burn a Kubuntu CD ISO at speeds of up to 35X without haven't to alter or tweak anything system or configuration wise.

I checked the device names for the drives (all /dev/hd*) and dmesg, no SCSI drivers appeared to be being used only IDE ones...

So, I removed the old PATA 40GB and put my swanky SATA 250GB back in and installed Kubuntu using the fresh copy I had just burned.

To cut a long story short... I am making coasters again, no matter what I try. ](*,)

I've also noticed this message appearing in the dmesg output:
"Driver 'sd' needs updating - please use bus_type methods"

Now I'm starting to wonder if there is a way to force PATA drives to use the "ide_cd" driver, instead of the scsi one.

---

### Post by lazywanker on 2006-07-28
I've been reading through this thread but cannot figure out why I cannot burn.  Initially I also had the problem '2' but I've followed the commands to fix that.  I'm trying to burn a Knoppix ISO onto 700MB CD-RWs rated as 16-24x with my DVD writer.  Naturally it works great under Windows :P  
I've tried burning at a variety of speeds and settings in gnomebaker and K3b without effect.
Any ideas? 


> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CD/DVDW TS-L532R'
Revision       : 'HA04'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0011 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1451664 = 1417 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Trying to use ultra high speed medium on improper writer.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 1 times full, min fill was 0%.


---

### Post by deepspring on 2006-07-29
Just a quick update...

I re-installed Xubuntu from scratch and I've norrowed the problem down even further to a problem in the latest i686 kernel build. If you stick with the latest i386 kernel build, everything should work as it should.

Also!

I added the following to the "/etc/modules" file:
```
piix
ide-core
ide-cd

```

And added the following to the "/etc/hdparm.conf" file:
```
/dev/scd0 {
        dma = on
}

```

---

### Post by mzilhao on 2006-07-29
i tried your suggestions and apparently they're working for me!
thanks

---

### Post by mzilhao on 2006-07-29
well, looks like i spoke too soon. tried to burn an iso with k3b and got the following:
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-15-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4160B A301 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-15-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
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
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13963 kB/s 79x CD 10x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   674 MB        
Total size:      775 MB (76:47.09) = 345532 sectors
Lout start:      775 MB (76:49/07) = 345532 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -12375 (97:17/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 14317
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  674 MB written.
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   73.208s
Average write speed  63.0x.
Fixating...
Fixating time:    0.004s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -dao -eject -data /home/shared/Downloads/distros/PCBSD-1.2-x86-CD1.iso 


```

---

### Post by deepspring on 2006-07-30
Found another possible reason for the wonderful coaster function...

Xfburn burns CD ISO's flawlessly, GnomeBaker will not burn a sodded thing.

Here is what dmesg spits out after trying to burn a CD with GnomeBaker:

```
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4e20
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f6780
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff30c0
[17179569.184000] ACPI: MCFG (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6d00
[17179569.184000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6c40
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:90000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2793.520 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.960000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.960000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.980000] Memory: 1028816k/1048512k available (1976k kernel code, 18944k reserved, 606k data, 288k init, 131008k highmem)
[17179572.980000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.060000] Calibrating delay using timer specific routine.. 5593.08 BogoMIPS (lpj=11186166)
[17179573.060000] Security Framework v1.0.0 initialized
[17179573.060000] SELinux:  Disabled at boot.
[17179573.060000] Mount-cache hash table entries: 512
[17179573.060000] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[17179573.060000] CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[17179573.060000] monitor/mwait feature present.
[17179573.060000] using mwait in idle threads.
[17179573.060000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179573.060000] CPU: L2 cache: 256K
[17179573.060000] CPU: After all inits, caps: bfebfbff 00100000 00000000 00000080 0000451d 00000000 00000000
[17179573.060000] mtrr: v2.0 (20020519)
[17179573.060000] CPU: Intel(R) Celeron(R) CPU 2.80GHz stepping 01
[17179573.060000] Enabling fast FPU save and restore... done.
[17179573.060000] Enabling unmasked SIMD FPU exception support... done.
[17179573.060000] Checking 'hlt' instruction... OK.
[17179573.076000] checking if image is initramfs... it is
[17179573.620000] Freeing initrd memory: 6625k freed
[17179573.632000] ACPI: Looking for DSDT ... not found!
[17179573.632000] ENABLING IO-APIC IRQs
[17179573.632000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.776000] NET: Registered protocol family 16
[17179573.776000] EISA bus registered
[17179573.776000] ACPI: bus type pci registered
[17179573.776000] PCI: PCI BIOS revision 3.00 entry at 0xfacd0, last bus=2
[17179573.776000] PCI: Using MMCONFIG
[17179573.780000] ACPI: Subsystem revision 20051216
[17179573.784000] ACPI: Interpreter enabled
[17179573.784000] ACPI: Using IOAPIC for interrupt routing
[17179573.784000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.784000] PCI: Probing PCI hardware (bus 00)
[17179573.788000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179573.788000] Boot video device is 0000:01:00.0
[17179573.788000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.788000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.800000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[17179573.800000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179573.800000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.800000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179573.800000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[17179573.800000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.800000] pnp: PnP ACPI init
[17179573.804000] pnp: PnP ACPI: found 10 devices
[17179573.804000] PnPBIOS: Disabled by ACPI PNP
[17179573.804000] PCI: Using ACPI for IRQ routing
[17179573.804000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.824000] pnp: 00:06: ioport range 0x400-0x4bf could not be reserved
[17179573.828000] PCI: Bridge: 0000:00:01.0
[17179573.828000]   IO window: disabled.
[17179573.828000]   MEM window: e8000000-efffffff
[17179573.828000]   PREFETCH window: e0000000-e7ffffff
[17179573.828000] PCI: Bridge: 0000:00:1e.0
[17179573.828000]   IO window: a000-afff
[17179573.828000]   MEM window: f0000000-f1ffffff
[17179573.828000]   PREFETCH window: 50000000-500fffff
[17179573.828000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.828000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.828000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.828000] audit: initializing netlink socket (disabled)
[17179573.828000] audit(1154222735.828:1): initialized
[17179573.828000] highmem bounce pool size: 64 pages
[17179573.828000] VFS: Disk quotas dquot_6.5.1
[17179573.828000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.828000] Initializing Cryptographic API
[17179573.828000] io scheduler noop registered
[17179573.828000] io scheduler anticipatory registered
[17179573.828000] io scheduler deadline registered
[17179573.828000] io scheduler cfq registered
[17179573.828000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.828000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.828000] assign_interrupt_mode Found MSI capability
[17179573.828000] Allocate Port Service[pcie00]
[17179573.828000] Allocate Port Service[pcie03]
[17179573.828000] isapnp: Scanning for PnP cards...
[17179574.180000] isapnp: No Plug & Play device found
[17179574.204000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.204000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.204000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.204000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.204000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.208000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.208000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.208000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.208000] mice: PS/2 mouse device common for all mice
[17179574.208000] EISA: Probing bus 0 at eisa.0
[17179574.208000] EISA: Detected 0 cards.
[17179574.208000] NET: Registered protocol family 2
[17179574.248000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.248000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179574.248000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.248000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.248000] TCP reno registered
[17179574.248000] TCP bic registered
[17179574.248000] NET: Registered protocol family 1
[17179574.248000] NET: Registered protocol family 8
[17179574.248000] NET: Registered protocol family 20
[17179574.248000] Using IPI Shortcut mode
[17179574.248000] ACPI wakeup devices: 
[17179574.248000] PCI0 PEX0 PEX1 PEX2 PEX3 HUB0 USB0 USB1 USB2 USB3 USBE AC97 MC97 AZAL 
[17179574.248000] ACPI: (supports S0 S1 S4 S5)
[17179574.248000] Freeing unused kernel memory: 288k freed
[17179574.304000] vga16fb: initializing
[17179574.304000] vga16fb: mapped to 0xc00a0000
[17179574.512000] Console: switching to colour frame buffer device 80x25
[17179574.512000] fb0: VGA16 VGA frame buffer device
[17179574.524000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.584000] Capability LSM initialized
[17179575.768000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179576.504000] SCSI subsystem initialized
[17179576.504000] ACPI: bus type scsi registered
[17179576.504000] libata version 1.20 loaded.
[17179576.504000] ata_piix 0000:00:1f.2: version 1.05
[17179576.504000] ata_pci_init_one: pci_dev class+intf: 0x10180
[17179576.504000] ata_pci_init_one: NO_LEGACY == 0
[17179576.504000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 193
[17179576.504000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.504000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xF000 irq 14
[17179576.668000] ata1: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3c41 87:4023 88:207f 93:0000
[17179576.668000] ata1: dev 0 ATA-7, max UDMA/133, 488395055 sectors: LBA48
[17179576.668000] ata_acpi_push_id: skipping for PATA mode
[17179576.668000] ata1: dev 0 configured for UDMA/133
[17179576.668000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.668000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdfffef20
[17179576.668000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179576.668000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe8cc0
[17179576.668000] scsi0 : ata_piix
[17179576.668000]   Vendor: ATA       Model: WDC WD2500JS-00N  Rev: 10.0
[17179576.668000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.668000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.668000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdfffef20
[17179576.668000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179576.668000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xF008 irq 15
[17179576.988000] ata2: dev 0 cfg 00:85c0 49:0f00 82:421c 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:604f
[17179576.988000] ata2: dev 0 ATAPI, max UDMA/33
[17179576.988000] ata2(0): applying bridge limits
[17179576.988000] ata_acpi_push_id: skipping for PATA mode
[17179576.988000] ata2: dev 0 configured for UDMA/33
[17179576.988000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.988000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdfffef20
[17179576.988000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179576.988000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe8b40
[17179576.988000] scsi1 : ata_piix
[17179576.992000]   Vendor: HL-DT-ST  Model: DVDRAM GSA-4163B  Rev: A103
[17179576.992000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179576.996000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.996000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdfffef20
[17179576.996000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179577.004000] Driver 'sd' needs updating - please use bus_type methods
[17179577.012000] SCSI device sda: 488395055 512-byte hdwr sectors (250058 MB)
[17179577.020000] SCSI device sda: drive cache: write back
[17179577.024000] SCSI device sda: 488395055 512-byte hdwr sectors (250058 MB)
[17179577.024000] SCSI device sda: drive cache: write back
[17179577.024000]  sda: sda1 sda2 sda3
[17179577.032000] sd 0:0:0:0: Attached scsi disk sda
[17179577.312000] usbcore: registered new driver usbfs
[17179577.312000] usbcore: registered new driver hub
[17179577.316000] USB Universal Host Controller Interface driver v2.3
[17179577.316000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179577.316000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.316000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.316000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.316000] uhci_hcd 0000:00:1d.0: irq 201, io base 0x0000bc00
[17179577.320000] hub 1-0:1.0: USB hub found
[17179577.320000] hub 1-0:1.0: 2 ports detected
[17179577.424000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179577.424000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.424000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.424000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.424000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000b000
[17179577.424000] hub 2-0:1.0: USB hub found
[17179577.424000] hub 2-0:1.0: 2 ports detected
[17179577.528000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179577.528000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.528000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.528000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.528000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000b400
[17179577.528000] hub 3-0:1.0: USB hub found
[17179577.528000] hub 3-0:1.0: 2 ports detected
[17179577.632000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.632000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.632000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.632000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.632000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000b800
[17179577.632000] hub 4-0:1.0: USB hub found
[17179577.632000] hub 4-0:1.0: 2 ports detected
[17179577.736000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 201
[17179577.736000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.736000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.736000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.736000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.736000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xf2000000
[17179577.740000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.740000] hub 5-0:1.0: USB hub found
[17179577.740000] hub 5-0:1.0: 8 ports detected
[17179577.864000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179577.864000] ide0: ports already in use, skipping probe
[17179577.864000] ide1: I/O resource 0x170-0x177 not free.
[17179577.864000] ide1: ports already in use, skipping probe
[17179577.896000] Attempting manual resume
[17179577.904000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[17179578.632000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17179579.028000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[17179579.176000] usbcore: registered new driver hiddev
[17179579.180000] input: Logitech USB Gaming Mouse as /class/input/input1
[17179579.180000] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.3-1
[17179579.192000] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.3-1
[17179579.192000] usbcore: registered new driver usbhid
[17179579.192000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179579.204000] Initializing USB Mass Storage driver...
[17179579.204000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179579.204000] usb-storage: device found at 3
[17179579.204000] usb-storage: waiting for device to settle before scanning
[17179579.204000] usbcore: registered new driver usb-storage
[17179579.204000] USB Mass Storage support registered.
[17179579.940000] ReiserFS: sda2: using ordered data mode
[17179579.952000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179579.952000] ReiserFS: sda2: checking transaction log (sda2)
[17179579.976000] ReiserFS: sda2: Using r5 hash to sort names
[17179584.212000]   Vendor: HP        Model: Photosmart 7400   Rev: 1.00
[17179584.212000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179584.256000] sd 2:0:0:0: Attached scsi removable disk sdb
[17179584.256000] usb-storage: device scan complete
[17179587.200000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179587.200000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179587.200000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17179587.204000] ts: Compaq touchscreen protocol output
[17179587.312000] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[17179587.312000] Uniform CD-ROM driver Revision: 3.20
[17179587.312000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179588.928000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.928000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.264000] hw_random hardware driver 1.0.0 loaded
[17179589.272000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.272000] agpgart: Detected an Intel 915G Chipset.
[17179589.292000] agpgart: AGP aperture is 256M @ 0x0
[17179589.308000] input: PC Speaker as /class/input/input2
[17179589.320000] Real Time Clock Driver v1.12
[17179589.344000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.348000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.348000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179589.348000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179589.988000] gameport: EMU10K1 is pci0000:02:01.1/gameport0, io 0xa400, speed 877kHz
[17179590.188000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179590.188000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 217
[17179590.188000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179590.188000] eth0: RTL8169 at 0xf8a66000, 00:0f:ea:ea:af:c2, IRQ 217
[17179590.364000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179590.540000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
[17179590.540000] usbcore: registered new driver usblp
[17179590.540000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179591.468000] r8169: eth0: link down
[17179591.560000] lp: driver loaded but no devices found
[17179591.612000] Adding 1076312k swap on /dev/sda1.  Priority:-1 extents:1 across:1076312k
[17179592.108000] r8169: eth0: link up
[17179592.524000] NET: Registered protocol family 17
[17179592.748000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.748000] md: bitmap version 4.39
[17179593.264000] NET: Registered protocol family 10
[17179593.264000] lo: Disabled Privacy Extensions
[17179593.264000] IPv6 over IPv4 tunneling driver
[17179593.372000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179596.664000] cdrom: open failed.
[17179597.048000] kjournald starting.  Commit interval 5 seconds
[17179597.048000] EXT3 FS on sda3, internal journal
[17179597.048000] EXT3-fs: mounted filesystem with ordered data mode.
[17179602.684000] pcc_acpi: loading...
[17179602.700000] ACPI: Power Button (FF) [PWRF]
[17179602.700000] ACPI: Power Button (CM) [PWRB]
[17179602.744000] ibm_acpi: ec object not found
[17179603.360000] eth0: no IPv6 routers present
[17179607.924000] ppdev: user-space parallel port driver
[17179608.220000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179608.220000] apm: overridden by ACPI.
[17179616.668000] Bluetooth: Core ver 2.8
[17179616.668000] NET: Registered protocol family 31
[17179616.668000] Bluetooth: HCI device and connection manager initialized
[17179616.668000] Bluetooth: HCI socket layer initialized
[17179616.704000] Bluetooth: L2CAP ver 2.8
[17179616.704000] Bluetooth: L2CAP socket layer initialized
[17179616.728000] Bluetooth: RFCOMM socket layer initialized
[17179616.728000] Bluetooth: RFCOMM TTY layer initialized
[17179616.728000] Bluetooth: RFCOMM ver 1.7
[17195044.756000] cdrom: This disc doesn't have any tracks I recognize!
[17195059.384000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.412000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.448000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.460000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.472000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.504000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.520000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195059.580000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.064000] scsi: unknown opcode 0x01
[17195060.092000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.108000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.128000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.144000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.160000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.192000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195060.208000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195062.240000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195062.248000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195062.284000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195062.304000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195161.868000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195205.340000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195205.424000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17195205.480000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17195205.540000] ISOFS: changing to secondary root
[17196290.776000] cdrom: This disc doesn't have any tracks I recognize!
[17196441.540000] cdrom: This disc doesn't have any tracks I recognize!
[17196662.956000] cdrom: This disc doesn't have any tracks I recognize!
[17196682.108000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.136000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.176000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.188000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.200000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.236000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.252000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196682.312000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.884000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.900000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.924000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.940000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.956000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196683.988000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196684.000000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196686.036000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196686.044000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196686.084000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196686.104000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[17196786.892000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531

```

---

### Post by mzilhao on 2006-08-03
just tried nero linux and apparently it's working fine. burned an ISO with no problems at all...
so, i'm gessing the problem is only with cdrecord...

---

### Post by mzilhao on 2006-08-04
another update: 
it turns out that the only reason i was able to burn ths ISO with nero linux was that the cd automount was disabled. 
i followed [this thread]("http://ubuntuforums.org/showthread.php?t=184786") to enable it again, and now i can't burn cds, once again...
so, it appears that somehow, the automounting feature confuses cdrecord, and nero and everything that burns cds. except for nautilus, that burns cds just fine...
can anyone confirm this?

---

### Post by autosuggested on 2006-08-04
Thanks, Wilco, I was churning out coaster after coaster until I found your solution to Issue #2.

// Dave

---

### Post by GoldBuggie on 2006-09-03
thank you for this solution

---

### Post by silpol on 2006-12-22
Have you ever thought to file bugs? :mrgreen: 

> **wilko said:**
> I've noticed a number of posts regarding different issues with this and suffered from the same problem myself - namely that I could only successfully burn when running my chosen burning app as sudo. A lot of the posts suggest problems with K3b, Gnomebaker or Ubuntu itself but the problem is present in many distros and is related to cdrecord and kernel versions.  I wouldn't expect a distro resolution anytime soon since Debian has these bugs as outstanding for over a year now.

Anyway this is what I did to fix the issues I suffered from:

/* rest removed by silpol for clarity */



---

### Post by wilko on 2006-12-24
> **silpol said:**
> Have you ever thought to file bugs? :mrgreen:
As stated in original post both bugs have been listed as outstanding at Debian for ages.  They are also listed a number of times in Launchpad as Ubuntu bugs.

Issue 1 seems to be specific to SATA drives and can be easily fixed in anumber of ways - I used udev for the reasons stated.  Hopefully Feisty will fix this.

Issue 2 isn't really a bug - the cdrecord manual specifies the need for cdrecord to be run as suid root and the resolution is listed in Launchpad a number of times.  The only surprise is that no distros (other than Solaris where the original maintainer now works) has addressed this.

---

### Post by irsic on 2007-01-26
I have a similar problem though.
when a type
$cdrecord -scanbus
i got
```
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
```

is there any official version?!?!
tnx for help

btw
the funny thing is that it burns ok with command
cdrecord speed=4 dev=/dev/cdrw file.iso
if the CD-RW was previously blank.
but it deosn't allow erasing CD-RW
when trying command
cdrecord dev=/dev/cdrw blank=fast
it says
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.

tnx for help

---

### Post by billybag on 2007-01-30
I am getting the same problem as MZILHAO

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SAMSUNG '
Identifikation : 'CD-R/RW SW-252F '
Revision       : 'R801'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1279488 = 1249 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 20.073s timeout 60s
cdrecord: OPC failed.
Writing  time:   24.373s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

```

the problem did not seem to happen until i installed GNORMALIZE. Before that, my cdburner/gnomebaker worked fine... i am going crazy though, trying to figure out a solution. i have so many CDs/Data Disks i need to burn. Has anyone found a solution?!!!

---

### Post by mzilhao on 2007-01-30
well, i haven't found a solution, but there is a workaround: brasero. 
works great, though it doesn't have all the k3b features.

---

### Post by billybag on 2007-01-30
> **mzilhao said:**
> well, i haven't found a solution, but there is a workaround: brasero. 
works great, though it doesn't have all the k3b features.
tried that app. It also had problems. It could not mount the drive

i am really determined to fix this. now, this seemed to have happened after i installed GNORMALIZE because i had burned a few CDs less than 24 hours before.

I had DLed a torrent and found that the formats were mp4 and i wanted them to be mp3 si i installed GNORMALIZE [which worked great by the way] and then i went to use gnomebaker so i can make a cd and i had no dice, same with trying to make a data disk. i am just wondering if maybe you installed anything similar before it happened to you?

---

### Post by vladf on 2007-01-31
> **irsic said:**
> when trying command
cdrecord dev=/dev/cdrw blank=fast
it says
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
May be you forgot umount /dev/cdrw (or /dev/cdrom) device? It could be mounted automatically.

---

### Post by mzilhao on 2007-01-31
> I had DLed a torrent and found that the formats were mp4 and i wanted them to be mp3 si i installed GNORMALIZE [which worked great by the way] and then i went to use gnomebaker so i can make a cd and i had no dice, same with trying to make a data disk. i am just wondering if maybe you installed anything similar before it happened to you?

no, i never installed gnormalize, or anything like it. 
i could only use gnomebaker/k3b/cdrecord successfully when i had my automounting off.

---

### Post by angelmb on 2007-02-05
Hi, what king of burning issue do you all have? Can you start burning?. In my case K3b, GnomeBaker or even graveman! start burning without problem. It is only after the 3rd or 4th song that the burning process unexpectedly stops. (session is closed). I have a post where I have pasted the error log.

Please take a look: [http://www.ubuntuforums.org/showthread.php?t=353518](http://www.ubuntuforums.org/showthread.php?t=353518)

I'll try running cdrecord as root, but I see from other users that this may not work.

The funny thing is that I have another laptop (HP n610C) where burning works perfectly well. It is only in my newer laptop (Acer 1692) where I have this problem.

Thanks!

---

### Post by the_james on 2007-02-09
thank you wilko that worked splendidly.

---

### Post by am_pcguy on 2007-02-24
I still have problems, I started with the same problems, and did fixes 1 and 2.

now I get this...

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-11-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GMA-4082N'
Revision       : 'PT06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13552 kB/s 77x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 9B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
cdrecord: Please report.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.


```

Right here the Nautlis cd recording dialog box pops up.  "You have inserted a blank CD would you like to open a folder" I choose "ignore".

```

write track data: error after 317440 bytes
Writing  time:   18.872s
Average write speed 190.8x.
Fixating...
Fixating time:   27.581s
cdrecord: fifo had 69 puts and 6 gets.
cdrecord: fifo was 0 times empty and 2 times full, min fill was 93%.

```

I can see why there would be a buffer underrun if the record speed is 190x but I set it to 16x.
I'm on my 14h coaster at this point.  

I am almost positive it has something to do with the Nautilus CD burner.  Is that possible?  How do I turn it off?  Any other ideas?

Thanks

---

### Post by voltsy on 2007-03-03
hi am_pcguy

If you're are convinced it is Nautilus's CD burner, is it relevant that previous posters said to turn off the automount? Maybe turning off automount makes Nautilus "unaware" that a disk is there? k3b goes looking for it - Nautilus prolly doesn't care or is agnostic. ;-)

---

### Post by drmbogo on 2007-04-20
Billybag,
I'm having a similar problem on my home machine; I get the same errors, i.e. "is cdrecord installed as SUID root",  AND "OPC Failed"
On my machine here at work, when burning a disc, I still get the "Is cdrecord...root" message, but it seems to burn fine. I've burned several audio cd's using gnomebaker, w/ no problems. I did have a problem w/ a data disc of mp3's that didn't quite work (Had 5 folders, only the first one was readable by my computer or my car stereo) I'm not at home to try the suggestions by wilko, but I'll try later...

Any know what OPC is/does and why it failed?

---

### Post by jmate24 on 2007-08-16
i did almost every thing that was suggested and a little bit more here is my GnomeBaker output now: 

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1H  '
Revision       : 'LL05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 988416 = 965 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 5645 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Writing  time:   55.414s
Average write speed  19.5x.
Min drive buffer fill was 77%
Fixating...
Fixating time:   16.230s
BURN-Free was never needed.

it's working!

and here is my hdparm.conf file:
```
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = passwrite_cache = oword
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for thwrite_cache = oose more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

/dev/hdb {
       dma = on
       defect_mana = on
       lookahead = on
       cd_speed = 48
       write_cache = on
}

/dev/scd0 {
        dma = on
        defect_mana = on
        lookahead = on
        cd_speed = 48
        write_cache = on
}
```

i put both instances and now it works execpt for sound juicer!

---

### Post by the badger on 2007-09-01
cheers wilko! "issue 2" was sorted by changing file permissions.this does seem to create a non-user-friendly vs possibly-insecure dichotomy... perhaps as i better understand linux i'll figure this out. 

meanwhile: less coasters! more cds!

---

### Post by Masaaah on 2007-11-26
Hi,
My burner does not burn! Stops during the Lead-in with an write error. I have updated my firmware, runned antiviruses, adwares, reinstalled hard/softwares, reinstalled drivers.
Haven't tryed yet on other computer or with other cables.. is my burner dead?

Log file should be an attachment on this message

---

### Post by Masaaah on 2007-11-26
Masaaah here again

 MY dvd-drive is LG 4160B with A306 Firmware

TY

---

### Post by djgrant on 2008-07-18
Thanks so much wilko. chmod cdrecord fixed all my issues.

---

### Post by Frazzle2 on 2008-07-20
Has anyone exprienced "unknown error" problems with Brasero while trying to copy CD's using Unubtu 8.04?  I managed to copy the CD fine under Windows.

---

### Post by Drakkenkill on 2009-12-23
Well All these commands make no sense to me but i tried to burn a version of puppy linux on to a cd and it got like half way and said there was an error and i couldn't open my cd drive till i restarted my computer anyone have some advise?

---

