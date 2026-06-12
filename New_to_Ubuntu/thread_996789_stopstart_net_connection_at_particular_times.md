---
title: "stop/start net connection at particular times"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by net-reg on 2008-11-29
hi,
	I have ubuntu 7.10 on my home comp. 
	I connect to adsl modem/router via ethernet cable.
           (only one modem/router, one comp, single ethernet cable)
	My modem/router has username/password configured inside it, so 
		when i switch it on, it dials and connects to net, and
                gives my home computer a LAN i.p. (192.168.....)
	So i dont have to use pppoe in ubuntu; only start firefox and start
                browsing.
	 
	Now my question is how to stop/switchoff this connection to
                ethernet.
	I want to keep modem on but stop/start net connection at 
                 particular times.

	(without switching over to pppoe, if possible)
	Tried '/etc/init.d/networking stop|start' , but didnt work.

---

### Post by cmnorton on 2008-11-30
I believe you can use ifconfig:

ifconfig eth0 down

providing eth0 is the name of your ethernet connection. You can find that by just entering ifconfig.

---

