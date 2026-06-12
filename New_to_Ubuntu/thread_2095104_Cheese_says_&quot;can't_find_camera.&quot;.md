---
title: "Cheese says &quot;can't find camera.&quot;"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by gordon33 on 2012-12-15
Hello all  

I am using Ubuntu 10.04 and a HP lab top G60t-200.  
It has been a year since I used the camera on this lab top.  
this lab top was taken apart 6 months ago to repair the screen's light.

Sometime I clicked on Cheese from the pull down menu and I get a blank / gray screen.

This time I got the same screen with "No device found".

What kinds of checks can I make to see if the on board camera is still connected correctly?  Or is there something else I should be checking?

gordon33

---

### Post by gordon33 on 2012-12-15
gordon@gordon-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gordon@gordon-laptop:~$ dmesg | tail
[   38.459148] wlan0: deauthenticating from 00:24:b2:05:d5:80 by local choice (reason=3)
[   38.459176] wlan0: direct probe to AP 00:24:b2:05:d5:80 (try 1)
[   38.461252] wlan0: direct probe responded
[   38.461256] wlan0: authenticate with AP 00:24:b2:05:d5:80 (try 1)
[   38.466791] wlan0: authenticated
[   38.466818] wlan0: associate with AP 00:24:b2:05:d5:80 (try 1)
[   38.469516] wlan0: RX AssocResp from 00:24:b2:05:d5:80 (capab=0x411 status=0 aid=2)
[   38.469520] wlan0: associated
[   38.470183] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.344520] wlan0: no IPv6 routers present
gordon@gordon-laptop:~$

---

### Post by gordon33 on 2012-12-16
Hello All


What did those 2 terminals commands reveal.

Gordon33

---

### Post by rburkartjo on 2012-12-16
gor if you still have not gotten cheese to work and you have made sure your camera is connected correctly try going to the ubuntu software center and downloading kamerka. cheese didnt work for me under 12.04 and now it is working in 12.10 but kamerka is better imho. good luck

---

### Post by gordon33 on 2012-12-16
Hello rburkartjo

Thank you for your reply.

Did you mean "kamera" I found that in Synaptic Package Manager.  I installed it and have no clue as to where to find it to even guess how to use it.  

To see if the camera is hooked up I would have to tare the laptop a part as the camera is in the screen's frame.

Isn't there a way to check to see if the camera is hooked up using a terminal command?

Gordon

---

### Post by ub-newbie on 2012-12-16
Gordon33  
The "LSUSB" command list all the USB devices your system sees.  It should show your webcam.  I.E.

```
Bus: 001 Device 003: ID 046d:0025 Logitech, Inc. Webcam C270
```

Another thing you could try would be (on the command line, but it opens a GUI window)```
gstreamer-properties
```

Then go to the Video tab, under Default Input, see if your camera is available under Device.  If so, try a Test.  

Hope this helps..

---

### Post by gordon33 on 2012-12-16
Hello ub-newbie

I The default input said "none" .  Was the multimedia system selector looking for an on board camera or a usb hooked up camera?

This labtop has a camera in the screens frame.

Gordon

---

### Post by ub-newbie on 2012-12-17
Gordon...
The on-board camera functions as a USB camera.  The on-board (in the screens frame) camera IS a USB camera.

When you opened gstremer-properites, Video, Default Input, could you change the dropdown menu from "none" to you camera.  If not, gstreamer-properties, just like LSUSB, is not seeing your camera, so it's probably broken.

---

### Post by audiomick on 2012-12-17
> **ub-newbie said:**
>  LSUSB, is not seeing your camera, so it's probably broken.

Yes. Or it didn't get plugged in properly when the laptop went back together after the repair you mentioned.

They do break. The one in this laptop stopped working a while back.

---

