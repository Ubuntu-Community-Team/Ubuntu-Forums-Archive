---
title: "Network Settings"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Bourlog on 2008-08-16
Hello guys!
I need some help with changing my IP

I have a port open to the ip 192.168.1.5 for bittorrent and stuff like that, so i need to change my ip to 192.168.1.5 but i have no idea how to do that, is there any good program for this? 

Thanks!

---

### Post by The Cog on 2008-08-16
System->Administration->Network is the easiest GUI way.
By command line:
sudo ifconfig eth0 192.168.1.5 netmask 255.255.255.0

---

### Post by lisati on 2008-08-16
Some routers can also assign a fixed IP to a particular computer from their admin browser.

---

