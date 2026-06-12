---
title: "Mobile Dongle connection to internet"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Grandad David on 2008-11-09
I live in a non-broadband area and use a dongle connection to the internet, (via Orange). The software for this is all Windows based and does not support Linux, so I have to connect to Ubuntu via Windows. Does anyone know of software that will let me connect in this way via Ubuntu Linux.
Thanks

---

### Post by Peter09 on 2008-11-09
Post the model number of the dongle, often there is more S/W than you think, but nobody can help you if we do not know the hardware that you have.

---

### Post by davideotape on 2008-11-09
I would advise getting the latest live CD and booting from it on your laptop. This will not change any thing on the computer, but it will allow you to test the dongle. Just plug the dongle in when the live CD has booted up and see what happens...

If it works, great.
If it doesn't I'm not sure if there is any way of getting it to work.

---

### Post by Grandad David on 2008-12-05
I have a dongle supplied by orange which is labelled ICON 225, but Ubuntu seems to recognise it as a Globemaster modem. I can't find any refs to orange dongles, but they are the only ones which have any signal strength here in mid-Wales (and its NOT 3G)
Thanks in advance for suggestions

---

### Post by TpyKv on 2009-04-16
Which version of Ubuntu are you using? 

The actual (HSO) driver is installed in Intrepid 8.10, and the network manager is 3G - enabled... you just need to go here 

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

and follow this guide to install "ozerocdoff" - this stops your modem working as a storage devince (where the windows/mac files are located) and makes it work as a modem.

You have to plug the device in after the system boots, mine doesn't work when you leave it in and then boot up..

Paul at Pharscape should be given a medal....

Let us know how you get on!

---

### Post by Grandad David on 2009-04-16
Thanks for your suggestions, although things have moved on a bit. Namely I have to have a new disk to install latest Ubuntu, since I have run out of space on my old one. Still I appreciate your comments and will explore further

---

### Post by TpyKv on 2009-04-17
You can upgrade to the latest one - and keep your current settings - if that is easier? or save everything important somewhere else, and wipe the disk, and start again?

good luck in whatever you choose!

---

### Post by Houssema on 2011-01-11
Hi, I could find the procedure that makes it work [here]("http://www.amazing-tutorials.com/linux/configure-huawei-e1752-dongle-orange-ubuntu/")

have a look and tell me if it works for you.

---

