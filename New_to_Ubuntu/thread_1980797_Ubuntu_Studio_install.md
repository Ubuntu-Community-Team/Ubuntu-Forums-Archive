---
title: "Ubuntu Studio install"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by JXR on 2012-05-15
Rest assured this is a beginner's question, but redirect me if I should be posting to a more appropriate forum...

I recently procured a relatively powerful computer on which I'd like to install Ubuntu Studio (primarily for sound work). Currently it's running Windows7.

My understanding is that Ubuntu (12.04 LTS) is the operating system and Ubuntu Studio (12.04 LTS) is an application set (or set of class libraries) that's installed onto Ubuntu, the operating system.

In other words the install procedure is:
1) Download and install Ubuntu Desktop 12.04 LTS
2) IF THAT GOES SMOOTHLY, download (somehow burn onto a DVD - I suppose I can use InfraRecorder?) and install Ubuntu Studio 12.04 LTS 

Right?

Thanks

---

### Post by acimi66 on 2012-05-15
short answer: YES!

Once you have Ubuntu as your os go here:

[http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/)

And follow the instructions.

Good luck

---

### Post by Frogs Hair on 2012-05-15
You can install Ubutnu and add the studio programs but it would be easier to start with the Ubuntu Studio ISO.

[http://cdimage.ubuntu.com/ubuntustudio/releases/12.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/12.04/release/) 

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Installation](https://help.ubuntu.com/community/Ubuntu%20Studio%20Installation)  

[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by JXR on 2012-05-17
I waited long enough to be confused...

Immediately after receiving a reply I downloaded and checksummed:
1)  ubuntu-12.04-desktop-i386.iso     718,124 KB   and
2)  **ubuntustudio-12.04-dvd-i386.iso**   1,949,996 KB

thinking I needed to install 
#1 followed by #2

Then I got reply #2. I'd much rather do a single install so I went to [https://help.ubuntu.com/community/Ubuntu%20Studio%20Installation](https://help.ubuntu.com/community/Ubuntu%20Studio%20Installation) and from there was directed to [http://cdimage.ubuntu.com/ubuntustudio/releases/](http://cdimage.ubuntu.com/ubuntustudio/releases/) which was just a directory of iso images. Picking the highest number (release) eventually got me back to **ubuntustudio-12.04-dvd-i386.iso **

So the question now is: **[COLOR=Red]Is ubuntustudio-12.04-dvd-i386.iso  the only install I need to do to get Ubuntu w. UbStudio?[/COLOR]** (I think I'll start with a dual boot and if everything works out eventually sack Windows.) [COLOR=Red]Also, I assume that this install does not limit me to only running the Ubuntu Studio suite (but also allows me to download/run other open source sound software), Right?[/COLOR]

Thanks

---

### Post by Cheesemill on 2012-05-17
You only need the Ubuntu Studio DVD.

No need to install Ubuntu first.

---

### Post by JXR on 2012-09-16
a problem.
 
Following [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
In trying to (Windows XP) burn the DVD with InfraRecorder (at minimum speed - 7.5x)
 
After:
Started to write track 1.
Input/Output error
A write error occurred. Please see program log...
Please properly read the error message above.
 
The program log says:
 
>  > BURN-Free is ON.
> Starting new track at sector: 0
> 0x
> Track 01: writing 30 KB of pad data
> Track 01: Total bytes read/written: 1996795904/1996826624 (975013 sectors)
> Writing time: 171
> 844s
> Average write speed 8
> 4x
> Min drive buffer fill was 80
> Fixating
> Fixating time: 28
> 078s
> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: fifo had 60938 puts and 60938 gets
> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: fifo was 2 times empty and 4432 times full, min fill was 0
CCore::ProcessEnded
Process exited with code: 0.
CCore::BurnImage
[0,1,0] PHILIPS DVD+-RW DVD8801 4D28
File = H:\Linux OS\Ubuntu 12.04 and Studio\ubuntustudio-12.04-dvd-i386.iso.
Eject = 1, Simulate = 0, BUP = 1, Pad tracks = 1, Close = 1, Overburn = 1, Swab = 0, Ignore size = 0, Immed = 0, Audio master = 1, Forcespeed = 0, VariRec (enabled) = 0, VariRec (value) = 0, Clone = 0.
Command line to run: "C:\Program Files\InfraRecorder\cdrtools\cdrecord.exe" -v dev=0,1,0 gracetime=5 -eject -sao driveropts=burnfree -pad -overburn speed=31 "/cygdrive/H/Linux OS/Ubuntu 12.04 and Studio/ubuntustudio-12.04-dvd-i386.iso"
> scsidev: '0,1,0'
> scsibus: 0 target: 1 lun: 0
> SCSI buffer size: 64512
> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: Warning: The DMA speed test has been skipped
> Cdrecord-ProDVD-ProBD-Clone 2
> 01
> 01a61 (i686-pc-cygwin) Copyright (C) 1995-2009 Jörg Schilling
> TOC Type: 1 = CD-ROM
> Using libscg version 'schily-0
> 9'
> Driveropts: 'burnfree'
> atapi: -1
> Device type : Removable CD-ROM
> Version : 0
> Response Format: 1
> Vendor_info : 'PHILIPS '
> Identifikation : 'DVD+-RW DVD8801 '
> Revision : '4D28'
> Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM
> Current: DVD-R sequential recording
> Profile: DVD+R/DL 
> Profile: DVD+R 
> Profile: DVD+RW 
> Profile: DVD-RW sequential recording 
> Profile: DVD-RW restricted overwrite 
> Profile: DVD-R sequential recording (current)
> Profile: DVD-ROM 
> Profile: CD-RW 
> Profile: CD-R 
> Profile: CD-ROM 
> Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd)
> Driver flags : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
> Supported modes: PACKET SAO
> Drive buf size : 655360 = 640 KB
> FIFO size : 4194304 = 4096 KB
> Track 01: data 1904 MB padsize: 30 KB
> Total size: 1904 MB = 975013 sectors
> Current Secsize: 2048
> Blocks total: 2297888 Blocks current: 2297888 Blocks remaining: 1322875
> Reducing transfer size from 64512 to 32768 bytes
> Starting to write CD/DVD/BD at speed 16 in real SAO mode for single session
> Last chance to quit, starting real write in 5 seconds
> Operation starts.
> Waiting for reader process to fill input buffer ... input buffer ready.
> BURN-Free is ON.
> Starting new track at sector: 0
CCore:ProcessEnded
Process exited with code: 254.
 
(the smilies did not appear in the program log)
 
I'm kinda dead in the water without a burned disk image. 
 
Anything I can do about it?
 
Thanks

---

### Post by Bashing-om on 2012-09-17
Suggestion: (as I am no longer windows wise)
1. Verify the .iso integrity:
                        [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. As you are d/l'n a DVD version...insure a quality DVD disk is utilized (cd's quality is less desirable).
3. Hate to be wasteful, but, burn another DVD on some other .iso to verify the writer is good.

Try the burn again (make sure burn as image not as data) ..and advise on results.
[INDENT][INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by JXR on 2012-09-19
Went on the network and copied the file to my wife's Win7 computer (re-checksummed) and tried Burning the iso from there. It was successful.
 
Still haven't found out if there's something wrong with my burner - it works fine with DVD Shrink and DVD Decryptor...but I think I'll let that go for now...I'm so eager to try Ubuntu...
 
Thanks for your help

---

