---
title: "Getting wireless working on Inspiron E1405"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by lagamemnon on 2008-10-03
Hi, I just installed Hardy Heron but my wireless card is not working, i.e. I'm not seeing any wireless networks although the light for the wireless card is on. I think that the card may be somehow disabled... but there is no button to "enable" it as in Windows. How do I do this? Thanks.

---

### Post by Ryadt on 2008-10-03
Go in System > Administration > Hardware Drivers and if it's in there, enable it.

---

### Post by phidia on 2008-10-03
What wireless card are you trying to get working? Some cards need additional configuration (ndiswrapper or madwifi) to work.
If you open a terminal and enter > lspci -v that should show your wireless card. You can also use the wiki [here]("https://help.ubuntu.com/community/WifiDocs?highlight=%28CategoryWireless%29") to go further with setting it up.

---

### Post by lagamemnon on 2008-10-04
There is nothing under hardware drivers.

So when i type in lspci, I get:

Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI

Is there something special I need to do with this card? I tried looking at the wiki but I got lost pretty quickly. I'm pretty new to the whole Ubuntu thing. Thanks for the help.

---

### Post by Ryadt on 2008-10-04
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM94311MCG](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM94311MCG)

---

### Post by Big_Kahunaca on 2008-10-04
> **Ryadt said:**
> Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM94311MCG](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM94311MCG)

Actually, I have the same wireless adapter and while the above method may work, there is a way to do it without using ndiswrapper.

The new version of Ubuntu includes the Broadcom-supplied driver, and can be installed using the following link...

[http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218")

Works like a charm on the Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

---

