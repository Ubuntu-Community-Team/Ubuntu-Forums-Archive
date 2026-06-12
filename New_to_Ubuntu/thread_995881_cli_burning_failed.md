---
title: "cli burning failed"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by muted1987 on 2008-11-28
hey all i just used this command to burn an iso and got a long winded error guessing something with my drive although it reads discs okay even copied ones. any hel p appreciated, oh and how do i specify write sppeed thx in advance.

code used =    cdrecord dev='/dev/scd0' -v xxx123.iso

output recieved

[HTML]wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'DVDRW   '
Identification : 'IDE 16X         '
Revision       : 'A091'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1409024 = 1376 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  4418 MB        
Total size:     5074 MB (502:46.06) = 2262455 sectors
Lout start:     5075 MB (502:48/05) = 2262455 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 36041
Speed set to 22160 KB/s
Starting to write CD/DVD at speed  17.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 11.377s timeout 60s
wodim: OPC failed.
Writing  time:   11.414s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.[/HTML]

---

### Post by lemming465 on 2008-11-30
*cdrecord --help* will show you a whole bunch of possible command line options.  To burn at 4x audio speed use an argument *speed=4*  If slowing the burn down doesn't fix the > OPC failed double check that the media you are trying to burn is compatible with your drive.

---

### Post by Xiong Chiamiov on 2008-11-30
Is there a particular reason why you're using cdrecord, rather than a graphical option like gnomebaker, like for educational purposes, or you don't have X installed?

---

### Post by muted1987 on 2008-11-30
> **Xiong Chiamiov said:**
> Is there a particular reason why you're using cdrecord, rather than a graphical option like gnomebaker, like for educational purposes, or you don't have X installed?

yes using gui's are good but in the long run they are just a pretty screen for the CL and im not afraid of trying anything ne and would like to learn to get things done from the CL unless i have to use a gui

---

### Post by andrew.46 on 2008-12-02
Hi,

Ubuntu includes cdrdao which is great for copying audio cds. I have a special interest in this as I have written a much-neglected guide that details its use:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

(An issue with Ubuntu is of course that when you ask for 'cdrecord' you actually get 'wodim'. I note with some interest that the 'real' cdrecord is on offer here:

[https://launchpad.net/~ubuntu-burning/+archive](https://launchpad.net/~ubuntu-burning/+archive)

although I should say up front that I not tried this archive myself.)

Anyway I would be flattered if you would try my cdrdao page and make any suggestions for improvements. I have yet to burn a coaster with the technique described there.

  Andrew

---

