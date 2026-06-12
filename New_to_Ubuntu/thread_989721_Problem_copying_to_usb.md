---
title: "Problem copying to usb"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by themoose on 2008-11-21
I somehow crashed my desktop.  I'm using Gutsy.  When I boot up it kicks me out to the command line.  I can still see all my files and before I do any more damage I'd like to copy my home directory (which - idiot me - I haven't done for a while....).  Anyway when I plug in a usb memory stick I get a message saying '/dev/bus/usb/005$ [17077.188000] sd 13:0:0:0: [sdb]  Assuming drive cache: write through sd 13:0:0:0: [sdb]  Assuming drive cache: write through'

and then it does not return to the prompt.  dmesg returns lots of info including usb-storage: device scan complete and it identifies the name of the device as well as its size etc...

However, sdb is not recognized as a directory in /dev and the usb stick is not in /media.  I tried to mount it and got an message that it's not in etc. 

I just want to rescue these files!!  Oh, and I can't get on-line either so no copying to external sources or apt-getting at least with my limited knowledge.  

Thank you

---

### Post by taurus on 2008-11-21
What's the output of this command?

```
sudo fdisk -l
```

---

### Post by nhasian on 2008-11-21
can you boot from the liveCD and then copy over your documents to the usb drive?

also a lot of people use the knoppix liveCD 

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by themoose on 2008-11-21
This is going to be slow as I can't copy anything from my laptop onto the forum here:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units - cylinders of 1606*512 = 
Disk identifier 0xd845332

Device Bot  Start   End  Blocks  Id     System
/dev/sda1     1     15112   121387108   Linux
/dev/sda2    29654  
/dev/sda3
/dev/sda5     and so on here
/dev/sda6

Parition table entries are not in disk order

Disk /dev/sdb: 2031 MB, 2031091712 bytes
16 heads, 32 setors/track, 7748 cylinders
Units = cylinders of 512:512 = 262144 bytes
Disk identifier: 0x00000000

Device        Boot    Start    End    Blocks    Id   System
/dev/sdb1      *      16        7748     1979456  e    W95  FAT16

---

### Post by taurus on 2008-11-21
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by themoose on 2008-11-21
OK,  I got an error message when I included df -h but without it I now have sdb1 as a directory in media.  If I copy to it will I be copying to the usb drive (hope hope hope...)

---

### Post by taurus on 2008-11-21
Only if you have mounted /dev/sdb1 to /media/sdb1 first.  Then, you would copy stuff to /media/sdb1 and it will be copied to your USB drive.  What does the output of this command say anyway?

```
df -h
-or-
mount
```

---

### Post by themoose on 2008-11-21
Well, I tried copying and I think it did.  The light on the drive was flashing while files were being copied.  Unfortunately, though, I ran out of space on my usb.  It was 2 gb and I have two other blank 2 gb drives.  First, do I have to umount media/sdb1 in order to save the data or is that bad?  Second how can I complete the copying to another usb where I left off?

Sorry to be a bit unruly/anxious/eager...

---

### Post by taurus on 2008-11-21
There should be an icon on your desktop so before you yank it out, click the icon with the right button and Eject it.  Then, you can safely remove it.  I haven't tried this but I don't believe you can write a large file to it but have it spread into two USB thumbdrives.  If a large file doesn't fit into a single drive, you need to split the file up until a smaller one would fit into your USB thumbdrive.  Otherwise, get a larger drive.

---

### Post by themoose on 2008-11-21
I'm an idiot.  I was going to buy a single larger drive, but I didn't in favor of 3 smaller ones.  I didn't listen to that small voice inside saying 'don't be cheap....'

I don't have access to the desktop - at all.  I only have access through the command line.  The desktop is just crashed.  And I can't get on-line to install a new one.

---

### Post by taurus on 2008-11-21
Then you must unmount it from a prompt before you remove it.

```
sudo umount /media/sdb1
df -h
```

p.s.  I am not sure where you reside but you can pick up a 8GB or even a 16GB thumbdrive for real cheap now.

---

### Post by themoose on 2008-11-22
Yeah, I was at a BB looking at a 6 gb but it was a few bucks more than 3 2gb and I cheaped out.  Tomorrow, first thing I'll go get a 10gb (what I'm copying is about 5...)  Do I need to follow the same steps I did tonight?  By the way, I just checked and it did indeed copy onto the drive.  In fact I got the most critical stuff (grade sheets I hadn't backed up in two weeks... OMG!)

---

### Post by taurus on 2008-11-22
If you have CompUSA near you, head over there first thing tomorrow morning, 9AM, because they have some crazy pre-Thanksgiving sales.

---

### Post by themoose on 2008-11-22
There's no CompUSA, unfortunately, but I'll go get a big one back at BB.  

The next step is to upgrade to intrepid.  The whole problem started when my school 'upgraded' their mail server to M$ 2007 and I couldn't read my email using evolution.  I'd heard that Evolution 2.24 had the protocal or could be adopted.  I tried to download it, was informed I needed some other files, downloaded them, tried to re-boot and, well, command line only.  I'm sure I'll be back on this thread and forum asking some more questions, but, until then, thank you so much.  You may have saved my career. No kidding.

---

