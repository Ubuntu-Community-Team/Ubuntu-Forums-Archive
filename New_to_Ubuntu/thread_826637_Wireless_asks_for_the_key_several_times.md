---
title: "Wireless asks for the key several times"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by andriy.kostyuk on 2008-06-12
Sometimes the computer connects to the wireless net automatically after I log-in. 
But sometimes it does not. Moreover, sometimes I have to tell it to which net it should connect several times. And each time it asks me for the key.
Is it possible to fix it?

---

### Post by Flag on 2008-06-12
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
Same problem here and elsewhere I guess.
That's what I use to get connected, am using an Acer Aspire 7520 with an Atheros 5007 wifi card, driver 5211.

---

### Post by ubume2 on 2008-06-12
Network Manager can be buggy.  I gave up on using System>Administration>Network, and manually installed the network instead.  This involves editing two files /etc/network/interfaces and /etc/rc.local

For a start see kevdog's HowTo Manually Configure Networks:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Another useful HowTo is in regard to setting up WPA by Wieman01. It does have some information on setting up wireless.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

The first thing to do is to check /etc/network/interfaces to see if your device is in there. Follow **Wieman01**'s instructions "Now Let's get started"
number 1 & 2. 

Then you could try to manually connect from the command line, to see if your connection is more reliable. The commands depend on which type of security you use:WEP,WPA, etc. See **Kevdog**'s HowTo.> sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "Routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>


If that results in a more reliable connection you can put those commands into your /etc/rc.local file. Take the sudo commands out.
My rc.local file was inactive so I had to give the permissions using chmod.

---

### Post by ukripper on 2008-06-12
> **andriy.kostyuk said:**
> Sometimes the computer connects to the wireless net automatically after I log-in. 
But sometimes it does not. Moreover, sometimes I have to tell it to which net it should connect several times. And each time it asks me for the key.
Is it possible to fix it?

in terminal type following
```
sudo gedit /etc/rc.local
```

A file will open up

Add the following before exit 0 
```
/etc/init.d/network restart
```

make sure above is added before exit 0 and then reboot.

---

