---
title: "odd incompatibility between ubuntu and my wireless router?"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by snowguy on 2011-10-23
I need help as to where even to start troubleshooting this problem.

I've got a new laptop and I put Ubuntu 11.10 on it. I can connect through Ubuntu with a wired connection to the network with no problem. I can load Windows 7 on the laptop and connect wired or wireless with no problem. I can connect through Ubuntu wireless to my neighbors network, no problem. However, when I connect to my own router wireless it works for a few seconds to maybe a minute and then causes the router to stop working completely. No wired or wireless connections work. The solution at that point is to reboot the router. Once reboot, the router will work fine with lots of other devices connecting to it (though none other happen to be running ubuntu connecting wireless). Then as soon as I connect this laptop under ubuntu wireless the problem happens again. 

So it seems like there is some incompatibility between Ubuntu and my router. I've got a netgear router running dd-wrt. Any ideas what to try to resolve this? 

I'm running ubuntu 11.10 32 bit.

I'm really stuck with this one and could really use some help. thanks in advance.

---

### Post by KL_72_TR on 2011-10-23
Take a look at one of these, maybe you can find something:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by snowguy on 2011-10-24
I took a look at the links. They were helpful in that I was able to determine what wireless card I have, namely: Intel Corporation Centrino Advanced-N 6205 AGN

Also I did find a work around to this problem. I disabled "n" on the router side so that it will only allow b & g connections. Once I did that things started working just fine from my laptop.

This leads me to two questions. 

(1) Does anyone know how to disable "n" on the ubuntu client side so that I can allow n type connections for other computers on the network?

(2) Any suggestions on how to solve this so I can use "n" on this laptop while in Ubuntu?

---

