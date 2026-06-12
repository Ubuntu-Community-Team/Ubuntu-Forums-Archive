---
title: "Network Issues"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by dolphin194 on 2011-11-18
I have this Dell PowerEdge 2650 that I got from a company that was originally going to send the computer to a recycling plant. I decided that I want to run a Minecraft and Team Fortress 2 server on it, and started to get it going.

I began by slapping Ubuntu 10.04 LTS Server on it. I then installed the basic Ubuntu desktop interface by using the command ```
sudo aptitude install --without-recommends ubuntu-desktop
``` and installing an Open SSH server on it.

After rebooting the machine, I installed the Network Connection manager (System>>Preferences>>Network Connections) to configure the network to use a Static IP.
[B]
This is where the real trouble began.[/B]

At first, the network connections window didn't have the automatic configuration for my LAN cards, so I rebooted the machine. They appeared in the window, and I edited the configurationfor the cards, and ticked the "Available to All Users" box at the bottom. That caused the configuration to disappear, and when I run ```
ifconfig
```, it will not tell me the IP address used by the card.

---

### Post by dolphin194 on 2011-11-21
Bump

---

