---
title: "Newbie and Atheros AR5007 Wireless"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by mt_100 on 2008-09-07
I've installed Ubuntu 8.04 32bit (I didn't want to experience extra problems from 64bit) on my Compaq C751NR that has the Atheros 5007 wireless but cannot get the wireless installed.

I have followed the step by step instructions in a few threads I found here but none seem to work for me.

Beginning to feel a little dumb to be honest ;). Hell, in the MS world I admin MS AD, Citrix, and many more all day but this linux things is kicking my butt. Love the challenge though.

So, are there some more updated instructions to follow or changes that I need to do? Maybe a new step by step instruction or something?

---

### Post by Sameer kumar on 2008-09-07
Type in:

sudo ifconfig -a

check if your wireless card is detected(ur mac id would be shown)

use 
ifconfig ath0(wlan) up/down(to on/off your wireless)
dhclient ath0(wlan) (to obtain an ip)
(refer man pages of ifconfig & iwconfig for details)

If your wifi led is not working, just edit /etc/sysctl.conf:
type gedit /etc/sysctl.conf and add this at the end of the file and save 
dev.wifi0.ledpin=1 
dev.wifi0.softled=1 
reboot!!!!!!!!!!!!!!

---

### Post by mt_100 on 2008-09-07
It's not detected.

There is a icon that says restricted drivers are in use with mention of Atheros but I cannot for the life of me get it to work.

---

