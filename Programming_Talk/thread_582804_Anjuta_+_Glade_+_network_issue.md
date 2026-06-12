---
title: "Anjuta + Glade + network issue"
date: 2007-10-20
forum: Programming Talk
---

### Post by golgot04 on 2007-10-20
Hi there!

I'm a little lost with anjuta (I'm not a programmer so...)

In fact, I'd like to build a very simple application :
It's a GUI with only 2 buttons (Connect & Quit) and a label. I've succeed to build a such GUI  with anjuta and glade, but i don't really know where i should put my code (callback.c, main.c etc..) 

In fact I would like that this application send an ethernet packet every 5 seconds since the connect button was press. This ethernet packet is nor TCP neither any known protocol. He is build like this :  [(@mac PC)(@mac device)(protocol code for example 01AB) and some hexa bytes...]
The device on the network respond to this packet with a similar structure [(@mac device)(@mac pc)(protocol code for example 01AB) and some hexa bytes...]. I'd like to extract these hexa bytes to put them on my label and actualize the value every 5 seconds.

I've tried a lot of things (sockets, libpcap, etc etc...) but I don't really know what I am doing... :)

Thanks in advance... It's my first experience of programming in the linux world (Huhh.. Visual Basic is more ... basic?).

---

