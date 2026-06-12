---
title: "Installing Ubuntu on Inspiron 1501: Driver error"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by johannes6 on 2014-04-17
I've tried to install Ubuntu 12.04 as well as Lubuntu x86 on my Dell Inspiron 1501, which is currently working on Windows XP. When running the installation from both DVD as well as USB, the infamous coloured vertical lines appear on my screen. This problem is only temporarily solved when choosing the "nomodeset" option. 

With "nomodeset", the installation DVD/USB seems to be running for 30 seconds, then error message "b43/ucode5fw" pops up, followed - again - by coloured vertical lines shortly after. At this stage, Ubuntu/Lubuntu have not been installed yet. Laptop connected to Ethernet, but wi-fi is not active. 

Any suggestions?

---

### Post by Hadaka on 2014-04-17
Hi, i have had the same issue with dells several times.
try this...boot into BIOS, find your pcmi mini card- wlan 
and disable it. then boot again and see if it loads the os without
squiggly lines and b43 error messages. **If it loads normal with
the possible exception of warnings..then do.
from a wired connecrtion connected to the internet
```
sudo apt-get update
sudo apt-get upgrade
```
this may take some time to run. once finished, back into bios
enable your wlan mini card. boot...and then do.
```
lspci -n | egrep '0200|0280'
```
post the results so we can give you the correct wlan driver
thanks.

---

### Post by johannes6 on 2014-04-17
Unfortunately, disabling wifi does not help much further. The error message does not pop up again and the Lubuntu installation from USB seems to run a little longer, but then the coloured lines make a comeback. :-(

---

### Post by mörgæs on 2014-04-17
Are you able to install using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by johannes6 on 2014-04-19
Yes! The 64-k alternate ISO for AMD worked perfectly! Problem [SOLVED]. Thanks everybody! 

(Just FYI: When enabling wi-fi, the error message pops up again, so I will now look for the missing driver. But the main challenge were the vertical lines).

---

