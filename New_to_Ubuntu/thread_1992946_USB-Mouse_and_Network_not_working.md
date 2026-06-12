---
title: "USB-Mouse and Network not working"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Yora on 2012-06-01
[CENTER]Hello, good people.
[/CENTER]
 
I tried out Ubuntu 12.04 on an UBB drive and since I liked what I saw, I used that drive to install the OS also on an empty partition on my Hard Drive.

The USB-Drive pretty much auto-detected everything and once I had the auto-update run through, everything works fine. However, on the Hard Drive, the mouse does not respond, and there is no network connection. There also appears to be a very low screen resolution. My PS/2 keyboard does work.

Running "lsusb", the mouse was detected as plugged in and it also showed the correct model-ID. Putting it into another USB-Port also gets it detected by "lsusb" and it also does not respond.
Attempting to download all the auto-updates does not work, because there is no network connection.

I attempted to use [this guide]("http://www.ehow.com/how_6800109_reinstall-ubuntu-using-command-line.html"), but step 4 "sudo apt-get install xserver-xorg" results in an error message, something about "could not retrieve package" or something to that effect.

One odd thing I noticed was that the paths for the packages always where "de.ubuntu". Location is set to "Berlin" and keyboard layout is set for "German", but for everything else I always selected English. (de is the code for Germany)
Could it be that there is some kind of mixup?

Right now, I have working WinXP on the Hard Drive and working Ubuntu 12.10 on a USB drive. I don't know if this might be helpful in some way to fix things. Retrieving and posting any error messages would be a bit complicated, to say the least. At the very worst I could write it down with a pencil and then type it all in again, but it would be nice to be able to avoid that.

The question: How do I get xserver-xorg reinstalled?

---

### Post by Yora on 2012-06-01
The installation is currently not booting at all. However, I did get the same error massage when I tried the repair mode and managed to photograph it.

I am now downloading the iso again and try a different way of installing. Possible that it will then run without problems.

---

