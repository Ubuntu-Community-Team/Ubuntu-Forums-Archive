---
title: "HOWTO: Sharing Internet connection with a router via Ethernet"
date: 2011-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Truthiswithin on 2011-06-20
*I was trying to set up an Ubuntu machine to act as an Internet connection for my whole LAN, via a wireless router's Internet port.  Here's how I got it working:*  

**Equipment:**
[LIST]
[*]Ubuntu 11.04 Desktop with Ethernet port

[*]Linksys WRT120N Wireless N Router

[*]Huawei E620 USB Broadband Modem

[*]Ethernet cable
[/LIST]
**Hardware Setup:**
[LIST]
[*]Huawei plugged into Ubuntu machine

[*]Ethernet cable plugged into Ethernet port

[*]other end of Ethernet cable plugged into the *Internet* port of The Linksys
[/LIST]
**Ubuntu Setup:**
[LIST=1]
[*]connect the Huawei to the Internet
[*]disconnect the wired connection (Auto Eth0) in network tray icon
[*]create new wired connection (Edit Connections... > Add, enter a name) and select *Shared To Other Computers*  from IPv4 settings tab.
[*]connect to this new wired connection
[*]note down the settings for this connection under *Connection Information*, and the DNS servers for the Huawei connection
[/LIST]
**Linksys Setup:**
[LIST=1]
[*]connect a computer on the receiving side to the Linksys (wired or wireless) 
[*]open a browser in this computer, navigate to Linksys (*192.168.1.1* is default, user and password should be both admin)
[*]Change *Internet Connection Type* to *Static IP*
[*]Under *Internet IP Address* I put the number that came after the Ubuntu machine's IP address for this connection (again, not the IP for the Huawei connection), this was just a guess as I'm pretty clueless about how this works.  So, my Ubuntu machine had an IP of *10.42.43.1*, and I gave the Linksys [/I]10.42.43.2[/I]
[*]*Subnet Mask* should be same as the Ubuntu machine, *255.255.255.0*
[*]*Default Gateway* should be the Ubuntu machine's IP address, *10.42.43.1* in my case.
[*]*DNS 1* (etc.) should be the same as the *Primary DNS* (etc.) used by the Ubuntu machine in the Huawei connection.
[*]Click *Save Settings*.
[/LIST]
That's it.  Computers connected to the Linksys can now browse the Internet via the Huawei connection :)

Finally, after days of trying all sorts of things, I have an alternative to buying a router with a port for my USB modem.  Using this method, I'm going to try to use a 1st gen. eeePC as a router instead :)

---

