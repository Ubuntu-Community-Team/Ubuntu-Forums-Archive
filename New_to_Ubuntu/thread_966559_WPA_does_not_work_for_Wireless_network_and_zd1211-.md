---
title: "WPA does not work for Wireless network and zd1211-source"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Gekke Henkie on 2008-11-01
Yesterday evening I installed for the first time in my life a Unix system. Downloaded the Ubuntu 8.10 build. Burnt it on a cd and fed it into an old Thinkpad T23. Everything installed in a breeze and I had my wired networking up in no time. Browsing and e-mail are up and running. 

Next step is to go wireless. I have a Planet wl-u356 USB wireless adapter so stick it in but nothing happened. Probably a driver is missing.

Did some searching around and found that the USB thing is suport in the zd1211-source. SO how to install?

Aha, you need the Synaptic package manager! Started and found the package. Installed it and voila I had also wireless networking in the Network Manager. It even showed my network and that of the neighbours. Both have WPA security and here is where I got stuck. My router doesn't accept the connection so wireless is not working.

I dropped the security on the router and then I get a connection. So hardware wise everything is OK. Only the WAP seems to be have trouble.

So what to do next? Has anybody had this before? I got stuck.

---

### Post by scprosser on 2008-11-01
Been having the same issues myself...I had 8.04 under a Wubi install, WPAworked fine, so I KNOW it is possible on this wireless card, I did a full 8.04 install, and WPA dissapeared, then I did a full, clean 8.10 install, still no love...I cheated and just went back to WEP (and changed the settings on 4 other devices to match the new router settings) but I would REALLYprefer to be back under WPA...any Guru's out there up to a challenge?

---

### Post by Gekke Henkie on 2008-11-16
Today after startup I had for a short while wireless connection over WPA. After a while the connection died. Removal and insertion of the wireless USB-stick does not re-instantiate the connection. 

Anybody has seen this before?

---

### Post by SeePU on 2008-12-10
I've had nothing but trouble with that chipset and driver.

I've had it work only to somehow, suddenly, lose not just the connection but the availability of the network.   Nothing is getting loaded and there is no option for choosing wireless.   Usually, I would just choose my wireless connection because of the built-in scan of them but now it doesn't detect wireless at all.

This is in Hardy.  I tried a live CD of 8.10 and I could choose the wireless network and connect to mine.  But, how long is that going to be available until it 'breaks' or "disappears" as well?  :-/

---

