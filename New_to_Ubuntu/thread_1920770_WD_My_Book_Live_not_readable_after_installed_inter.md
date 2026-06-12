---
title: "WD My Book Live not readable after installed internally"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Zenereffect on 2012-02-05
I'm starting a new thread, since the subject of the last one no longer applies, but here's the link to it to see what's been going on...

[URL="http://ubuntuforums.org/showthread.php?t=1920025"]http://ubuntuforums.org/showthread.php?t=1920025
[/URL]
I've seen some other similar posts, but nothing I've tried so far has worked.

In short, here's the issue: I have a 2TB WDMBL (Wester Digital My Book Live).  The drive quit responding over the network, so I removed the drive from its case (it's an internal drive connected to a network card - see other post for more detail) and installed it inside my MacPro.  The drive is seen but is giving me errors when trying to access it.  When attempting to access it via the GUI of Ubuntu I get this message:

> Error mounting: mount: wrong fs type, bad option, bad superblock on  /dev/sdb4, missing codepage or helper program, or other error. In some  cases useful info is found is syslog - try dmesg | tail or so

Any suggestions are welcome! Please keep in mind I'm new to Linux, so an explanation of any commands you are recommending would be appreciated! Thanks!

---

### Post by Zenereffect on 2012-02-05
> **sudodus said:**
> How did you install gparted?

0. It is already there on the install CD or USB, when you run a live session.

1. ```
sudo apt-get install gparted
``` should do the trick. You  might have installed something not compatible. Take that away!
--
You must ask the [COLOR=Red]**moderators**[/COLOR] to change  the title of the thread, I think you cannot do it yourself. But an  alternative is to start a new thread with an appropriate title (and we  can continue there, hoping to attract someone with more knowledge about  your drive and problem).

I used option 1.

---

### Post by TeoBigusGeekus on 2012-02-05
What's the file system of the drive?
If it's an ext one, you could try an fsck on it.

---

### Post by sudodus on 2012-02-05
> **Zenereffect said:**
> I used option 1.
Which really should work. Anyway, try Gparted from a live session using your Ubuntu install drive! But I have not much hope that it will find more than [FONT="Courier New"]sudo fdisk -lu[/FONT]. That is why I suggested that you go for the disk repair tools.

---

### Post by Zenereffect on 2012-02-05
> **TeoBigusGeekus said:**
> What's the file system of the drive?
If it's an ext one, you could try an fsck on it.

Tried that and it froze in the process of a force rewrite.

Not 100% sure, but it might be ext4

---

### Post by Zenereffect on 2012-02-05
I started up using the install disk and tried running gparted with the same error: > cannot open display

I'll start working on your other suggestions in the meantime...

---

### Post by sudodus on 2012-02-05
> **Zenereffect said:**
> I started up using the install disk and tried running gparted with the same error: cannot open display

I'll start working on your other suggestions in the meantime...
I guess you can run other programs in graphics mode?!

Anyway, I think it is a good idea to get one of the ISO files to make a live CD or USB drive with testdisk and photorec.

---

### Post by Zenereffect on 2012-02-05
> **sudodus said:**
> I guess you can run other programs in graphics mode?!

Anyway, I think it is a good idea to get one of the ISO files to make a live CD or USB drive with testdisk and photorec.

Yeah, at the very least firefox is working

...setting up a testdisk CD now...

---

### Post by Zenereffect on 2012-02-06
I'm getting all sorts of errors when trying to analyze the drive in testdisk. Is that just confirming it has corrupted partitions or does that mean the disk won't be fixable? (It doesn't finish analyzing it before the errors crash the whole system - I can only imagine that means it's more than just a basic fix right?)

---

### Post by sudodus on 2012-02-07
It depends ***what*** kind of errors. It is hard to help with so vague information.

1. Have you checked if there is S.M.A.R.T. information on the HDD with problems? That can be checked with ```
palimpsest
``` We don't know yet if there are physical or logical errors. It is more likely logical errors, but I wouldn't say for sure. If there are physical errors, clone the readable content to another HDD with ddrescue!

2. At some point you should give up testdisk and try other tools, for example gpart and finally photorec. Gpart tried to do something similar to testdisk.

If the file data is there at all, photorec can recover it without partition tables and file systems.

---

### Post by Zenereffect on 2012-02-07
I'm getting a "cannot open display" message when I try running gparted or palimpsest from the VT, how do I fix that?

```
Script started on Tue 07 Feb 2012 09:28:34 AM MST
root@johnaspin-MacPro:/home# palimpsest 
Cannot open display:  
root@johnaspin-MacPro:/home# palimpsest & 
[1] 2139 
root@johnaspin-MacPro:/home# Cannot open display:  
 
[1]+  Exit 1                  palimpsest 
root@johnaspin-MacPro:/home# gparted 
 
(gpartedbin:2155): Gtk-WARNING **: cannot open display:  
root@johnaspin-MacPro:/home# exit 
exit 

Script done on Tue 07 Feb 2012 09:30:08 AM MST
```

---

### Post by sudodus on 2012-02-07
OK, so you have the same problem with palimpsest as with gparted. Maybe there is something wrong with gnome. Which version of Ubuntu are you running? 11.10?

Alternative 1. Try an older version, 10.04 LTS or 11.04 (download the ISO files and start live sessions and hope palimpsest and gparted will work in graphics mode.

Alternative 2. Use command line tools. See the following link for ***smartctl***

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

and you have already run ```
sudo fdisk -lu 
``` but it did not give that much information.

---

### Post by Zenereffect on 2012-02-07
I'll work on trying an older version then, cuz yeah, I'm working with 11.10 right now.  In the meantime, here's the output for
 ```
fdisk -lu
``````

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33          16+  ee  GPT
/dev/sda2              34    48828159    24414063   82  Linux swap / Solaris
/dev/sda3   *    48828160   976771519   463971680   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT
```Also ran:

```

smartctl -i /dev/sdb1
```with this output:

```

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-15-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA3420817
LU WWN Device Id: 5 0014ee 20568ff4e
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Feb  7 20:17:29 2012 MST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

I decided to open diskutility through the GUI and took a screen shot of the window:
[ATTACH]212256[/ATTACH]

---

### Post by sudodus on 2012-02-08
The diskutility is (or at least was) palimpsest. It works now :-) Anyway, you got the S.M.A.R.T. stated: ***there are a few bad sectors***. Select some other and more advanced smartctl command to get a better test of the disk status, if you wish. Look at the examples in
```
man smartctl
```If you have good luck, no important information was there. It might be the partition information that is bad, but your file data may still be OK and possible to recover. The bad sectors might not even be used at all, but we don't know that yet.

I don't like disks with bad sectors, and try to save the information to another drive as soon as possible. So I suggest that, if you want to get back as much as possible and get back the partition table, try cloning the drive using ***ddrescue***. And then try to repair the partition table on the cloned copy.
```
sudo apt-get install ddrescue
``` and read the excellent info pages to learn how to use ddrescue
```
info ddrescue
```

---

### Post by Zenereffect on 2012-02-12
I need to order a HD to perform ddrescue, so I'll do that and see what works out. Thanks for all your help so far and if I have more questions I'll post them, but it might take a week or so to get the hard drive and back to trying things out (I'm in school for engineering, so free time is usually sparse). You've certainly helped me learn a number of different recovery methods so far, so thanks again!!!

---

### Post by Zenereffect on 2012-03-01
So at this point I've started ddrescue.  It's not done and it's been running for about 3 days now (2TB -> 2TB).  There are quite a few errors it seems, but as long as I can tell it's still running should I be concerned that it's stuck in some sort of loop? It doesn't appear to be, but this seems to be taking longer than I would expect.

---

### Post by sudodus on 2012-03-01
Yes, I think you can tell, if the drives are working in a 'normal way'. It is hard to say exactly how long it will take, but I would definitely get tired of waiting. Maybe you can put the limit at one week.

Are you running something similar to one of the examples in [FONT=Courier New][SIZE=3]info ddrescue[/SIZE][/FONT] ?

---

### Post by Zenereffect on 2012-05-09
...mission failure...

I decided to call it quits after 2 weeks and haven't made any other attempts, but at this point I'm giving up anyway.  Thanks for all the help, I'm sure it'll come in handy with something else at some point anyway!!

---

### Post by Jeremyunbricked on 2012-09-15
This post has nothing to do with ubuntu but it will solve your problem. This is how i fixed mine.

Hi! I had a problem where my mybook live 2tb drive suddenly stopped working. To be honest, I was using it as a portable drive and was storing it away. When I took it out and plugged it back in to do a backup, the light when from blue to white to red and I tried everything in order to get it working. Everything the support site said and about 4 hours of messing around on the internet reading all these forums and trying everything suggested. Here is what I learned:

Solution: (I'm previously computer literate but less so now as I'm older and have wasted enough of my life with this crap)

Whatever file system this is it is not linux native ext2 or 3 or whatever, it is mac. It WILL NOT mount under ubuntu, which is what i'm running and will continually give all these bull$hit errors. when you access it eventually you will see all kind of .apple files. 

Easy fix. Open up your piece of junk WD mybook drive, pull it out, undo the nic card, buy the SATA to usb adapter cord or the docking port from best buy, take it to a friends house that has a windows system, use the linux file system reader from [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

install that, plug in the drive, when windows wants to format it hit CANCEL and run that program and voila there your files are. back em up however you can.

---

