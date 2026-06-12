---
title: "[SOLVED] Autostart wireless in Zenwalk"
date: 2007-12-13
forum: Other OS Talk
---

### Post by Telecaster72 on 2007-12-13
So i decided to try out Zenwalk for a while, i like the speed and snappiness, i dont like the packagemanager compared to the wealth of ubuntus synaptic though;-)
I figured the only way to learn linux is to go cold turkey from ubuntu for a little while and get my hands dirty by compiling...

I cant get wireless to start automatically when i boot.

I compiled the latest madwifi from source (very proud) and my wireless works and i get an IP address when i type:
"ifconfig ath0 up"
and
"dhcpcd ath0"  (as root)

Can i make some kind of script using that and put it in autostart?
The included wireless utility Wifi-Radar does not work very well for me and ath0 does not show up in the regular network manager.

Any suggestions are welcome!

---

### Post by Telecaster72 on 2007-12-13
It works now, i had to add ath0 to
/etc/rc.d/rc.inet1.conf 

by adding this:

# Config information for ath0 (using dhcp):
IFNAME[1]="ath0"
IPADDR[1]=""
NETMASK[1]=""
USE_DHCP[1]="yes"
DHCP_HOSTNAME[1]=""

...off to fix the loginscreen resolution...

---

