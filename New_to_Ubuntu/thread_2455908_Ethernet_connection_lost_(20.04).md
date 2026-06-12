---
title: "Ethernet connection lost (20.04)"
date: 2020-12-30
forum: New to Ubuntu
---

### Post by deejayw on 2020-12-30
I have recently (Dec 2020) built a new machine and installed Uby 20.04 LTS (client). I have done many updates since ! I'm using ethernet only (on MSI B450 mobo), no wifi.
I shutdown the machine on the 24th and resumed on the 27th. It booted normally but there was no network activity whatsoever except for flashing port lights. ifconfig showed a 10.something ip address !)
I went into settings | network and deleted a profile that didn't seem appropriate (looked VPN like) and revealed one that did. Connectivity was restored, LAN & WAN.
Since then, I have re-booted twice (following hardware additions - SSD & USB daughterboard). On each occasion I have lost internet connectivity (LAN was fine). On both occasions, I have restored connectivity by deleting the presented profile in settings and creating a new one with fixed IPv4 and disabled IPv6.

Why is the configuration being corrupted/lost on shutdown-startup ?

---

