---
title: "[SOLVED] How do I change my eth0 to DHCP?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by suomalainen on 2008-08-31
Ubunteros,


During Ubintu install, I set my eth0 at static IP. I want to now set it to DHCP.

How is this accomplished?

Thank you

---

### Post by rogeriopvl on 2008-08-31
You should have a network icon near the clock, click it and select "manual configure". There you can configure all your connections.

---

### Post by cdtech on 2008-08-31
You would need to change your interfaces file:
sudo gedit /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface **eth0** inet **dhcp**
```

---

### Post by suomalainen on 2008-08-31
Thanks for the info. I guess I'm still doing something wrong. 

Here's what I'd like to do.

I have a Western Digital, "my Book World Edition" and want to be able to see in under "Connect to server".

But this isn't happening. Online I have found things about this problems, or being able to do thius, but everything seems so technically oriented that I'm lost rather quickly.

Help and suggestions always appreciated.

Thank you

---

### Post by fidamehran on 2008-08-31
Let me see if I got you right. You configured a Static IP in the beginning. Now you want DHCP with no IP config.
"rogeriopvl" solved your problem I guess. Click (left click) the networks icon on top right and select manual configuration.
Click unlock and give your password. Then Click Wired Connection--> Properties. Then change the setting.

---

