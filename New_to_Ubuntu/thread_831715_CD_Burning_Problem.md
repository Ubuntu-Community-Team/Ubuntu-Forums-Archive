---
title: "CD Burning Problem"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-17
I am trying to burn a disc, and it gets burn fine, after i put it back in the tray and check it, its all blank.

I have tried it using K3B, nautilus burn://, Brasero, and Gnome Baker...
Have tried with the kernel -19 and -16. Using Ubuntu 8.04LTS.

and when i tried to burn the CD using Gnome Baker, i got:
```

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-861H '
Revision       : '1.50'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1411 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Writing  time:  137.222s
Average write speed   7.8x.
Min drive buffer fill was 97%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 15 12 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.466s timeout 480s
cmd finished after 4.466s timeout 480s
Fixating time:    4.493s
wodim: Cannot fixate disk.
wodim: fifo had 2452 puts and 2452 gets.
wodim: fifo was 0 times empty and 2244 times full, min fill was 97%.
BURN-Free was never needed.

```

---

### Post by simontaylor on 2008-06-17
hi shoaibi,
here's what I posted earlier for the same problem on a thread I initiated ... 
"K3b cdrecord vs. cdrdao? conflict? (Brasero fails too)"

OK, so this is a confirmed bug: #149076 Launchpad, first reported on 2007-10-04  by  hendrikwout.

here's the link: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076")

And some observations thereon:

> Copying my post from bug #178808, which is probably a duplicate:

> OK, I tried the fixes mentioned at:
[http://linux-ata.org/faq,html#combined](http://linux-ata.org/faq,html#combined)

...

> Adding kernel parameters is not for the newbie,the problem exists elsewhere and should be fixed elsewhere. Adding the kernel parameter should be viewed as a workaround, so the bug should probably not be closed, just re-pointed to wodim or wherever the bug actually lives.



> Same problem in 8.04. combined_mode=ide did the trick.

> I hope to see some progress on this issue soon as it seems to be a fairly common issue. There a lot of duplicate bugs out there describing basically the same thing "/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'" perhaps the description should be changed to something reflecting this? "I can't write a cd" is pretty generic and not particularly helpful for identifying this bug accurately.

Separate cases of the same bug relate to Kubuntu and Ubuntu, Feisty, Gutsy and Hardy.

Now, I don't understand the fixes mentioned, possibly because I am a newbie and ought not to be messing with the kernel?

The solution mentioned above is to go to libATA FAQ where we read:
     
> * Recommended (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".

* Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.

* Disable libata (CONFIG_ATA) entirely, and enable CONFIG_BLK_DEV_IDE_SATA.

* (newer choice, with less field testing) Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.


So can somebody please help me out?

(other possible fixes: dpkg-statoverride ??)

so, shoaibi, give me a yell if you make any headway.

thanks,
simon

---

### Post by shoaibi on 2008-06-17
some links are broken. atleast that linux ata one....
isnt there a simple solution???

---

### Post by simontaylor on 2008-06-17
hi again,
that link should redirect to [http://linux-ata.org/faq.html]("http://linux-ata.org/faq.html")

Yes, there are case-specific sticking-plasters, like lowering burn speed (x 4 for Brasero,in one case) or adding usr to group (in one case) or doing a chown and a chmode ---  which I don't know enough about to investigate in my case --- but the deeper source of the problem seems to be ATA / RAID / COMBINED issues, i.e. kernel.

best,
simon

---

