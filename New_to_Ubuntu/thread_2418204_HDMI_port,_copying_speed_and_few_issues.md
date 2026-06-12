---
title: "HDMI port, copying speed and few issues"
date: 2019-05-03
forum: New to Ubuntu
---

### Post by aem5299 on 2019-05-03
Hi,

I have just installed Ubuntu yesterday, and honestly is hasn't been a good experience so far. I had more issues than I had with windows for the past 2 years.

I am trying to connect my laptop to my TV to mirror my screen, with windows as soon as I hook the HDMI cable the mirroring starts. but with Ubuntu nothing happens. this is the output of xrandr
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.02*+  40.03  
HDMI-1 disconnected (normal left inverted right x axis y axis)
   1920x1080     60.02 
```

the HDMI-1 doesn't change weather I plug or unplug it.

another issue I have. I was trying to copy 700mb video to a USB flash drive, instantly the copying loading bar reached about 90% (680/700mb) and just stopped there. I waited more than 20 minutes it never finished! And I have tried multiple times and even restarted my laptop, the same exact behaviour happens.

Please tell me if that's the norm using Ubuntu, because this my everyday use laptop, I can't deal with such headaches in a daily basis.

Thanks!

---

### Post by TheFu on 2019-05-03
Expecting any Linux to be like Windows is a mistake. You'll only be frustrated, probably in a similar way that people here find using Windows extremely frustrating for all the things is doesn't/cannot do.  We all have expectations based on our prior computer use.  Linux isn't Windows.

Whether HDMI can work or not depends on all sorts of things.  Perhaps if you shared the Ubuntu release you are running, the DE you are using and what other things you've tried besides xrandr, someone could help?  For example, is the system using F/LOSS GPU drivers or proprietary drivers? Have you tried using lxrandr?

Best to ask 1 question per thread. Seldom do the people answering 1 question know the answers to every question.  I came here for the "copying speed" question, but there isn't enough information to attempt an answer.
* which file system is on the flash drive? exFat, fat32, ntfs, ext2, something else?
* how is it connected to the system?  USB2, USB3, USB3.1?
* which interface does the flash drive support?  ^^^^^^  Expecting a USB1.1 storage device to behave like a USB3.1 device isn't fair.

All Unix systems use buffers.  These are used to help commands finish quicker by leveraging RAM for data movement. That movement can be from/to storage or from/to network locations.  A program copying files will appear to complete once the file has been copied from the disk into the buffer and is still being written to the other storage device.  If the buffer cannot hold the entire file, then the command will have to wait as the file is flushed from the buffer to storage. Writing is a much slower process, almost always.  If there is some physical or logical problem with the storage media, either the source or the target, then those issues would be logged into the system log files.  Have you looked at those?  They are in /var/log/

Learning Linux (Ubuntu is a version of Linux), is like learning a foreign language.  You've probably spent over a decade, perhaps longer, learning MS-Windows.  Please keep that in mind and that Linux isn't Windows. It has a completely different design philosophy and vastly different implementation for almost everything.  OTOH, to more you learn Linux, the more you will understand pretty much every other popular OS used in the world today, except 1.  Unix is the preferred OS for almost everything these days.  Phones, tablets, TVs, Video players, vehicles, watches, servers (by far), supercomputers, networking equipment, IoT stuff, basically everything except the corporate desktop.

Every new device we try out has something new to learn and understand.  Here's a primer [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) that I hope makes your transition less painful.

---

### Post by aem5299 on 2019-05-04
Hi,

The filesystem of flashdrive is fat32. The connector is USB3. I'm not sure what the flashdrive supports honestly, but with the same connector and device with windows copying about the same size takes approx. 2 mins.

Thank you for the guide, and I will give lxrandr.

EDIT: I tried lxrandr, the TV doesn't appear in the options. Only the internal display.

---

### Post by Autodave on 2019-05-04
Can we please have the specs on your machine and what version of 'buntu you are using??

---

