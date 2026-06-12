---
title: "Static vs Dynamic IP Addresses"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by warhelmet on 2008-11-13
Having read the documentation about Samba - thanks to those who pointed me in the right direction - I have discovered that I am best off assigning static ip addresses to the devices on my home network.

This is not a problem. However, what does this mean for my mobile devices? For example, I've got at Asus EeePC 701. Currently, it's running Windows XP but that's going to be replaced with Ubuntu. If I assign a static ip address for my private subnet, what happens when I connect to a wi-fi access point?

My guess that is that I should pick ip addresses that are not at the beginning of the range that DHCP servers in access points, etc, use???

Also, I do get the occaisonal visitor with a wi-fi enabled device. I don't mind them using my internet connection, but I generally would not want them to see my network. Things work OK at the moment, but more by accident than design.

What's the best way to manage this?

---

### Post by Liviu-Theodor on 2008-11-13
If you have a small network, is indeed better with static IPs. But if you have a network not so small, managing it using only static IP becames a nightmare. What you should do? For always online equipment (server, router, network printer, and such), use static IP. For the normal PCs, use dinamic IP. That is the structure here where I work: 1 router, 3 servers, 2 network printers (all with static IP), and 20 (and occasionally some other PCs) stations with dinamic IP.

---

### Post by superprash2003 on 2008-11-13
well if you only want to share internet and not your network files, just ensure that samba is set properly with samba users so it asks for username and password everytime..
As you said, mobile devices better leave it to DHCP.. pcs which are at home always like desktops etc.use static

---

