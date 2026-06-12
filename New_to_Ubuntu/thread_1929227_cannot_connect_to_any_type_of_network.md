---
title: "cannot connect to any type of network"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by philmacdonald2 on 2012-02-21
:confused::confused::confused:

I've had Ubuntu 11.10 for a few days now, and on install it detected my Netgear WG111v3 USB wireless network adapter, and I could access the internet. Now, for some reason, the networking interface doesn't seem to do anything. Under Wireless connections, I just get "Device not managed" and wired connections do not give a connection to the internet, even though they should do (I used a different PC running Win7 to check to see if a wired internet connection could be achieved before trying to get one on the Ubuntu one).

I've probably somehow managed to break the network settings. Any help to solve this would greatly be appreciated :D

---

### Post by philmacdonald2 on 2012-02-21
The ifconfig command doesn't show the wireless connection anymore, which confuses me, but I don't know how to fix it... :confused:

---

### Post by kazztan0325 on 2012-02-22
Hi philmacdonald2,

I would like to suggest you would try to install **"wicd (wired and wireless network manager)"** with Synaptic or Software Center.

---

### Post by grahammechanical on 2012-02-22
You need this guide:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

You should also understand that in the past it was customary to edit the /etc/network/interfaces file but since Network manager became the default network management tool it is not necessary to edit that file and in fact editing it will stop you from getting network connections.

It is also not advisable to have two or more network management utilities installed at the same time. It causes conflicts.

Use Gedit to open /etc/network/interfaces and see what is in that document. It should only have

> auto lo
iface lo inet loopback

Anything else will prevent Network Manager from managing you network connections. With Network Manager installed we must use Network manager to edit connections otherwise things stop working.

Regards.

---

### Post by philmacdonald2 on 2012-02-22
I couldn't install WICD even if I wanted to because I have no network connection at all... even ethernet doesn't work...

I'll check the interfaces file and see what is contained. I have a feeling that other things may have appeared there. Thanks for the troubleshooting guide, I was trying to fix it with that now... I'll get back to you when I see what was wrong.

---

### Post by philmacdonald2 on 2012-02-22
Ok, so the wireless adapter now shows signs of life, and there were a few more lines in that file that I deleted, added what you said, and then rebooted and the light flashed on the USB adapter (before it wouldn't even power on). I now, however, can't move my mouse at all... so I wonder:

1) How do you connect to a wireless network using terminal commands (so I can test to see if it works)?
2) How do I get my mouse to work again?

Seems like my hardware has a strange habit of working and not working again...

---

