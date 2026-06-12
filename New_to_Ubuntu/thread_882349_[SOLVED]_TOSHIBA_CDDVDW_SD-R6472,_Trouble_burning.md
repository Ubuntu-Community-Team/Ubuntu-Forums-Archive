---
title: "[SOLVED] TOSHIBA CD/DVDW SD-R6472, Trouble burning"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-08-06
Hey

Writing data cds, using Brasero and Gnomebaker.  Having to make iso's first... cant burn on the fly.

Lost a few cd's along the way, just wondering if there was a better software for Ubuntu.  Have looked online via google searches, and most cd writing packages I have found are for SuSe, Redhat, etc and not for Ubuntu.

Nero worked great for me under XP.  Is there anything similar?  Is there a way to check to see if my drive is supported?

Thanks

---

### Post by eightmillion on 2008-08-06
Have you tried K3B? You can install it via synaptic.

---

### Post by SonOfOdin on 2008-08-06
Hey

I havent tried it, but I will :)

This is the type of error I get...

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Speed set to 1411 KB/s
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 0F 00 00 0F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 30720
cmd finished after 0.000s timeout 40s
Writing  time:  204.526s
Average write speed  22.0x.
Fixating...
Errno: 0 (Success), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 480s
cmd finished after 0.000s timeout 480s
wodim: Cannot fixate disk.
Fixating time:    0.005s
wodim: fifo had 10878 puts and 10878 gets.
wodim: fifo was 470 times empty and 5 times full, min fill was 0%.

Strange thing is I can burn an an iso to disc - not the extracted image, just the iso itself...  ie when I open the cd after burning it gnomemaker.iso is there, and not the files themselves.  I cant get an image to burn either.

Edit: Just had a look at K3B - this is KDE, I am running pure gnome...  is this going to cause me troubles later on if I install K3B?

---

### Post by SonOfOdin on 2008-08-07
K3B!!!  What a cool program.

So far so good.  Just made a data cd!  Never thought I'd be so excited about using a burner for the first time again :)

So, another reason why I dont need M$ :guitar:

Thanks for your help 8Mill,

This topic is toast.

---

