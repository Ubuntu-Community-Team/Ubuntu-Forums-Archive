---
title: "External hard drive issues"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by russ6 on 2008-09-19
I had a poke about on the forums for anything similar but found nothing.

i have a freecom external HDD for all my music and videos and it works nicely with my laptop running ubuntu.until today when all of a sudden it won't let me write anything to it. it just stops writing about 20-30% of the way through... no error message; just stops.

it's fat 32 formatted.

if anyone could give me a hand it would be much appreciated

russ

---

### Post by MegaJim on 2008-09-19
Are you copying using the GUI (nautilus)?

If so, try copying the file again using the terminal, as it will most likely give you some kind of error message if it fails...

---

### Post by russ6 on 2008-09-19
I typed in this in the terminal


 cp -r /home/russ/Desktop/alphabeat/* '/media/FREECOM HDD'

two of the files transferred over then my external packed up and wouldn't respond to anything, i.e. wouldn't even let me see files on it using nautilus...

There was no error message in terminal

---

### Post by MegaJim on 2008-09-19
Sounds ominous, no error messages on the console?

If that drive has important data on it I would consider backup as soon as possible.

I would have a look in the log files and search for any relevent error messages:

Alt+F2 to launch the run application dialog, then type in gnome-system-log.  If you don't immediately see anything relevant try to trigger some events by writing to the disk again.

It could just be a problem with the filesystem, if not we can try to diagnose the hard drive with a handy package called smartmontools.

---

### Post by russ6 on 2008-09-19
Tried copying to it again and got the following message.. in the system log viewer:

Sep 19 15:15:11 russ-laptop kernel: [  467.682083] usb 5-2: reset high speed USB device using ehci_hcd and address 3
Sep 19 15:15:41 russ-laptop kernel: [  507.073877] usb 5-2: reset high speed USB device using ehci_hcd and address 3
Sep 19 15:15:42 russ-laptop kernel: [  507.228035] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
Sep 19 15:15:42 russ-laptop kernel: [  507.228050] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information.

going to buy a replacement external and a bigger internal tommorrow, but i tried taking stuff off the drive and it failed after a while

---

### Post by MegaJim on 2008-09-19
Try reading this thread: [http://ubuntuforums.org/showthread.php?t=163716](http://ubuntuforums.org/showthread.php?t=163716)

---

### Post by timcredible on 2008-09-19
try doing a dosfsck on the drive.

---

