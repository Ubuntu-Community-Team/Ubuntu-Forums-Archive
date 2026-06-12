---
title: "iPod not showing up in Banshee?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by karasuman on 2008-07-10
I need to preface this by saying that I know very little about Ubuntu and even less about iPods.  :)  I'm trying to explore the option of maybe buying an iPod, but if it won't work with Ubuntu, I don't want to waste my time and money.  I've borrowed an iPod to see if I could get it working.

I plugged the thing in, and voila!  I had access to the files on it in rhythmbox, just like that.  Unfortunately, I couldn't seem to add NEW files to it, so I looked around and found Banshee.

Banshee is all installed, etc., but the iPod is not showing up in the list on the left.  I googled some, found a script to run, ran it (output below), ran some other command about HAL something, found all of the information that it said should be there, and... well, I guess I'm just stuck.

Any suggestions?  I'm open to using another program, if there's a better recommendation.  All I really want is the ability to put my music on an iPod with this computer.  :)

```
beth@grumpy-laptop:~/Desktop$ ./ipod-debug-dump.sh
[[------------ Output of 'ipod --list' ------------]]

glibtop: statvfs '/media/GREYSWANDIR' failed

(process:15813): GLib-CRITICAL **: g_strchug: assertion `string != NULL' failed

(process:15813): GLib-CRITICAL **: g_strchomp: assertion `string != NULL' failed

(process:15813): GLib-CRITICAL **: g_parse_long_long: assertion `nptr != NULL' failed
Path Info
   Device Path:      /dev/sdc
   Mount Point:      /media/GREYSWANDIR_
   Control Path:     /media/GREYSWANDIR_/iPod_Control/
   HAL ID:           /org/freedesktop/Hal/devices/volume_uuid_5032_5F59_0
Device Info
   Model Number:     (null)
   Device Model:     Unknown
   iPod Generation:  Unknown
   Adv. Capacity:    (null)
   Is New:           YES
   Writable:         YES
   Serial Number:    5D7036L9XQS
   Firmware Version: (null)
   Manufacturer ID:  5D
   Production Year:  2007
   Production Week:  03
   Production Index: 7659
Volume Info
   Volume Size:      1015021568
   Volume Used:      1014112256
   Available         909312
   UUID:             5032-5F59
   Label             GREYSWANDIR
User-Provided Info
   Device Name:      (null)
   User Name:        (null)
   Host Name:        (null)

Path Info
   Device Path:      /dev/sdb
   Mount Point:      /media/GREYSWANDIR
   Control Path:     /media/GREYSWANDIR/iPod_Control/
   HAL ID:           /org/freedesktop/Hal/devices/volume_uuid_5032_5F59
Device Info
   Model Number:     (null)
   Device Model:     Unknown
   iPod Generation:  Unknown
   Adv. Capacity:    (null)
   Is New:           YES
   Writable:         NO
   Serial Number:    (null)
   Firmware Version: (null)
   Manufacturer ID:  
   Production Year:  0000
   Production Week:  00
   Production Index: 0
Volume Info
   Volume Size:      1015021568
   Volume Used:      1015021568
   Available         0
   UUID:             5032-5F59
   Label             GREYSWANDIR
User-Provided Info
   Device Name:      (null)
   User Name:        (null)
   Host Name:        (null)



[[-------------------- HAL Dump -------------------]]

```

---

### Post by sydbat on 2008-07-10
I found [this (older) article]("http://www.linuxjournal.com/article/9266") discussing Ubuntu and iPods. The author suggests gtkpod. Might work.

---

### Post by karasuman on 2008-07-10
Not only did gtkpod work great as soon as I tried it, but I like its interface more than Banshee's, too.  :)  Thanks for the link.  That was a very helpful article!

---

### Post by sydbat on 2008-07-11
You're welcome. Google is a wonderful thing!

---

