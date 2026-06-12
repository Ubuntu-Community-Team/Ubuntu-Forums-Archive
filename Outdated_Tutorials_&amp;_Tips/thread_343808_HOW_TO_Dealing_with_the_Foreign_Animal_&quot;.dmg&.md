---
title: "HOW TO: Dealing with the Foreign Animal &quot;.dmg&quot; (.dmg to iso burning)"
date: 2007-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by EvanPMeth on 2007-01-22
So I ran into a predicament the other day when trying to burn a .dmg file on Linux. At first I thought to myself, why does there need to be another cd/dvd image format. Its already hard enough keeping track. So i did my little routine when finding something new I, instantly go to my life partner Google, buddy ole' pal. And was hard pressed to find a concrete solution. Looking for about 2 minutes I became frustrated. And then i struck gold, with handy little perl script referenced by this thread:
[COLOR="DarkOrange"] [ dmg2iso error]("http://ubuntuforums.org/showthread.php?t=128833&page=2")[/COLOR]
 and available @:
[COLOR="Blue"][http://blinkenlights.ch/gnupod/dmg2iso.pl](http://blinkenlights.ch/gnupod/dmg2iso.pl)[/COLOR]

 So I decided to right a little How to on this subject:

1.) Download the script [COLOR="Blue"][dmg2iso.pl]("http://blinkenlights.ch/gnupod/dmg2iso.pl")[/COLOR]
2.) Install dependencies that were not present in my situation:
```
sudo apt-get install libcompress-zlib-perl
```
3.) Run the script and cross your fingers:
```
perl dmg2iso.pl DMGFILE.dmg NEWISOFILE.iso
```
  
Burning the new ISO image:
              IF DVD:
                           1.) Install service required for writing to the dvd:
                                 ```
sudo apt-get install &#8216;dvd+rw-tools&#8217;
```
                           2.) Right to the DVD:
                                 ```
growisofs -Z /dev/dvd= path/to/NEWISOFILE.iso
```

               IF CD:
                            1.) Install service for burning cds:
                                 ```
sudo apt-get install cdrecord
```
                            2.) Find the SCSI ID of your cd-burner w/ the following comand:
                                  ```
cdrecord dev=ATA: -scanbus
```

                                 ```
Cdrecord-Clone 2.01a34 (i686-pc-linux-gnu)
Copyright (C) 1995-2004 Jrg Schilling
scsidev: 'ATA:'
devname: 'ATA'
scsibus: -1 target: -1 lun: -1
Warning: Using badly designed ATAPI via /dev/hd*
interface.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.8'.
scsibus1:
 ***1,0,0** 100) 'SONY' 'CD-Writer' '1.0g'*
 1,1,0 101) *
 1,2,0 102) *
 1,3,0 103) *
 1,4,0 104) *
 1,5,0 105) *
 1,6,0 106) *
 1.7.0 107) *

```

                              3.) Then burn it, but replace **1,0,0** with yours, and set the speed to your liking:
                                     ```
cdrecord -v -dev=ATA:**1,0,0** speed=4 NEWISOFILE.iso
```

Hope thats helps any stranded sole out there.

-EvanPMeth

Sources:
[http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)    ---  vultur
[http://ubuntuforums.org/showthread.php?t=128833&page=2](http://ubuntuforums.org/showthread.php?t=128833&page=2)   --- nalle
[http://blinkenlights.ch/gnupod/dmg2iso.pl](http://blinkenlights.ch/gnupod/dmg2iso.pl)  --- nalle
[http://www.cyberciti.biz/tips/how-do-i-write-cd-at-debain-linux-command-prompt.html](http://www.cyberciti.biz/tips/how-do-i-write-cd-at-debain-linux-command-prompt.html)  ---   LinuxTitli
[http://www.cyberciti.biz/tips/howto-linux-write-burn-data-to-dvd-or-dvdrw.html](http://www.cyberciti.biz/tips/howto-linux-write-burn-data-to-dvd-or-dvdrw.html)  ---  LinuxTitli

---

### Post by bodhi.zazen on 2007-02-04
Nice How-to

This thread has been added to the UDSF wiki.

[.dmg_to_iso_burning](http://doc.gwos.org/index.php/.dmg_to_iso_burning)

---

### Post by Achetar on 2009-02-10
hey, this is an old thread, but i need some help. I have a 6.5GB dual-layer DVD .dmg file. The dmg2iso.pl script errors out like so:
```

dmg2iso v0.2a by vu1tur (vu1tur@gmx.de)

reading property list...found 5 partitions
decompressing:
partition 0
partition 1

Conversion failed. File may be corrupted.

```I've done md5 and sha1 checks and the source file is fine. Any clues how to do it?

Nvm, i found the solution! Search through the forums a bit more and you can find it too!! (jk) The perl version of dmg2iso won't work on 6.5GB images. For that you need the java version of dmgextractor.

---

### Post by NicePics13 on 2009-05-05
dmg2iso has been superseded by dmg2img - it can handle files >4GB
[http://vu1tur.eu.org/tools/]("http://vu1tur.eu.org/tools/")

---

### Post by scarf on 2009-12-31
i used dmg2img and k3b doesn't recognize the resulting img.  is the only way to burn using growisofs?

---

### Post by huntz on 2010-08-10
If you can't burn the image with K3B, you can install Brasero and rename the file extension from IMG to ISO.

Brasero will recognise the image and let you to burn the disc.

;)

---

