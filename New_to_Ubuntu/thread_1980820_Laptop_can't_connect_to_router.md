---
title: "Laptop can't connect to router"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Victoriousness on 2012-05-15
I just installed Ubuntu on my laptop. The wireless card wasn't working, so I had to do a bunch of ndiswrapper stuff and blah blah blah. After much tinkering, I finally got the wireless to work, and I can now see the different networks around me. But when I try to connect to my network, the little icon keeps trying but then gives up and a window pops up asking me for my password.

I'm definitely close enough to the router, and I know the password is correct, because I can connect to the router with my phone and other laptop using the same settings. Does anyone know what's going on here?

Btw, the network is a hidden network, but it looks like the wireless card recognizes it. Also, my card is Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01). I believe it's called Dell 1390 WLAN MiniCard.

---

### Post by Sidmaker on 2012-05-15
> **Victoriousness said:**
> I just installed Ubuntu on my laptop. The wireless card wasn't working, so I had to do a bunch of ndiswrapper stuff and blah blah blah. After much tinkering, I finally got the wireless to work, and I can now see the different networks around me. But when I try to connect to my network, the little icon keeps trying but then gives up and a window pops up asking me for my password.

I'm definitely close enough to the router, and I know the password is correct, because I can connect to the router with my phone and other laptop using the same settings. Does anyone know what's going on here?

Btw, the network is a hidden network, but it looks like the wireless card recognizes it. Also, my card is Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01). I believe it's called Dell 1390 WLAN MiniCard.

As i can see you have the same problem like i had couple weeks ago,
So in general the problem in your wireless driver - pay attention on vendor (**Broadcom Corporation BCM4311**)
So how it can be fixed ?
The are two ways for my opinion: 

[LIST=1]
[*]Try reinstall wireless driver manually ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access") hope will help)
[*]Try install new Ubuntu distribution (12.04 recommended)
[/LIST]
Additional information about point 2:
I have tried install Ubuntu 11.10 after 10.04 (I didn't fix this problem in 10.04). The problem didn't disappear for 11.10 i did point 1). After so called trick and dancing with tambourine around my laptop the wireless works fine, then i migrated on 12.04 and as you can see everything fine ;)

Also see [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)


Hope it will help you ;)

---

### Post by Lisiano on 2012-05-16
Found you. Should have asked us first. There is no need to do those ndiswrapper stuff. Since you just installed, could you reinstall again to revert all the ndiswrapper changes?

After that all you need to do to get your WiFi adapter working is to use this command in a terminal (To open it, press Ctrl+Alt+T).
```
sudo apt-get install [firmware-b43-installer](apt://firmware-b43-installer)
```
OR you can just [click here](apt://firmware-b43-installer) to install it. Then reboot and you are done.

---

### Post by Victoriousness on 2012-05-16
Hey, thanks for the responses. I now realize that I didn't need to do the ndiswrapper stuff. I'll try to reinstall Ubuntu tonight and do that line of code.

After I install b43, I'm supposed to select it from the list at System Settings > Additional Drivers, correct?

---

### Post by Lisiano on 2012-05-16
If you see it available in additional drivers, you should first install it from there, if it doesn't then run my commands.

---

### Post by Victoriousness on 2012-05-16
It works now!!! Thanks, Lisiano and everyone else who helped!

---

### Post by Lisiano on 2012-05-17
Glad it works! Way easier than using ndiswrapper, no? :3

---

### Post by Victoriousness on 2012-05-17
Absolutely! It's unfortunate that I wasted all those hours trying to get it to work, but at least now I have that skill if I ever need it.

---

