---
title: "Ebook Reader not detected, USB won't mount"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by amayan on 2013-03-04
I'm using Ubuntu 12.04 and trying to access a RockChip ebook reader V1.1.0 but cannot seem to get Ubuntu to recognise that it's plugged in. It's charging so the usb works fine, and i've accessed it before through windows vista and there is data on it. 

It doesn't show up in 'dmesg' that something's been plugged in, and 'sudo fdisk -l' brings up the following :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062b6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   230264831   115131392   83  Linux
/dev/sda2       230266878   234440703     2086913    5  Extended
/dev/sda5       230266880   234440703     2086912   82  Linux swap / Solaris


and 'lsusb' brings up:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:0a04 Logitech, Inc. V20 portable speakers (USB powered)


and is the same wether device is plugged in or not. Still pretty new to ubuntu and don't really understand the commands all too well yet, so not sure how to delve much further.

Hoping to get this working with my laptop (ubuntu only) as it was a gift, any ideas?

---

### Post by sully101 on 2013-03-06
Have you tried installing Calibre. [http://manual.calibre-ebook.com/faq.html]("http://manual.calibre-ebook.com/faq.html")

I would start by installing the package in the repositorys and if that failed have a look at their FAQ section [http://manual.calibre-ebook.com/faq.html]("http://manual.calibre-ebook.com/faq.html") there is a section on devices not detected by linux [http://manual.calibre-ebook.com/faq.html#why-is-my-device-not-detected-in-linux]("http://manual.calibre-ebook.com/faq.html#why-is-my-device-not-detected-in-linux")

---

### Post by cortman on 2013-03-06
If dmesg doesn't even show anything I'm at a loss. That's a pretty unusual situation. Try Calibre as suggested, is all I can think of.

---

### Post by amayan on 2013-04-04
After trying a couple of things, turned out i'd overlooked the simplest of problems... i tried a different usb lead and it worked just fine. Unfortunately i dropped it on the floor a couple of days later and it's now broken. Looks like we weren't meant to be together after all. Thank you for the help just the same :)

---

### Post by Elfy on 2013-04-04
I quickly marked it solved for you in response to report - for next time, until we get the plugin back [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by amayan on 2013-04-08
Thanks :)

---

