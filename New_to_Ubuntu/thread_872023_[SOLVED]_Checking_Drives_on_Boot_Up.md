---
title: "[SOLVED] Checking Drives on Boot Up?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by gabriella on 2008-07-27
When I boot up just after the UBUNTU logo loads it then goes through the "checking" drives routine with the option of pressing "esc" to skip it. How do I turn this part off? I'm convinced that when I first installed it didn't do this!

---

### Post by GreenN00b on 2008-07-27
It does this from time to time after a number of boot ups, if you let it finish if will not attempt to scan for a while - this is the default behavior.

I recommend you don't disable this but if you want to disable it edit /etc/fstab file and set last column to 0 for the filesystem you want to disable.

---

### Post by caljohnsmith on 2008-07-27
Instead of turning off the file system checking completely, I would recommend setting the check interval for say a month at a time; having Ubuntu do a file system check is a good way to make sure your system is OK, and if it only runs once a month, that shouldn't be too often.

You can change it to once a month using:
```
$ sudo tune2fs -c 0 <Ubuntu partition>   (this first disables fsck from checking based on number of reboots)
$ sudo tune2fs -i 1m <Ubuntu partition>   (this then sets the time interval between running fsck checks to 1 month)
```
<Ubuntu partition> should be the path to your Ubuntu partition, e.g. /dev/sda2, which if you don't know you can find using:
```
sudo fdisk -l
```

---

### Post by halitech on 2008-07-27
I think the default is every 30 boots so if you turn your machine off every night, once a month you will have to do a check. If you do multiple reboots during the day (for whatever reason) it will happen sooner.

---

### Post by stevoo on 2008-07-27
i was annoyed for that, especially when in 7.10 you couldnt stop it. And even worse it happened on the worst time when i was gonna give a presentation :( 15 mins of waiting there.

But that is vital to ensure that your hard disk is ok and working. We dont want it to go dead with no notice or to store something in a bad byte. That could crash everything. So leave it since it is every 30 boots, if you are busy at that time just hit Esc

---

### Post by gabriella on 2008-07-27
OK thanks guys. That explains it, I wasn't going crazy in thinking this only just started to happen! And of course as soon as it did I just hit esc to get rid of it.
I'll leave it running now I know what's happening!

---

