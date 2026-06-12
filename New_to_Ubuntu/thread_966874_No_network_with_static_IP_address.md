---
title: "No network with static IP address"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by spdaniel91 on 2008-11-01
Hey guys, I'm trying to forward ports from the router to my computer, for torrents, a server, etc.

It works fine on Windows, but on Ubuntu **(I'm using Intrepid)** I'm not sure how to set a static IP address, could anybody help me? This is the stuff I need:

IP address: 192.168.1.5
Subnet mask: 255.255.255.0
Gateway: 192.168.0.1

And OpenDns servers (208.67.222.222, 208.67.220.220).

Any help would be appreciated.

---

### Post by prshah on 2008-11-01
> **spdaniel91 said:**
> on Ubuntu **(I'm using Intrepid)** I'm not sure how to set a static IP address, could anybody help me? This is the stuff I need:
IP address: 192.168.1.5
Subnet mask: 255.255.255.0
Gateway: 192.168.0.1

Click **System**[color="blue"]->[/color]**Preferences**[color="blue"]->[/color]**Network Configuration**[color="blue"]->[/color]**Wired**[color="blue"]->[/color]**eth0**[color="blue"]->[/color]**Edit**[color="blue"]->[/color]**IPv4 settings**[color="blue"]->[/color]**Method=*Manual***[color="blue"]->[/color]**Add**[color="blue"]->[/color]**Address=*192.168.1.5***[color="blue"]->[/color]**Subnet Mask=*255.255.255.0***[color="blue"]->[/color]**Gateway=*192.168.0.1*, DNS servers=*208.67.222.222, 208.67.220.220***[color="blue"]->[/color]**Ok**[color="blue"]->[/color]**Close**.

btw, your gateway address is on a different subnet than your system ip address (192.168.1.x <> 192.168.0.x); I don't think this will work, unless you have two networks setup on the same system (in which case, select the correct eth card in the steps above), or unless you change your subnet mask.

---

