---
title: "Issue with connecting to an IPSec VPN"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by yakinikku on 2013-09-23
Hi all!  I have been having some issues connecting to my IPSec VPN tunnel I have setup at home.  I can connect to it from my phone without issues so I know the tunnel is up and working.  

To try to get this working I installed the packages vpnc and network-manager-vpnc.  I then tried setting it up using network manager.  I entered all of my information correctly and tried connecting.  No luck.  I then started duckduckgoing around and found many people were saying to add 

NAT Traversal mode cisco-udp

To the default.conf.  So I do that and when I run vpnc --debug 1 I still see "vpnc: no response from target" when trying to connect.

Then I found information about people saying to also add 

Local Port 10000 

to the default.conf as well.  Again, I try this and it fails.  I am out of ideas at this point.  Does anyone have any suggestions for me?

TIA!

---

### Post by whitesmith on 2013-09-23
You'd have better luck posting this in Networking and Wireless. I would ask a moderator to move it.

---

### Post by yakinikku on 2013-09-23
Mods, could you please move this if necessary?

---

