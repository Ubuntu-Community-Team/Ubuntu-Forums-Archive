---
title: "Using OWC Mercury On The Go Hard Drive with Ubuntu"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by markwco on 2014-03-09
I have an external OWC Mercury On The Go Hard Drive.  It says on OWC's website that it's Linux compatible.  When I plug it into my Ubuntu Linux machine it's not recognized though.  I have viewed USB devices and it detects my keyboard, mouse, logitech webcam, and wifi adapter but not this hard drive.
I'm not sure if this could have something to do with it but it is separated into two partitions and the first one is formatted for a Mac I own but the 2nd is formatted as HTFS.
Any idea how I can get my computer to recognize this drive?
Thanks!

---

### Post by Vladlenin5000 on 2014-03-10
I seriously doubt the website mentions Linux but they should be compatible anyway provided the manufacturer follow the usual mass storage device adapter interface industry standards. The file system, however, are an entirely different and unrelated issue.
First of all, with the enclosure+HDD connected, please do:
```
sudo lsusb
```
in order to confirm the device is being correctly detected. Please post the results.

---

### Post by markwco on 2014-03-10
Hello Galiza,

I did a sudo lsusb and it lists all my other USB items such as webcam, keyboard, mouse, and wifi adapter but the hard drive is the one USB device that isn't listed. I know the hard drive and cable is okay since it's being recognized on my Mac computer.  Often Linux is left out but amazingly on the OWC website for this drive it lists it as compatible with Linux.

---

### Post by Vladlenin5000 on 2014-03-10
Well, you just found out it isn't... Or, most likely, you have a problem with that USB port; even a device requiring drivers or special configurations/tweaks would have been listed with that command.

---

### Post by markwco on 2014-03-10
Other devices are working on that port so it definitely isn't the port.  I am still at Ubuntu Linux 12.04 so maybe it's time to upgrade to a newer version.  I'm waiting on the next LTS version in April so I'll see if that makes a difference.  It sounds like the best solution though may be to get a new external hard drive.  Thanks for your help.

---

### Post by markwco on 2014-03-10
I just solved my problem. I don't know why I didn't think of it sooner.  I was plugging the hard drive into an extension cable from the back of the computer to my desk.  Other items work in there so I never thought of that but the distance must have been a problem.  I plugged it directly into my computer and it's working fine now!

---

