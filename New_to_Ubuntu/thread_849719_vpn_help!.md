---
title: "vpn help!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-07-04
Hi all, i am trying to connect to my work network (windows) i have setup the vpn (pptp) connection, but i from memory i know i need to set up a ip tunnel, or something like that.. because when i try to connect to my pc in the office using Terminal Server Client, it cant find the computer... 

i have done this before, but i cant remember how i did it... 

Please help :)

---

### Post by gate on 2008-07-05
Hi, I use my laptop (Ubuntu) to connect to a windows domain/pptp vpn. All I did was make sure 
network-manager-openvpn  
network-manager-vpnc
network-manager-pptp
were all installed, then use the network manager to configure a new VPN (right click, VPN->Configure). It was all pretty intuitive. I don't have the domain append set up, so I have to add '.domain.com' to all the host names.

---

