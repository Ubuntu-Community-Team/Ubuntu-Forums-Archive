---
title: "What did this comand Do &quot;cdrecord blank=all dev-1,0,0&quot;"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by gordon33 on 2014-01-02
Hello All


What did this comand Do "cdrecord blank=all dev-1,0,0"  after I typed it in I got a long winded responce form the Termional.  That responce is pasted below:

```
gordon@gordon-desktop:~$ wodim -scanbus 
scsibus1: 
	1,0,0	100) 'PBDS    ' 'CDRWDVD DH-48C2S' 'ND11' Removable CD-ROM 
	1,1,0	101) * 
	1,2,0	102) * 
	1,3,0	103) * 
	1,4,0	104) * 
	1,5,0	105) * 
	1,6,0	106) * 
	1,7,0	107) * 
gordon@gordon-desktop:~$ cdrecord blank=all dev=1,0,0 
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits. 
WARNING: the deprecated pseudo SCSI syntax found as device specification. 
Support for that may cease in the future versions of wodim. For now, 
the device will be mapped to a block device file where possible. 
Run "wodim --devices" for details. 
Device type    : Removable CD-ROM 
Version        : 5 
Response Format: 2 
Capabilities   : 
Vendor_info    : 'PBDS    ' 
Identification : 'CDRWDVD DH-48C2S' 
Revision       : 'ND11' 
Device seems to be: Generic mmc2 DVD-ROM. 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr). 
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R 
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error 
CDB:  00 00 00 00 00 00 
status: 0x2 (CHECK CONDITION) 
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00 
Sense Key: 0x2 Not Ready, Segment 0 
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0 
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s 
wodim: No disk / Wrong disk! 
gordon@gordon-desktop:~$ 

```


Gordon

---

### Post by chkneater on 2014-01-02
looks like you need to do "sudo" in front of the command.  Permission was denied to raise the mem limits, usually because you need to be super user, IE 'sudo cdrecord blank=all dev-1,0,0' and add password.  Should work then.  I assume you're blanking the disk or trying to record to it?

---

### Post by gordon33 on 2014-01-02
Hello Chkneater

Yes I am trying to make a ubuntu start up disk.  I keep getting a the "wright to  disk " box withthe message " Please replace the disk witha supported CD or DVD".  A saw the command "cdrecord blank=all dev-1,0,0" on another fourm.  Will it help if I go back and use sudo?

Gordon33

---

### Post by gordon33 on 2014-01-03
I tried sudo   what does all this mean?


gordon@gordon-desktop:~$ sudo cdrecord blank=all dev-1,0,0
[sudo] password for gordon: 
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PBDS    '
Identification : 'CDRWDVD DH-48C2S'
Revision       : 'ND11'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: No such file or directory. Cannot open 'dev-1,0,0'.
gordon@gordon-desktop:~$

---

### Post by chkneater on 2014-01-03
If you're making an Ubuntu install disk then you need to have a DVD drive and disk.  From what I see it looks like you have a CD drive, am I correct?

---

### Post by gordon33 on 2014-01-03
Hello Chkneater


When I open the disc drawer on the right printed is "DVD" and below that is "ROM".  On the right printed is "Compact DISC Rewriteable, and Ultra Speed".  I have to guess that means the disc drive at least can read a DVD.  

When I try to write to the disk I get the "Write To Disk" box with a message "Please replace the disk with a supported CD or DVD."  

I have been think it may be a read only disk drive.  I thought I could write to a disk but with all the problems I have been having I am unsure of every thing.

I have not used this computer much at all.  That is why I am so unsure of its disk drive.

Gordon

Gordon

---

### Post by mc4man on 2014-01-04
that drive reads/writes cd's but only reads dvd's

---

### Post by andrew.46 on 2014-01-04
> **gordon33 said:**
> I tried sudo   what does all this mean?


```
gordon@gordon-desktop:~$ sudo cdrecord blank=all dev-1,0,0
[...]
wodim: No such file or directory. Cannot open 'dev-1,0,0'.

```


I cannot test this as I do not use the debian fork wodim but you have made a typo with your command, try:

```

sudo cdrecord blank=all dev**[COLOR="#FF0000"]=[/COLOR]**1,0,0

```

Mind you this command will only blank the disk before writing and looks like you need to address the cd vs dvd issue as well...

---

### Post by gordon33 on 2014-01-04
Hello Mc4man and Andrew46

Thank you that explains the message when I put in the DVD.  I will skip the command "sudo cdrecord blank=all dev=1,0,0" until I get a CD with the capabilities to make a ubuntu start up disc.

Gordon

---

### Post by mc4man on 2014-01-04
> **gordon33 said:**
> Hello Mc4man and Andrew46

Thank you that explains the message when I put in the DVD.  I will skip the command "sudo cdrecord blank=all dev=1,0,0" until I get a CD with the capabilities to make a ubuntu start up disc.

Gordon
You could probably fit current iso's on 90 min cd's (800Mb) but keep in mind that not all drives support such media. Does your setup support usb boot?

---

### Post by gordon33 on 2014-01-04
Hello Mc4man

I beleve it does support boot option from a USB .

The boot options from Bios are:

CD-Rom Boot   Enabled
Floppy Boot  Enabled
Internal Network Adapter Boot  Disabled
Boot Order

Boot Order
USB Diskette on Key/USB Hard Disk
Internal CD/DVD ROM Drive
Notebook Hard Drive
   Network Adaprer

I am going to be working on the laptops problem from Post:        [http://ubuntuforums.org/showthread.php?t=2197574](http://ubuntuforums.org/showthread.php?t=2197574)

Gordon33

---

