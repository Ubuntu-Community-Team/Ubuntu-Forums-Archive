---
title: "Wireless Internet won't show up on Ubuntu 14.04"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by abe5 on 2015-01-03
Okay, I'm completely new to Linux, I thought I would try and start learning it. That being said, I downloaded Ubuntu 14.04 LTS on an old Dell Studio 1735 laptop I had sitting around (I put a new hard drive because the old one failed), and can't get it to connect to WiFi. I watched a few YouTube videos but when I click on the internet icon on top my router isn't there, and when I go to network under system settings all that show up is wired and Network proxy. Is there anything I can do to fix my wireless without being able to connect through a cable? Also thought I should add that I have read some threads about this same problem but with 12.04 and really didn't quite understand what I was suppose to do when options were given

---

### Post by jeremy31 on 2015-01-03
In terminal enter ```
lspci -nnk | grep -iA2 net
``` and post the result

---

### Post by abe5 on 2015-01-03
0:900.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM 5784M Gigabi
t Ethernet PCIe [14e4:1698] (rev 10)
           Subsystem: Dell Device [1028:0256]
           Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11B/G LP-PHY
 [14e4:4315] (rev 01)
          Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
          Kernel driver in use: b43-pci-bridge

---

### Post by Bucky Ball on 2015-01-03
Welcome. If you can get online with a cable, try following the instructions for 12.04 [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29") (the very first ones on that page that are in view). Think you need the STA driver. Don't worry that they're for 12.04. Odd that card didn't work out of the box. :-k

Before doing any of this, though, please use Software Updater to update while online with a cable and then check 'Additional Drivers'. Is the STA driver offered?

Also, please provide the result of:

```
sudo lshw -C network
```

* Just looking at the output of your last command, are you getting online at the moment with a USB wireless dongle plugged in rather than a cable? Removing the dongle, if there is one, and using a cable will prevent confusion. If this is not possible, go through the steps and then pull the dongle out and reboot when finished the commands.

PS: Please use [code] tags for output. See how with the last link in my signature. Good luck. ;)

---

### Post by abe5 on 2015-01-03
I'm not online at all with that computer I'm doing this with a different computer

---

### Post by Bucky Ball on 2015-01-03
You can't get an ethernet cable to it? Makes things a LOT easier. Is your output from post 3 from the computer you are currently using online? If so, of no use. If not, try [THIS]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access") on the computer you are looking to fix if it actually does have the BCM4312 and the output from post 3 is actually from the computer you are trying to fix.

---

### Post by abe5 on 2015-01-03
Hey, sorry had to run, but I got an ethernet cable hooked up and doing updates now and the post#3 is the output from the computer I am trying to fix. I'll post again when it is finished.

---

### Post by abe5 on 2015-01-03
Ok, after the update the STA showed up in the additional drivers and my wireless is now working, Thanks a lot for your help!

---

### Post by Bucky Ball on 2015-01-03
Excellent news! Enjoy and thanks for marking as solved to help future travelers. ;)

---

