---
title: "[How-To] iPhone / iPod Touch over USB in Ubuntu"
date: 2009-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by carlosgs91 on 2009-09-27
.

---

### Post by Giant Speck on 2009-09-27
Oh wow.  This actually works!

---

### Post by Exodist on 2009-09-27
This needs a sticky somewhere!

---

### Post by sudoer541 on 2009-09-27
can you load music into your ipod touch/iphone?

---

### Post by steev182 on 2009-09-27
This is what I was wondering.

With this can you use Banshee or Rhythmbox or Songbird to sync your iPnone?

---

### Post by carlosgs91 on 2009-09-27
.

---

### Post by outphase on 2009-09-29
What is the proper method to unmount the iPhone? I get this error > umount: /media/iPhone is not in the fstab (and you are not root)

edit: Found the answer: $ sudo umount mount.fuse.ifuse

---

### Post by carlosgs91 on 2009-09-29
.

---

### Post by mlrivera on 2009-09-29
I've followed the instructions from the first post, but when i get to sudo apt-get install ifuse i get an error message like this E: couldn't find package ifuse
I'm really really new at this, I was wondering how or if this can be solved

Thank you in advance!

---

### Post by carlosgs91 on 2009-09-30
.

---

### Post by The Creator on 2009-10-04
This is old news. I actually found this around a year ago and here is the thread. thanks though. [http://ubuntuforums.org/showthread.php?t=953381](http://ubuntuforums.org/showthread.php?t=953381)

---

### Post by delianeal on 2009-10-08
I really would like to do this but I read the iFuse main page info and it says that your library will be destroyed (yikes!) if you are using Apple's 2.0 firmware.  I just updated my iPod Touch to version 3.1.1. . .brace yourselves, here comes the stupid question:  in this context, are "firmware" and "version" the same thing?  In other words, will iFuse blow up my library?

Also, am I correct that the consensus is to use Amarok instead of Rhythm Box for my music player if I'm able to use iFuse?

thanks in advance!

---

### Post by kevinguillorytraining on 2009-10-09
Worked for me. My iPod is now connect-able in my Ubuntu machine. :)

---

### Post by rootie on 2009-10-11
Any idea how to fix this? I've tried every permutation of arguments and still nothing...

```
usbmuxd_scan: Invalid packet size (20) received when expecting a device info record.
No iPhone found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
```

---

### Post by randcoop on 2009-11-18
First, be sure you have a mount point for the Ipod (e.g. /mount/ipod).  The error message you're getting should be fixed by running ```
usbmuxd
```
before running ifuse.  Then run ifuse /media/ipod (or whatever your mount point is) and you should get connected.

If it doesn't work, it's probably a permissions problem.  You can run sudo ifuse /media/ipod to resolve that problem.

---

### Post by neoroses on 2010-03-02
heyup when i try and access the  mounted folder on the desktop (the ipod logo) i get this error:

```
Could not display "/media/iPod".

the file is of a unknow type
```

any clues?

---

### Post by carlosgs91 on 2010-03-03
.

---

### Post by dcjose20 on 2010-03-07
Thats good to hear, I'll just wait til Lucid comes out that way I will save myself the headache of messing up my iphone lol.

---

### Post by Thomas Garman on 2010-03-07
I just got Rhythmbox to detect my iPod Touch and I added music to it... it works...

[http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13](http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13)

The only thing I would add is this:  when you first plug in your iPod touch you will get a dialogue that asks you if you want to initialize your iPod.  Obviously, NO you do NOT want to initialize your iPod because then you would have to put all the apps back on it...

So, click cancel.

Then Rythmbox detects the device and you can add music to it, like iTunes but without some of the functionality and none of the annoying apple proprietary business.

I like my iPod Touch, but I hate iTunes.  THANKS for making this work everybody. 

Incidentally, I got this to work on my Acer Aspire One using Karmic.

---

### Post by ootawata on 2011-01-01
Sorry to raise the dead, but for anyone still searching for answers:
I run Ubuntu 10.10, and it initially appeared to mount my iphone (I still run 3.something iOS) but I was unable to look at anything in my phone (I was getting some obscure, unhelpful, error message).  So I installed ifuse and gtkpod and now I can transfer music to/from my iphone easily.  To clarify:

```
apt-get install ifuse
apt-get install gtkpod
```

Then start up gtkpod and it'll use ifuse to mount your phone (assuming your phone is plugged into your computer).  
If gtkpod cannot mount your phone, do this before running gtkpod:

```
mkdir myiPhoneDirectory
ifuse myiPhoneDirectory
gtkpod
```

Hope this helps.
Also, I've never used Amarok to manage music on my phone, but I know it can be done.

---

