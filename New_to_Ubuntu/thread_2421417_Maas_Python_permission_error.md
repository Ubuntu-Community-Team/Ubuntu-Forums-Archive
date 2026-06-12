---
title: "Maas Python permission error"
date: 2019-06-21
forum: New to Ubuntu
---

### Post by hgkrug1 on 2019-06-21
I have installed Maas (region contoller) on a PC (Ubuntu 18.10 - desktop).  I was able to get the web gui going and was busy with setting up the Vlan etc.  When I rebooted, the Ubuntu desktop froze upon startup giving a list of messages about maas-server/pyhon errors (Permission denied).  A screenshot from the error message is atatched.

Another point, I thought it would have been appropriate to post this message under the "Ubuntu Servers, Cloud and Juju" forum section, but I see I am not allowed to post there?

So the screen is frozen, I cannot get further.  I can SSH into the system.

Apologies for my ignorance! And thanks for your help.
Gert Kruger

---

### Post by hgkrug1 on 2019-06-21
I was able to determine that Maas is not running:

$ sudo systemctl status maas-dhcpd
maas-dhcpd.service - MAAS instance of ISC DHCP server for IPv4
Loaded: loaded (/lib/systemd/system/maas-dhcpd.service; enabled; vendor prese
Active: inactive (dead)
Condition: start condition failed at Fri 2019-06-21 12:43:04 SAST; 4s ago
&#9492;&#9472; ConditionPathExists=/var/lib/maas/dhcpd.conf was not met
Docs: man:dhcpd(8)

The command to restart Maas, does not help. ($ sudo systemctl restart maas-dhcpd) 

Hope that helps.
Gert Kruger

---

