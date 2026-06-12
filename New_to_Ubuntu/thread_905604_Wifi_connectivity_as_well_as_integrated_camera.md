---
title: "Wifi connectivity as well as integrated camera"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by ronferds on 2008-08-30
Hi,

How do i monitor my wi fi on my laptop with ubuntu 8.04? I plan to connect my present Internet plan to a wifi enabled modem. So How do i configure it and give my system a password?

I have an integrated camera, how do i use it? :)

---

### Post by pytheas22 on 2008-08-30
If your wireless card is correctly configured (depending on which model it is, it may or may not have been automatically set up when you installed Ubuntu), you should be able simply to left-click on the Network Manager applet (looks like two computer screens and should be in the top-right corner of the screen), which will display a list of available networks.  Click the one you want to connect to, and it will prompt you for the passphrase if necessary.

If you don't see any wireless networks mentioned in Network Manager, then your wireless card is probably not set up.  Please post the output of these commands so that we can tell you how to make it work:
```

lshw -C Network
lspci -nn
lsusb
iwlist scan
```

As for the camera, take a look [here]("https://help.ubuntu.com/community/Webcam") (I assume you are referring to a webcam; if not, please let me know what you mean by "integrated camera").  Webcams should also "just work" in Ubuntu, but some models require extra work to get them installed.

---

