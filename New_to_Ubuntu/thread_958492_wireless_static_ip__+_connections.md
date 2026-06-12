---
title: "wireless static ip ? + connections ?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by garyed on 2008-10-25
I have two questions.
1 - I edited my /etc/network/interfaces file to make my wireless laptop ip static so I can connect with my other computers easily. The problem is it connected to my neighbor's unencrypted router & I couldn't find a way to disconnect from his router & reconnect to mine like I do when I don't use static ip because there's no other wireless options available. I'm thinking maybe static wireless ip is not practical.

2 - I use auto logon when I boot up so is there a way to make sure I always boot to my router no matter how many are available? I have two neighbors with unsecured networks in range.

---

### Post by codeking on 2008-10-25
as far as i know theres no such thing as a static wireless ip.  static IPs are purchased from your ISP, and usually are only used by servers/hosts

can't you just click the wifi signal strength icon on the top right and select which connection you want to use?

as for two, it should automatically select the previous selected network

---

### Post by garyed on 2008-10-25
> **codeking said:**
> ..can't you just click the wifi signal strength icon on the top right and select which connection you want to use?

as for two, it should automatically select the previous selected network

When I edit my interfaces for static ip the wifi signal strength icon doesn't show up any more, just the manual configuration icon & I can still get online so I know my wireless is working. When I run iwconfig it shows my neighbor's 
router name.
As for the other thing, I have to constantly check to see what router I'm on
because I never know. My daughter's Windows laptop has the same problem in the house but windows is another story.

---

### Post by melojo on 2008-10-25
I connect my wireless card manually.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I created a file call net.sh

```

#!/bin/sh -e
#script to start wireless network
dhclient -r wlan0
ifconfig wlan0 192.168.2.5 netmask 255.255.255.0 up
route add default gw 192.168.2.1
iwconfig wlan0 essid "belkin54g"
iwconfig wlan0 key XXXXX
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
#dhclient wlan0

```
made sure it was set to executable
added it to /etc/rc.local above the exit line
make sure the rc.local file is set to executable 

I may have had to remove gnome-network-manager

---

### Post by mikewhatever on 2008-10-25
Have you also entered your network name and correct gateway?


> **codeking said:**
> as far as i know theres no such thing as a static wireless ip.  static IPs are purchased from your ISP, and usually are only used by servers/hosts

You can ask for a specific (read static) ip from the router, while the ISP stays with DHCP.

---

