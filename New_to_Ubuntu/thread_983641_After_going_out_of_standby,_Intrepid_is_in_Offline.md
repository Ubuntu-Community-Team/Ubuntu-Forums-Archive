---
title: "After going out of standby, Intrepid is in Offline Mode?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-11-15
Often, whenever I go out of standby, my HP dv2000 is in offline mode, and the network manager icon has a ! and says networking disabled if I click on it. It's not a huge problem, since switching in and out of standby seems to fix it, but is there an update or anything to fix the networking? Because, besides doing this, sometimes it will also connect to not only the ethernet connection, but also a public wireless connection. This CAN sometimes have some problems. In addition, I'm no expert on wireless connections, but I'm worried that if it connects to the ethernet connection and also the wireless public connection, that anyone also on the wireless connection will be able to see what I'm viewing online. Any help? Thanks.

---

### Post by Sava8420 on 2008-11-15
Even Vista will switch to offline mode in standby.  That is normal.  If your concern is only about the wireless connection, then simply disable wireless.  There are a couple of ways to do that either through Network Manager or through the terminal.
```
sudo ifconfig wlan0 down
```
that will disable the wireless connection.

---

### Post by Watchtow3r on 2008-11-15
and up re-enables it?

---

### Post by Sava8420 on 2008-11-16
> **Watchtow3r said:**
> and up re-enables it?

That would be correct. 
```
sudo if config wlan0 up
```
If it gives an error about wlan0 then use 
```
sudo ifconfig
```
that will show you all your connections then replace wlan0 with the name of your wireless connection.  If you run that it should show you two wlan0 and wlan:Master you want to use wlan0 always.  wlan:Master is not a physical device.

---

