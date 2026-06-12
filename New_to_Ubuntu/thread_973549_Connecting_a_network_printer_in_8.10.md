---
title: "Connecting a network printer in 8.10"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-11-06
So I'm trying to connect a printer to my linux box (I'm running ubuntu 8.10) so I can print papers and what not.  I am using my dad's old Apple Laserwriter 16/600 PS which I believe he stole from work, but I have no way to prove it, so it's not really pertinent.  At any rate, I have it hooked up to the router, I have the IP and all sorts of information on it, I was just wondering how I should go about doing this.

Help is greatly appreciated,
--Wes

---

### Post by cmnorton on 2008-11-07
You'll probably need to know something about the port on which this print server listens. Either the web cups interface localhost:631 (make sure your user is in lpadmin group to use), or the Ubuntu menus should let you find this printer and connect to it. 

As to configuring the printer, it would probably be helpful to give the printer a fixed IP address through its own menus. You can pick something high, out of the way of the addresses granted by DHCP, or limit that in the router's config.

---

