---
title: "Weak wireless reception?.."
date: 2009-08-03
forum: Philippine Team
---

### Post by killer_d76 on 2009-08-03
i just noticed early this morning when i discovered an Open  Wireless Connection courtesy of my kapitbahay (i have informed him about this already and thought him how to secure his wireless connection) the signal was detected by my wireless card (broadcom wireless card) when i tried to connect to it using jaunty.. it failed to connect... i booted to OSX and tried to connect to the same wireless connection and "boom"!.. i was getting a very good signal and i was able to surf a few sites... then reboot back to jaunty (sigh) :( can't seem to connect to it again...

take note that the test was done using a Neo Empriva Laptop (dual boot with Ubuntu Jaunty and Mac OSX ) using the stock broadcom wireless card.

---

### Post by loell on 2009-08-03
would you know the specific chipset of your broadcom?

---

### Post by killer_d76 on 2009-08-04
it's a Broadcom 3945.. by defualt it is detected by Jaunty.. not unlike Gutsy that i have to install its firmaware (provided by you loell!.. thanks).. i was just wondering maybe it's because of the default/bundled wireless firmware on ubuntu jaunty?.. :confused:

---

### Post by loell on 2009-08-04
seems a know issue in jaunty,
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/348204]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/348204")

the overall concensus is to use **wicd** instead of network manager.

---

### Post by pinoyskull on 2009-08-05
> **loell said:**
> seems a know issue in jaunty,
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/348204]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/348204")

the overall concensus is to use **wicd** instead of network manager.
+1 to that

and also check which encryption it uses

---

