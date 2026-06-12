---
title: "HP scanjet 3570c not detected under Hardy"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by ranch hand on 2008-11-17
This box is 8.04.1 all the way.

I get this message from Xsane; no devices available

Under possible reasons is #4 no backend loaded and a suggestion to try "man sane-dll".

To which I get "No manual entry for sane-dll"

This, I assume, means that I have no backend for this scanner.  However, if I try to download and install the first 2 files in this post;

<http://ubuntuforums.org/showpost.php?p=1030523&postcount=16>

I am informed that a newer version is installed.

I am missing something here but I'll be jiggered if I can figure out what.  It is too muddy to get much done on the ranch today so I have been at this for about 5 hours now and I think I have hit a wall.

Part of the reason I chose this scanner is this entry;

 HP  ScanJet 3570c  v8.04 (Hardy)  USB. Recognized right away. Works fine.   2008-Jun-12

Admittedly this is from the Kubuntu wiki.

I hope someone can give me a clue as to what to do.

---

### Post by Crafty Kisses on 2008-11-17
What are the results of this command? Please make sure the scanner is plugged in:
```
lsusb
```

---

### Post by ranch hand on 2008-11-17
thom@playtime:~$ lsusb
Bus 008 Device 003: ID 0644:0201 TEAC Corp. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 003: ID beef:0006  
Bus 007 Device 002: ID 4855:6288  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0461:4d15 Primax Electronics, Ltd 
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 046d:c719 Logitech, Inc. 
Bus 004 Device 004: ID 046d:c718 Logitech, Inc. 
Bus 004 Device 003: ID 413c:8130 Dell Computer Corp. 
Bus 004 Device 002: ID 046d:0b05 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by Crafty Kisses on 2008-11-17
The only entries of lsusb it could could be really would one of two, and I'm guessing it would be this:
```
Bus 008 Device 003: ID 0644:0201 TEAC Corp.
```
If that's the case, then it does recognize your scanner. You may also want to take a look at this link > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) and see if you're scanner is on that list.

---

### Post by ranch hand on 2008-11-17
Yes I have actually been there and it is listed as good.

---

### Post by bumanie on 2008-11-17
HP are a big supporter of open source, unfortunately, according to the HP site that is one product they do nothave linux drivers for.

---

### Post by ranch hand on 2008-11-17
Sane support is supposed to be good for this model and it is used more on Mac than Win.

Searching the forums I found so odd problems, but generally old posts.

I am sure that the problem is with me.

---

### Post by halitech on 2008-11-17
have you tried running```
sudo xsane
``` 

when I got my new HP Scanjet G3010 (which works like a charm I may add) it failed to detect until I ran it as root the first time

there is good information here on most scanners

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by ranch hand on 2008-11-17
Scary warning before you try that, neet.  I am on my #2 install of a dual boot Ubuntu system so those don't bother me.

Unfortunately, I still get the message that no device is detected.

---

### Post by ranch hand on 2008-11-17
I have been perrusing the link to scanninghowto.  Interesting stuff.

May have a clue to the problem.

From; "cat /proc/filesystems"  you should reportedly get;

nodev   usbdevfs
nodev   usbfs

I have the 2nd, not the first.

It is also stated that;

You may need to mount usbdevfs to enable it and see the device files, which you can do at the command line with mount -t usbdevfs none /proc/bus/usb.

I tried this thinking that it may not be listed with out doing this.  that gave this result;

mount: unknown filesystem type 'usbdevfs'

I reinstalled  "libusb"  and installed "libusb-dev" in hopes of getting "usbdevfs" but to no avail.

Any thoughts?

---

### Post by Moriak on 2010-07-10
I know the last post is over 2 years old but I wanted to leave a trace for people who, like me, have a HP SCANJET 3570c.

It works fine under 10.04 with xsane started as root:

```

sudo xsane

```

---

### Post by Georgia boy on 2010-07-10
Tried that command but this is what happened:

thomas@thomas-desktop:~$ sudo xsane
sudo: xsane: command not found
thomas@thomas-desktop:~$ 

Do something wrong?

Tom

---

### Post by StrobeWylan on 2012-03-30
> **Georgia boy said:**
> Tried that command but this is what happened:

thomas@thomas-desktop:~$ sudo xsane
sudo: xsane: command not found
thomas@thomas-desktop:~$ 

Do something wrong?

Tom

I know this is an older post, but for anyone who searches and reads this thread like I did: 

Same thing happened to me. Then I realized I need to go to Ubuntu Software Center and install Xsane. After that all I had to do was open Xsane under applications-graphics and follow the prompts. Ended up closing terminal, cuz didn't really need it for this. 

HP 3570c works really good.:p

---

