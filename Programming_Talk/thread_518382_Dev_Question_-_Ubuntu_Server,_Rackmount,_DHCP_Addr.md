---
title: "Dev Question - Ubuntu Server, Rackmount, DHCP Address"
date: 2007-08-05
forum: Programming Talk
---

### Post by SuperMike on 2007-08-05
Let's say I want to build a rackmount server appliance with Ubuntu Server on it. And, to make it easy for someone to administer, I make it come up on DHCP (DHCP client) initially, but then let some administrator connect to its website after that and set it to a static IP address.

The expensive way to handle this is to get a rackmount appliance with a small LED character panel on the front that permits me to show the current DHCP address so that the admin can find it on the network. That's the coolest way, but probably not that affordable when I'm trying to maximize profit.

However, what's the cheap way to do this? I mean, is there a Java Swing app or something like that (which can work in both Windows, Mac, or Linux) that lets one see where this server arrived on the network? Or, is there a command that one can type on Windows, Mac, or Linux that permits them to see it if the server were to send out some kind of signal to the network?

I figured I should ask developers this question -- I hope I posted to the proper forum.

---

### Post by AlexThomson_NZ on 2007-08-05
Sorry, why can't the admin find it by name, rather than IP adress?

---

### Post by SuperMike on 2007-08-06
> **AlexThomson_NZ said:**
> Sorry, why can't the admin find it by name, rather than IP adress?

Good thought. Some DHCP servers will automatically register the DNS. Therefore, if the Windows, Mac, or Linux workstation shares that same DNS, you should be able to ping it by name to get the IP. However, if your workstation doesn't share the same DNS in your corporate environment, or if your DHCP server doesn't automatically register the DNS, it won't work.

It's like the server needs a companion tool that can detect its presence (and therefore IP) on the LAN.

---

### Post by cwaldbieser on 2007-08-06
> **SuperMike said:**
> Good thought. Some DHCP servers will automatically register the DNS. Therefore, if the Windows, Mac, or Linux workstation shares that same DNS, you should be able to ping it by name to get the IP. However, if your workstation doesn't share the same DNS in your corporate environment, or if your DHCP server doesn't automatically register the DNS, it won't work.

It's like the server needs a companion tool that can detect its presence (and therefore IP) on the LAN.

Would the appliances all be on the same LAN?  If so, you might be able to have their MAC addresses printed on the outside (since these do not change).  Then if you ping one from a computer on the same LAN, you could look up its MAC address with "arp".

---

### Post by SuperMike on 2007-08-06
Fascinating. Now we're cooking with grease. So if, while this server is on DHCP, and only while this server is on DHCP, it pings once every 15 seconds to one random address in the same subnet, then a workstation in that same subnet can pick it up if it either has GNU arp for Windows, or arp for Mac/BSD Unix, or Linux. Can you show me how the arp command syntax would look?

---

### Post by cwaldbieser on 2007-08-07
> **SuperMike said:**
> Fascinating. Now we're cooking with grease. So if, while this server is on DHCP, and only while this server is on DHCP, it pings once every 15 seconds to one random address in the same subnet, then a workstation in that same subnet can pick it up if it either has GNU arp for Windows, or arp for Mac/BSD Unix, or Linux. Can you show me how the arp command syntax would look?

I forget the exact syntax on Windows.  On a typical GNU/Linux platform, you might do something like:
```

ping $IP_ADDR;
arp | awk 'NR > 1 {print $1,$3;}' | grep $IP_ADDR | cut -d " " -f2;

```
You can probably make the pipeline a lot nicer.

---

### Post by SuperMike on 2007-08-07
Great news!

I discovered that Windows comes with the 'arp' command by default just like Mac and Linux do. Therefore, if you want to ship a server appliance to a customer with no video, where it's administered with a web interface, just have the MAC address printed on a label on the back of the rackmount server, have it grab a DHCP address by default, have it ping all 254 addresses every minute when in DHCP mode (not static IP mode), and then tell the local admin to find its IP simply by typing 'arp -a' on his Windows, Mac, or Linux workstation in the same subnet. The local admin can then just match MAC addresses to IP address. Once they know that, they can connect to this in their web browser to administer the system. One of the first steps in that web interface could be a message to encourage the admin to switch the server to a static IP address (and explain the requirements for that, such as how to reserve an IP address on their DHCP server). No DHCP address needs to be printed on an LED panel, so therefore you can save the cash for having to add that to your rackmount server appliance running Ubuntu Server.

---

