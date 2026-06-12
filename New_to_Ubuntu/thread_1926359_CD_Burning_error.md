---
title: "CD Burning error"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by aykoola on 2012-02-16
I'm using Oneiric and i can't burn CDs and DVDs on my system.  I used Brasero and K3b and none would work, it would show an error  every time somewhere near the 70% mark and the error would be something  like it can't access cdrom or something. Try to fix it through some  instructions on the forums but it wouldn't work still.
  Any help?
  I'm running 11.10 on a 64bit machine.
  Thank y'all in advance guys!

---

### Post by 23dornot23d on 2012-02-16
Is it the CD drive failing ..... can you burn ok using a different OS

The other thing is the discs .... are they good quality CD's

What is it you are trying to burn ..... ? (are you doing a copy of a CD, a ISO or DATA)

other than these - all I can think is to re-install k3b and brasero and try again posting the full error if it occurs again 

( do the following one at a time in a terminal to make sure k3b and brasero are not missing anything ....... and are uptodate )

[B]sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude reinstall k3b
sudo aptitude reinstall brasero[/B]


Take a screenshot of any errors .... or cut and paste them back here so we can see
more what it fully reports as the error ......

---

### Post by aykoola on 2012-02-16
Not working again:

"cdrecord returned an unknown error (code 254)

Sometimes using TAO writing mode solves this issue."

Any help?

---

### Post by aykoola on 2012-02-16
any1?

---

### Post by 23dornot23d on 2012-02-16
A google search turned up this ....

[https://www.google.com/search?client=ubuntu&channel=fs&q=cdrecord+returned+an+unknown+error+%28code+254%29&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=cdrecord+returned+an+unknown+error+%28code+254%29&ie=utf-8&oe=utf-8)

one of the things I found pointed to this but it is quite old ..... 2008

[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

But I am not sure if this still applies ....  could even be that you are burning at too high
a speed .......

Best I can do at the moment with the information you have given .... more information
and more chance of a good answer ......

[B]Try to find the error log ... that is generated too - and post it ....
[/B]
To give more information on your CD/Dvd drive ...... enter the commands below in a terminal

**sudo apt-get update**
[B]sudo apt-get install hwinfo

hwinfo --scsi

_____________________________

Then cut and paste the results back here .....

[/B]

---

### Post by Rtedmonston on 2012-02-18
I've been having this same issue for days and posted error logs and all here: [http://ubuntuforums.org/showthread.php?t=1926606](http://ubuntuforums.org/showthread.php?t=1926606) now I'm getting the same error as aykoola.
Trying to burn ISO's w/ k3b and it quit working recently after a major update to the Ubuntu kernel (3.0.0 -16) 3-4 days ago. I've tried re-installing k3b and Brasero to no avail, I can't burn anything without getting an error of some sort and wasting another blank disc ><, I can still burn fine under Windows though so it's not my drive. heres more info:

 [quote=acer@aspire] hwinfo --scsi
> hal.1: read hal dataprocess 2548: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: SCSI 400.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  Unique ID: KD9E.mkB+i3zwpgA
  Parent ID: w7Y8.A++qjDUok+B
  SysFS ID: /class/block/sr0
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GT30N"
  Vendor: "HL-DT-ST"
  Device: "DVDRAM GT30N"
  Revision: "1.01"
  Driver: "ahci", "sr"
  Driver Modules: "ahci"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-HL-DT-STDVDRAM_GT30N_KZGA1822803, /dev/disk/by-path/pci-0000:00:1f.2-scsi-4:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: DVD
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (SATA controller)
  Drive Speed: 24[/quote]

---

### Post by Rtedmonston on 2012-02-19
bump

---

