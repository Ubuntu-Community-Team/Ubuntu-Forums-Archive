---
title: "Need help installing drivers."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by PlutoniumBoss on 2008-07-28
I've been trying to get a Logitech Quickcam Web USB working. I found a set of drivers here. [ [http://tuukkat.awardspace.com/quickcam/quickcam.html](http://tuukkat.awardspace.com/quickcam/quickcam.html) ]

I've been using Ubuntu for a few months now, and I'm basically familiar with the interface, but the author of the page seems to be assuming the user to be more technically experienced than I seem to be. Would anyone be able to give me a bit of guidance?

---

### Post by cariboo on 2008-07-28
Open a terminal and type:

```
lsusb
```

you will get a result something like this:

```
Bus 002 Device 003: ID 0665:5161  
Bus 002 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Make note of the hex id number of your device eg: 046d:08da for my webcam. Then go to this page:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

to see if the driver there supports your webgam, if so download the driver and extract it to a place you can find it. Read the READ_AND_INSTALL file. Ignore the info about recompiling the kernel, the info needed to install the module is there. Once you are done install cheese and see if it works.

Jim

---

### Post by PlutoniumBoss on 2008-07-28
It doesn't appear that my device is compatible. The identifier I got was 046d:0850 which doesn't seem to be listed there.

---

### Post by PlutoniumBoss on 2008-07-28
Looking further, I followed a link on the page you gave me to ( [www.quickcamteam.net](www.quickcamteam.net) ), which identified my device as compatible with qc-usb at ( [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) ). But again, the instructions don't seem to be intended for the novice.

---

