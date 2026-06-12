---
title: "Wireless Adapter does not use the right drivers"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by mrtalkingbadger on 2011-11-09
I'm using an D-Link DWA-126 Wireless adapter.
The Interface (wlan1) is recognized in iwconfig.
it seems to work properly since it is seen in the network indicator menu and displays all the APs  properly.

however i can't connect to them. it just keeps loading or asking for the psk (which i paste from the other interface that connects without any problem.

when i type airmon-ng it is displayed that the chipset is unknown and that it uses usb drivers.
however i found out, that it is meant to use the ath9k_htc driver wich i have installed and started using modprobe.

i have tried about every method i found on the internet to get this stupid dongle to work.
using ndisgtk, installing compat-wireless modules manually, adding ath9k_htc to /etc/modules.
in the result nothing changes.

i think the problem is, that the chipset is not recognized properly.
modinfo for ath9k_includes the ar9721.fw which tells me, that it would be used, if the according chipset would be recognized if i'm not mistaken.

is there a way to manually edit which chipset is used (or which driver)?
think this would solve the problem.

if you you need any more info just let me know.

---

### Post by Mark_in_Hollywood on 2011-11-12
Maybe this will help:


[http://askubuntu.com/questions/68326/d-link-dwa0126-usb-wifi-adapter-keeps-asking-for-a-password]("http://askubuntu.com/questions/68326/d-link-dwa0126-usb-wifi-adapter-keeps-asking-for-a-password")

---

### Post by anewguy on 2011-11-13
You probably also need to blacklist the default ath9k module.  If you lsmod you'll probably see it's there.  You could try rmmod ath9k and see if it helps.

Dave ;)

---

### Post by mrtalkingbadger on 2011-11-13
yes the ath9k is there...but what if i need it for my other wireless card?
the ath9k_htc is also there...

the problem is solved for me since i decided to return this piece of  crap to the store and instead wait a little till i'm back in germany and  can buy an alfa dongle.

still i think the problem was the unremoved ath9k...
but maybe someone has another idea?

this does not seem to be solved at aksubuntu as well.
(did u even read the thread before posting it?)

only thing i found, that could help if u have the same problem is on russian:
[http://xn--b1afc3b.net/2011/09/29/ubuntu-10-04-d-link-dwa-126/](http://xn--b1afc3b.net/2011/09/29/ubuntu-10-04-d-link-dwa-126/)

to summarize in short:
sudo apt-get install linux-backports-modules-wireless-lucid-generic (get drivers - they are already included in 11.04)
modprobe ath (acitvate the drivers)
modinfo ath9k_htc (see if it applies for the chipset ar9721)
sudo gedit /etc/modules (add ath9k_htc to this file so it is startef at systemstart)

if it still does not work
modprobe -r ath9k (remove the ath9k. if this helps blacklist ath9k)

good luck.

---

