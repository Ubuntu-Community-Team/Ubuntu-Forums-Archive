---
title: "DHCP Server"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by warhelmet on 2008-11-13
I'm in the process of setting up my home network. I've got Ubuntu Server on my Dell Poweredge T605. I've got an old E-Machines Celeron box that I've put two NICs and I've downloaded Smoothwall to install on it so I can use it as a dedicated firewall. I'm also got a Netgear wireless router.

All of these devices can act as a DHCP server. I don't think that I want the router to be a DHCP server but my question is, am I better running a DHCP server on the firewall or on my main server? I don't have any problems doing the necessary config, I'm most interested in what is best practise security wise?

---

### Post by chrisod on 2008-11-13
The wireless router almost certainly has a firewall, and possibly an IDS, built in. (My $50 wireless router does...) What is the purpose of using a server as a firewall? I'd use the DHCP from the router and skip the server acting as a firewall. Seems like you are adding a lot of complexity to your network that doesn't need to be there.

---

### Post by superprash2003 on 2008-11-13
i'd say combine your main server and your firewall into one server.. which acts like a gateway to your network.. as mentioned above try not to make it too complex.. to setup internet sharing, an easy way is to setup firestarter , it has internet connection sharing support and is a GUI for your firewall.. so thats a good choice..

---

### Post by warhelmet on 2008-11-13
I am certainly making things too complicated for my current situation but I'm looking to the future. At some point, my network will be entirely wired. Wi-fi is just temporary.

The reason for having a pc running a firewall is cost driven. I had an old pc doing nothing. PCI ethernet cards *very* cheap and you can buy them everywhere. PCIe ethernet cards are more expensive. My PowerEdge is PCIe only.

The firewall will be attached to a cable modem. so 100Mb networking is OK, but I'm planning on Gigabit ethernet for the rest of the network.

On top of this, in the future, I may well be running Ubuntu Server as a VM and Windows Server as a VM. Depending on what I'm doing, it could be the case that I'm only running one. I think I might have answered my own question - if the firewall is the only constant, run the DHCP server there.

It's also worth pointing out that part of the complexity is due to using fiddling with computers as therapy.

---

