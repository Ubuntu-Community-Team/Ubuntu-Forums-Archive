---
title: "No wired connection"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by mnettrour on 2012-06-13
**SOLVED see last two posts**

All previous post see the link: running Ubuntu 10.04 
[http://ubuntuforums.org/showthread.php?t=1994624](http://ubuntuforums.org/showthread.php?t=1994624) tried all suggestions, currently the results of nm-tool are the same wired connection not available.
I tried unplugging the ethernet cable, restarting the router, then shutting down the computer, restarting and plugging the network cable back in. The router is working supplying wireless and a cable connection to a Windows system.
 
Tried sudo /etc/init.d/networking restart says if worked and had me go into etc/networkmanager/networkmanager.conf and edit ifupdown and make sure it said false. I had changed it to true as you can see from the previous thread.
 
Then tried sudo dhclient and it was unable to get a lease which was probably stupid considering the system cannot see the wired connection.
 
Appreciate any help. Thank you.

---

### Post by steeldriver on 2012-06-13
let's see exactly which card(s) you have

```
lspci -nn | grep "\[0200\]"
```

---

### Post by mnettrour on 2012-06-13
It returns RTL8111/8168b (Realtek)  nm-tool thinks it is a r8169. Do you think it is a driver problem?

PS just to save another beginner some trouble the correct line to find out what card you have is:

lspci -nn | grep "[\0200\]"

---

### Post by mnettrour on 2012-06-13
Steeldriver, found the problem. Driver indeed. [http://ubuntuforums.org/archive/index.php/t-1661489.html](http://ubuntuforums.org/archive/index.php/t-1661489.html) If you go to the end of this post, you unplug the machine and it sees the network card again. Now I just have to blacklistth 8169 driver and install the 8168B which I downloaded. Although by reading the post this is going to be a recurring problem with this realtek card. Sounds like it is better to by an intel NIC card install it in a slot and use it instead. It is 2 am here and two tired to move the driver over to the ubuntu box so in the morning should have it fixed. Thanks for your help. This is a known bug since 2007, maybe they will fix it and it is probably causing the network connection problem that many are having with 12.0. Best. Mike

---

### Post by mnettrour on 2012-06-14
For whatever reason after following all the quite correct help, in the link in my reply above, It would not work on eth0 under any conditions. Just for grins I tried wired connection 1 it is working with automatic DHCP addresses only selected and the DNS as my router 192.168.1.1 Just for curiosity tried that for eth0 no dice. I did go into ifupdown and changed managed to true,  but suspect that it will work with false also. My advice is as noted in the link in my reply above. Buy a intel network card install it in the slot and you won't have to go through all the hassle the next time a ubuntu update that addresses networking takes place. The realtek 8168 built into the mb does not play well with Ubuntu. My fun meter is pegged, I want to use my computer not become a Ubuntu expert.  BTW, I built this machine and while not a Linux expert have been with computers since the old IBM 360's back to back configuration in my high school data center circa early seventies. Now if I can make this thing talk to my windows network, share files and a printer, I might not wipe it out and replace it with XP. 
**I really appreciate steeldrivers help he got me on the right path.** It was fairly easy to load the 8168 drivers and blacklist the 8169. Why it does not work with eth0 would be a good science project but happy to have it work on wired connection 1.

---

