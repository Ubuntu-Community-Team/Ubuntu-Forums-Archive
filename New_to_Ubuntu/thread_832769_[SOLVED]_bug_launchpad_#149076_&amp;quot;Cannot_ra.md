---
title: "[SOLVED] bug: launchpad #149076: &amp;quot;Cannot raise RLIMIT_MEMLOCK limits&amp;quot;"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by simontaylor on 2008-06-18
Please help: Audio CD will not write in Gnomebaker, K3b, Gnome writer, Serpentine or Brasero since updating to Ubuntu Hardy Heron 8.04. Readout / output / bug report from all of these apps have the following in common:

> Cannot raise RLIMIT_MEMLOCK limits 

Winner with solution receives matching set of 14 (+) highly attractive but inedible, inaudible and entirely useless plastic coasters.

And many many many thanks, possibly in perpetuity. And the thanks from the over 22 reported cases of the same bug in this forum alone.

Steps taken so far and links to literature are detailed in thread 

> K3b cdrecord vs. cdrdao? conflict? (Brasero fails too) 

As the original fly said in the original web:

Help me!

best,

simon

---

### Post by simontaylor on 2008-06-18
contents of /etc/security/limits.conf 

> #*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file

---

### Post by editrix on 2008-07-03
Hi Simon:

I found your post when researching the same problem. Did you ever find a solution?

At least I've bumped this.

---

### Post by simontaylor on 2008-07-03
hi editrix,
whether a cloak or conspiracy of silence, I don't know. But no, no clear solution has appeared. Many work-arounds and "I just re-installed and had no problem" or "burning at certain speeds, with certain weather conditions, punching the keys with a friendly thought, if I stand on one leg and my software does too"... etc. That is, compromise more common. 

thanks for the bump. We'll see...

best,
simon

---

### Post by Jingo on 2008-07-16
Having this problem too!

The wierd thing is, I burned a data cd just 2 weeks ago. Today nothing works!?

Any of the resent updates causing this troubles?

---

### Post by mc4man on 2008-07-16
Can either post a log from Brasero,k3b or maybe a dmesg | tail right after a failed burn?
do you have any lines that look similar to this in your logs (k3b, brasero, ect)
> Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 


---

### Post by editrix on 2008-07-21
> **mc4man said:**
> Can either post a log from Brasero,k3b or maybe a dmesg | tail right after a failed burn?
do you have any lines that look similar to this in your logs (k3b, brasero, ect)

Hi mc4man:

I'm really, **really** sorry I somehow lost track of this thread, especially since you're the first person I've found who suggested anything like the Sense messages. And also because I had kept the K3B log for a while, but must have deleted it because I can't find it anymore.

Needless to say, I'm reluctant to produce yet another coaster just to engender the error message, but I will if I have to--just need to go out and buy more CDs.

In the meantime, I'm posting here
1. To bump the thread so I can find it again
2. To bump it so maybe someone else with the same problem can post their logs or dmseg
3. To ask you why you're asking about those specific Sense messages--i.e., what would be the issue if that was the message returned?

---

### Post by editrix on 2008-07-22
Okay, I tried burning with Brasero, which is supposed to burn anything. It didn't. I got the "unknown error" message. I tried attaching the log, but was told it's too long. So I had to zip it. Sorry for the extra hassle.

Unfortunately, I forgot about dmesg | tail and had to reboot in order to eject the madly spinning CD, since there was no icon on my desktop and no way of ejecting it--I've had this issue each time, which is why I'm reluctant to do too many tests--along with the coaster collection. However, I did read dmesg0 right after rebooting, and here's some stuff that may be relevant:
> 
 22.070846] ata2.00: ATAPI: CW078D ATAPI CD-R/RW, V150E, max UDMA/33
[   22.070877] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0040, max UDMA/33
[   22.242458] ata2.00: configured for UDMA/33
[   22.414103] ata2.01: configured for UDMA/33
[   22.414270] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800AB-22CB 04.0 PQ: 0 ANSI: 5
[   22.415463] scsi 1:0:0:0: CD-ROM            CyberDrv CW078D CD-R/RW   150E PQ: 0 ANSI: 5
[   22.422060] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8161B 0040 PQ: 0 ANSI: 5
[   22.424677] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   22.425353] eth0: RealTek RTL8139 at 0xc800, 00:40:ca:3b:c5:5b, IRQ 17
[   22.425357] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   22.443904] Driver 'sd' needs updating - please use bus_type methods
[   22.444018] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.444035] sd 0:0:0:0: [sda] Write Protect is off
[   22.444038] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.444062] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.444123] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.444137] sd 0:0:0:0: [sda] Write Protect is off
[   22.444140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.444162] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.444168]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.466293]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[   22.489799] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.498248] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.498275] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   22.498296] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   22.501248] sr0: scsi3-mmc drive: 4x/40x writer cd/rw xa/form2 cdda tray
[   22.501257] Uniform CD-ROM driver Revision: 3.20
[   22.501337] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   22.524382] sr1: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[   22.524459] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   22.653600] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000516000052a044]
[   23.180181] Attempting manual resume
[   23.180187] swsusp: Resume From Partition 8:5

I don't see anything in dmesg or dmesg0 that looks like a brasero or wodim error. Then again, I'm not sure what to look for. But that 
> 
Driver 'sd' needs updating - please use bus_type methods  sounds interesting. What the heck does it mean?

PS: I was not trying to copy a CD, but to burn from my hard drive.

PPS: Now I know why they call it "burning." That CD was HOT when I finally got it out.

---

### Post by mc4man on 2008-07-22
@ editrix
What i was referring to I don't think applies here, (if anywhere, was just a thought).
While glancing through those endless logs on launchpad i noticed a fair number of posters had the error lines noted previously. With that error I'd assume data transfer issues and would take a look at the hardware itself. (position on cable, jumpers, using a 40 wire ide cable instead of 80 wire).

In your case it appears you have things set up fairly well, the cd burner is in a master position to the dvd reader and in any event it's configured for UDMA/33 which a 40 wire should suffice. (though if you had an 80 wire available I wouldn't hesitate to try, in which case if you're jumpered to cable select (cs) change to master/slave)

As far as Cannot raise RLIMIT_MEMLOCK limits, I may be misreading this but i don't see this as the major issue. For one it's a warning not an error. It seems to imply a failed attempt to raise the limit on memory 'locked' for exclusive use during the burn, ie. the ram buffer.
It shouldn't prevent the burn from taking place and in most cases wouldn't even effect the burn quality unless the buffer kept emptying and the burner was pausing to allow it to fill. 
I guess there's a possibility these burning apps will fail if they can't raise the buffer, seems sketchy though, maybe it's because as a user there is no limit to raise. If I run 
ulimit -m | grep 'limit'  it returns 'unlimited' (possibly wrong way to look at that ?)


I would think the sense errors you do have are involved, I just don't know what to make of them. In my case while I never use any of the linux ui apps for my burning needs, I have tested alot of them for various types of burns. With the exception of 2 occasions the burns started and completed without incident. Out of those only 2 or 3 had usability issues (IIRC they were a dvd video and data dvd). (seems to be the way at times - I have no use for these apps and they work 'ok' here, you want to use them and can't)

I did notice your particular drive has more than a handful of reported similar problems which may not be encouraging as far as finding a solution.

I did just try a audio cd burn with brasero (copy from cd in other drive) and it worked fine, maybe 8-10 min. start to finish. What i was looking for was the log, can't find it anywhere. Is it stored in some obscure place or do you need to do something to have one created?

If you want we could test your drives performance by using an app in wine, let me know.

---

### Post by editrix on 2008-07-23
mc4man, I have been all over the web looking for answers, and this is the first time I've understood *anything.* So I thank you for using English I can understand.

I'm certainly not the only one who can't burn CDs, but I have no idea if everyone has the same problem, or it's all different problems. Yes, I've seen the issues with my burner, but it must be a pretty obscure burner to have found so few posts about it in comparison with all the "can't burn a cd" posts. And this box is an HP, not known for using crappy hardware (although I grant it's possible).

I can copy stuff from CD to my hard drive, and I can extract music tracks from a CD to the hard drive, so I don't understand why it would be a hardware issue. To me, the thing either works or doesn't, but ...

> If I run ulimit -m | grep 'limit' it returns 'unlimited'

Same here.

> (possibly wrong way to look at that ?)

Why?

> I did just try a audio cd burn with brasero ... What i was looking for was the log ... do you need to do something to have one created?

Yes, you have to have a burn fail. That is, the log showed up because the burn failed. I wouldn't know what would happen with a successful burn :-(

I'm sorry if I'm asking too many questions, but this is a big issue for me. I'm on dialup, which means doing any research takes forever, and I'd really like to copy all the programs and updates I've downloaded onto CD so I can reinstall them if I need to.

> If you want we could test your drives performance by using an app in wine, let me know.

Then I'd need a Windows CD burning app, no? I don't have one. Nor Wine; although, obviously, I can get that.

PS: A bit of history: I was gifted with this machine from someone who bought a new one. It had XP installed and although I left it on the HD, I reduced the partition size to minimal--less than 400MB free on it, and no idea if it will even work. I've never logged into it--forgot I even had it. I don't see a CD burning app there, but I could, I suppose, download a trial version of some program and see if the burner works there. Except I'm pretty sure it does. Unless something got damaged in transporting the box from the friend's place to mine ...

PPS: I've never used XP. No idea how to set up the modem, etc. to download, and no idea of the learning curve.

PPPS: Another possibility is to install Dapper (my previous release on another, much slower box) and try dual booting with it, since Dapper used cdrecord and not wodim. All these CD burning bugs began with Gutsy, I think. However, I doubt I'd have room for Dapper until I get all the downloaded *.deb packages off my HD :-(

---

### Post by sydbat on 2008-07-23
This really could be a hardware issue. Your last post tells me that the whole box is old (how old?). I recently had to replace my DVD burner (this cleared up my burning problems) because it would no longer recognize blank DVD's...in either Hardy or XP...and it was less than 3 years old. It does happen.

---

### Post by editrix on 2008-07-23
[QUOTE=sydbat;5442136]This really could be a hardware issue. Your last post tells me that the whole box is old (how old?).{/QUOTE]

Not as old as the box I had before :-)

It's maybe 5 years, I don't really know. Needless to say, I'm reluctant to buy hardware if it's a software problem, but I do still have the old box with a working CD burner on it. Would have to haul it out of storage and find a hardware geek to take out the burner and put it in the new(er) box, so it's kind of a last resort thing.

Thing is, if I weren't finding so many bugs about CD/DVD burning when researching, I'd be more inclined to think it was hardware, too.

---

### Post by simontaylor on 2008-11-09
I hung out for months til Ibex landed. K3b seems (!HOPE!) to be working. I'm surprised there was not more outcry about the cdrecord clash.

---

### Post by editrix on 2008-11-10
Hi Simon:

Thanks for posting this, because the "conspiracy of silence" seems to be continuing.

I'm reluctant to move to Intrepid because a) I don't want to exchange one set of bugs for another, and b) I'm on dialup, and downloading all those programs again ... :-(

Anyway, could you please tell us which version of wodim and cdrkit you have now? I've been monitoring this as best I can, but there seems to be very little info out there. I'm 99% sure, but only 99% that the problem's with wodim and/or the other programs in cdrkit.

---

### Post by Nikos_M on 2008-11-11
By the description of the problem, this is not hardware related since it is caused by the RLIMIT_MEMLOCK. This limit is the maximum amount of memory (applies for the "unprivileged" user) that the user can lock in RAM (with mlock). It is not the amount of malloced space! The space that is reserved through malloc CAN be swapped out (to disk lets say) by the operating system when this is needed. The mlock keeps the amount of memory on RAM (actual hardware).

Now the solution to this (as I have no idea which part of the applications is causing this) could be to run the application as root (root does not have restrictions with RLIMIT_MEMLOCK). The other is to replace cdrdao/cdrecord with another version as it "seems" that the problem resides somewhere in there.

Otherwise if someone feels up to the task (and have some experience with this) he can always try to see where this happens using strace/ltrace. Good luck.

---

### Post by simontaylor on 2008-11-11
Re: versions of wodim & cdrkit - please refresh my memory on how to find out which versions I'm using. I in't messing with nothin that in't broke - which so far it has not appeared to be with 8.10.

Better: what has 8.10 done with the cdrdao/cdrecord software schism? What version/s come as standard?

Best,
Simon

---

### Post by editrix on 2008-11-12
Hi Simon:

I always get lazy and use Synaptic. It tells you what version of the program is installed. Or you can, in the terminal:

```
apt-cache show program_name | grep Version
```

Substitute the name of the program for program_name.

But double-checking, I see cdrkit isn't listed as a program on its own. As I understand it, there used to be something called cdtools, which included cdrecord, mkisofs and some other stuff. And, also if I understand it, that has been replaced by cdrkit, which included the buggy wodim and perhaps other buggy programs.

For several reasons, I do NOT want to use Intrepid--especially if the CD burning issue hasn't been fixed for me. But also, as I understand it, the problem could lie elsewhere than wodim et al. So the first step is to see if wodim's been fixed. I assume if the version number is different, something's been done to it. But with all my tracking of this issue, I haven't yet seen anything about it being fixed.

> I in't messing with nothin that in't broke - which so far it has not appeared to be with 8.10.

You've been lucky. But I'm not asking you to "mess" with anything :-)

> Better: what has 8.10 done with the cdrdao/cdrecord software schism? What version/s come as standard?

Oh yeah. Forgot about cdrdao--although I think the real issue is wodim/cdrecord. The versions that come as standard--standard for Ubuntu, at any rate--is whatever is installed on your system. And from my reading, the schism will not be healed any time soon.

---

### Post by simontaylor on 2008-11-12
ok let's see what we got on a simple synaptic search for wodim:
> 
wodim         9:1.1.8 1ubuntu1 
cdrkit-doc    9:1.1.8 1ubuntu1
cdw           0.3.3-2
genisoimage   9:1.1.8 1ubuntu1
cdrdao        1:1.2.2-16

a search for cdrecord shows that it's all KDE now - cdrecord itself not marked. And > cd+dvd-rw tools 7.1-2ubuntu1

another curious point. I recall when K3b ceased to proceed in 8.04 going through all the dependencies and finding Red Hat - think it was the cluster manager, cman. 

On upgrade to 8.10 cman played up - libfence3 had to be removed in a swift response apt-get remove motion.

My in't broke line is me being superstitious.

Best,
s.

---

### Post by editrix on 2008-11-14
Hi Simon:

Thanks for the info. It sent me on a goose chase--not entirely wild, because I discovered a couple of posts that gave me other possible causes and cures for the problem. If they don't work, I'll probably try installing the later versions of wodim, genisoimage and cdrdao, if that's possible.
> another curious point. I recall when K3b ceased to proceed in 8.04 going through all the dependencies and finding Red Hat - think it was the cluster manager, cman. 

Red Hat? Sorry, I'm not following. I don't have cman installed, nor do I know what a cluster manager does :-(

> On upgrade to 8.10 cman played up ...

Was it installed by default? I only ask because, maybe it should have and that caused the problem :confused:
> 
My in't broke line is me being superstitious.

Oh, how well I understand that!

Hope I'm not driving you crazy with these questions.

---

### Post by Headstand on 2008-11-21
Hey all,

So far found no solutions, but I've found tons of people having this same problem. Ive been working on it for a few days now. 
Heres my results from both music and image burning:

K3B: Image Burn w/TAO
unable to fixate
cdrecord has no permission to open the device

K3B: Music Disc w/TAO
unable to fixate
cdrecord has no permission to open the device


Brasero: Image Burn
The image does not seem to be a proper iso9660 file system.

Brasero: Music Disc
Program freezes when I try to add mp3 file

---

### Post by Headstand on 2008-11-21
Heres my debug output:

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-8-generic
Devices
-----------------------
HP CD-Writer+ 9300 1.0c (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

TOSHIBA DVD-ROM SD-M1612 1004 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'CD-Writer+ 9300 '
Revision       : '1.0c'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 22093 kB/s 125x CD 15x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
Track 01: data     0 MB         padsize:  236 KB
Track 02: data   589 MB        
Total size:      677 MB (67:07.89) = 302092 sectors
Lout start:      677 MB (67:09/67) = 302092 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 57756
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of    0 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:    5.106s
Average write speed 802.1x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.019s timeout 480s
cmd finished after 0.019s timeout 480s
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    0.022s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=10 -tao -eject /usr/bin/cdrecord -data -tsize=301638s - 

BUMPAGE!!

---

