---
title: "Compaq Presario 2500 wireless problems"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by MaddoxBT on 2008-07-29
First time installing Ubuntu (wubi) and I am having a problem getting the wireless to work. I have a Compaq Presario 2500 series with a Broadcom BCM4306 wireless LAN controller and a Linksys Wireless-G Speedbooster (I forget the model number) router running WEP 64-bit hex 10 security. 

I tried clicking the little network computer thing and entering my code and no dice. So I tried manual config, and again no dice. My router SSID doesn't show up, though I have it set to broadcast and the card picks it up in Windows just fine. So the card is fine and the router is broadcasting the SSID just fine as well. I know I entered the hex key correctly, as I entered all four of the hex keys my router generated twice each just to be sure.

I tried following the directions on the how-to manual networking thing here at the forums, but it didn't work. What do I do?

Couple things that might be the problem...

1. When I ran sudo lshw -C network, it shows *-network DISABLED. I don't know how to "ENABLE" it though. The help section says to go to system -> preferences -> hardware information, but I don't have hardware information in my system/preferences.

2. DHCPDISCOVER is apparently looking at 255.255.255.255 and it says that the server is down, but my subnet mask is 255.255.255.240. Is that a problem? If so, how would I change it.

If I forgot to include any pertinent information, I'm sorry. Very new to this. Thank you for any help.

---

### Post by MaddoxBT on 2008-07-30
Anyone?

---

### Post by MaddoxBT on 2008-07-30
Nevermind, did it myself.

For me, it was as easy as downloading the firmware here:
[http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb](http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb)

And just installing it. Simple as could be.

I am the man.

---

