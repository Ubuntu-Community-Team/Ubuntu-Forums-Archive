---
title: "Can't Change DNS Address"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Wadcutter on 2012-04-15
I had OpenDNS running successfully on my computer--too successfully. For some reason it blocked access to an important site that I needed right then. I couldn't wait for their tech support to get back to me in 2 or 3 days, so I deleted their DNS settings (208 67 222 222,208 67 220 220) that I had set up by editing my Auto eth0 IPv4 settings (System, Preferences, Network Connections, Edit, IPv4, DNS servers_________).

Their tech support got back to me and said they had fixed their system to recognize the site I wanted access to as a legitimate business site, so I decided to go back and re-set their above addresses in my DNS settings preference. But I haven't been able to do so because every time I try to enter a number into the DNS server box, the "Apply" button grays out. (To be clear, here's what I do: System, Preferences, Network Connections, Edit Auto eth0, IPv4 Settings tab, then change the Method to "Automatic (DHCP) addresses only" which highlights the "DNS servers" box.) But the instant a number is entered in that box, the "Apply" button at the bottom goes gray thus preventing me from actually applying any new or different DNS addresses. Entering the entire setting number 208 67 222 222 doesn't change anything; the Apply button is still disabled.

If I try the "Manual" method, the DNS addresses box is lighted, but the "Apply" button is automatically grayed out. For some reason my system doesn't want me entering any new DNS addresses into it.

I am using Ubuntu 10.04 with a network card hardwired to an outdoor antenna that receives a signal from a mountaintop wireless transmitter. I run my hardwired system thru a router, but use it only as a hardwire switch to connect 2 other computers to the same antenna for internet connection. It does not broadcast a wireless signal. Connection information shows my current Primary DNS as 192.168.1.1.

I can live without OpenDNS, but it does bother me that I can't change my DNS settings. If anyone has any suggestions, I would be grateful. I'm sorry if I left out some pertinent info.

---

### Post by gordintoronto on 2012-04-15
Is your IP address also 192.168.something.something?

---

### Post by papibe on 2012-04-16
> **Wadcutter said:**
> every time I try to enter a number into the DNS server box, the "Apply" button grays out.
That is normal. Just complete entering the addresses:
```
208.67.222.222, 208.67.220.220
```
The 'Apply' button will become available after each address is enter (the whole 4 digits).

Regards.

---

### Post by Wadcutter on 2012-04-16
Thank you, papibe. You nailed it. I guess I wasn't entering correctly. I've got it now.

---

