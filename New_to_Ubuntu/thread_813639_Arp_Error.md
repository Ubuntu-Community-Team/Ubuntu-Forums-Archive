---
title: "Arp Error"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by anothrguitarist on 2008-05-31
I am trying to set an IP for my Dreamcast address using arp, but I receive the following error message:

john@anothrcomputer:~/dc/dcload/dcload-ip$ sudo arp -s 192.168.2.4 00:d0:f1:hard:ware:add
SIOCSARP: Network is unreachable

Does anyone know why it is not working?

---

### Post by SpaceTeddy on 2008-05-31
why on earth would you want to edit your arp table directly ? ARP (Address Resolution Protocol) is a plug and play protocol that should not be messed around with at all... So out of curiosity - why do you want to set it manually instead of letting the protocol stack do the ARP Request and ARP reply ?

besides that, your error looks like you do not have a network card attached to the network you are trying to specify.

ARP is a local area network protocol only - i.e. it is a broadcast protocol. It will not pass beyond any router or firewall.Therefore, ARP will NOT allow you do add addresses to it's cache that are not directly connected to your computer. Thus, you do not have a network card that hold access to the 192.178.2.0/24 network is my guess...

---

