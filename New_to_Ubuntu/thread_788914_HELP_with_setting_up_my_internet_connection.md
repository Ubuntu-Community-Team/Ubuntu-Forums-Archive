---
title: "HELP with setting up my internet connection"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by franzrebs on 2008-05-10
I just installed Xubuntu 8.04 last night and since then I've been having trouble connecting to the internet, which is seriously starting to tick me off.

I use a Speedtouch 330 ADSL USB modem. I installed it with the setting PPPoE 0-35 LLC in windows and it's working all right. I don't know much about configuring my network settings so I tried all the methods available.

I went to Applications - System - Network. I tried enabling the first option and the little Network icon at the top didn't show the exclamation mark but I couldn't connect to websites through Firefox. I then tried the second option but an exclamation mark appeared on the Network icon.

I tried doing this:
```
sudo pppoeconf
```
and they detected 'eth0' but couldn't enable it.

I tried following [this guide.]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch") but 'THOMSON' couldn't be found in given directory.

I inserted my modem's accompanying CD but wasn't able to run the setup.exe because I couldn't find wine (even though I did *sudo aptitude install wine*.)



I really want this to work as I'm very eager to start using Xubuntu as my main OS, so please, can somebody guide me through the steps? I would be forever grateful. :KS

And tell me if you need more information about my modem.

---

### Post by brettg on 2008-05-10
This;

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)

may help.

Of course the best solution is to grab an external "router" (in quotes because most consumer grade kit are NAT gateways and NOT routers) and do away with all the pain of having to connect to the net every time you boot up, but it's  your call.

---

### Post by franzrebs on 2008-05-10
> **brettg said:**
> This;

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)

may help.

Of course the best solution is to grab an external "router" (in quotes because most consumer grade kit are NAT gateways and NOT routers) and do away with all the pain of having to connect to the net every time you boot up, but it's  your call.
The .deb file can't be installed. I get an error-

Dependency is not satisfiable: python-gnome2-extras.

How to fix this? :(

---

### Post by franzrebs on 2008-05-10
Never mind, I got it working already. Thank you so much brettg!

---

