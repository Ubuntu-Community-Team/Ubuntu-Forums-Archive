---
title: "Problem mounting windows partition"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by spaceship.rodeo on 2008-08-10
Whenever I try to mount my windows partition, it keeps giving me this error:
```
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
I don't know what it means?  Here's my fstab output:
```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       60167   483227167+   7  HPFS/NTFS
/dev/sda3           60168       60787     4980150   db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

I really need to get my stuff of the windows partition and would appreciate any help.

---

### Post by Pro-reason on 2008-08-10
It looks like that partition is corrupt.  Are you able to boot into Windows?

---

### Post by spaceship.rodeo on 2008-08-10
Uh, no.  It won't even boot up windows, but before that happened, it would give me a BSOD as soon as I logged into a profile.

---

### Post by tinker312 on 2008-08-10
Hey Spaceship.Rodeo, 

You may be able to fix your windows installation by booting to your windows disk, going to the recovery console, and typing chkdsk /p /r  

I wouldn't mess with the Master Boot Record if you run a dual boot machine.  It sounds like you do.  If the NTFS partition is corrupt chkdsk MAY fix it . . .and then you should be able to mount the drive successfully in Ubuntu.   

There is a legendary computer guru named Steve Gibson who sells a product called SpinRite . . . It's probably one of the best hard drive recovery applications out there.  I think there are freebies that you could try as well.

---

### Post by spaceship.rodeo on 2008-08-10
See, that's the kicker here.  I tried putting in my windows cd to repair the messed up file, but as soon as everything's done loading, it gives me a bsod.  That's the thing I don't understand, I have never heard of this happening.

---

### Post by tinker312 on 2008-08-10
Ok, if you have a functional Ubuntu system and a hard drive with bad sectors or "corrupt" then this app written for debian may help you.  

[http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.htmlprint/](http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.htmlprint/)

I would try this if if I wasn't going to lose years worth of essays or a couple 20 gigs of media I don't have backed up.  If your real worried you may want try ntfs specific recovery app like one from Gibson.  

Also the Knoppix live cd is pretty awesome, i used it at work to ssh into broken windows computers and save peoples files. Here is a tutorial on hard drive recovery using Knoppix.  

[http://www.google.com/notebook/public/13391255910222927091/BDSe5QgoQ57vTvvki](http://www.google.com/notebook/public/13391255910222927091/BDSe5QgoQ57vTvvki)

I haven't personally tested this stuff but I offer it as a place to begin.  Good Luck . . .

---

