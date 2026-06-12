---
title: "adsl modem not working"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by bernix007 on 2008-09-03
Just installed ubuntu 8.04 on my brand new asus m50vm laptop (P45 chipset). Basics seem to work but no internet.
with ifconfig eth1: error fetching interface info:device not found.
with pppoeconf: scanned 2 interfaces,but the access concentrator of your provider did not respond.
And going to hardware drivers: no proprietary drivers are in use on this system.
Needless to say that I dont understand spit to all this. But would be quite disappointing to revert to vista just because I'm no computer buff...
bernix007

---

### Post by paul_mcl on 2008-09-03
maybe ifconfig eth0?
maybe tell us how 've you set up this in your windows?

---

### Post by oilchangeguy on 2008-09-03
> **bernix007 said:**
> Just installed ubuntu 8.04 on my brand new asus m50vm laptop (P45 chipset). Basics seem to work but no internet.
with ifconfig eth1: error fetching interface info:device not found.
with pppoeconf: scanned 2 interfaces,but the access concentrator of your provider did not respond.
And going to hardware drivers: no proprietary drivers are in use on this system.
Needless to say that I dont understand spit to all this. But would be quite disappointing to revert to vista just because I'm no computer buff...
bernix007

your wired connection should be eth0. and if you have wireless it's wlan0. try unplugging the modem, let it stay turned off for at least a minute, and reboot the computer, and turn the modem back on.

---

### Post by bernix007 on 2008-09-03
unplugged modem (speedtouch st516v6), rebooted. Now with ifconfig eth0:
link encap:Ethernet HWaddr 00:22:15:37:1b:99
inet 6 addr: fe80::etc... Scope: Link
Up broadcast running multicast MTU:1500 
...
interrupt:248 Base address 0x000
I guess he detected something...
Nevertheless, sudo pppoeconf gives same answer...
Thanks, and let's keep on trying...
Bernix007

---

### Post by bhadotia on 2008-09-03
I think there are some drivers for speed touch modems in synaptic (and as far as I can remember some community tutorials on the net too ). I have an adsl modem at home (at the hostel I use my university's wireless network) and it shows up as ppp0 after I have configured it.
The modem is ZTE and has three (or four- don't remmember) LEDs one of which lights up when the power is turned on, another when it has gained access to the cocentrator and the last when I'm connected to internet.
The sudo pppoeconf won't gain accees to the provider if my second (of the above) LED is not fully light (it blinks first).

Also, you can see the yelp help page regarding 'connecting to the internet' its got some useful links.

---

