---
title: "Wireless WNA3100 setup problems"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by czn89v on 2012-01-25
I have been trying to get the wireless usb wna3100 from Netgear.  I followed the instructions from this link because it seemed the most simple step by step instruction. 

[http://www.linuxhelp.net/forums/index.php?showtopic=9898](http://www.linuxhelp.net/forums/index.php?showtopic=9898)

I followed the instructions and I have no working wireless internet connection.  Any help would be appreciated.  I know a command will be needed to show what is going on in my system so if someone can let me know the code needed I will repost.


Thanks,

czn89v

---

### Post by anewguy on 2012-01-26
With the adapter plugged in to a USB port, post back the output of:

lsusb


We'll go from there.


Dave ;)

---

### Post by czn89v on 2012-01-26
Here is the result of lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 0461:4d46 Primax Electronics, Ltd 
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 005: ID 040b:2000 Weltrend Semiconductor 


Thanks,

czn89v

---

### Post by anewguy on 2012-01-26
There's another very recent thread here on the forums for this - it may not say wna3100, but you have the same chipset - broadcom 4323.  Basically, my net searching and what another expert said is that there is no native driver for this.

So, get a hold of the Windows XP driver that matches your Ubuntu architecture (32 or 64 bit) - they *must* be Windows XP drivers.  Put the .inf and .sys files from the driver in a folder - something like ~/bcm4323 would be handy!

Post back when you've done that and I'll give you the step-by-step for installing them in Ubuntu.

Dave ;)

---

### Post by anewguy on 2012-01-26
Here's link to the other thread - see post 6.  That way I don't have to type it in all over again.

[http://ubuntuforums.org/showthread.php?t=1913059]("http://ubuntuforums.org/showthread.php?t=1913059")


Dave ;)

---

### Post by czn89v on 2012-01-29
> **anewguy said:**
> There's another very recent thread here on the forums for this - it may not say wna3100, but you have the same chipset - broadcom 4323.  Basically, my net searching and what another expert said is that there is no native driver for this.

So, get a hold of the Windows XP driver that matches your Ubuntu architecture (32 or 64 bit) - they *must* be Windows XP drivers.  Put the .inf and .sys files from the driver in a folder - something like ~/bcm4323 would be handy!

Post back when you've done that and I'll give you the step-by-step for installing them in Ubuntu.

Dave ;)
I have the two files in my home folder under wifi driver because of another attempt at trying to get this to work.  Is that okay to keep the files in that folder.  I also already installed ndiswrapper I believe successfully due to another attempt as well.

thanks,

Chris

---

### Post by anewguy on 2012-01-29
Yep, it's fine - there's no "law" on where they go.

So, if you tried this before:

- reverse any edits to the /etc/modules file

- reverse any edits to the /etc/blacklist file

- using ndiswrapper at the command line, be sure nothing is returned when you do the following:

ndiswrapper -l <press return>  BTW - that's a lower-case "L" for "list"

Be sure to install ndisgtk as outlined in the link.

Follow the other link to install the Windows drivers using ndisgtk.

Remember:  Windows XP drivers only and they must match Ubuntu architecture (32 or 64 bit).

Dave ;)

---

