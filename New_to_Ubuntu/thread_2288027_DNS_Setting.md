---
title: "DNS Setting"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by king_kong2 on 2015-07-23
Hello
I've got a version of Ubuntu on a BeagleBone Black. The next step I need to do is install a GUI, therefore everything I'm doing right now is via the command line.My issue is that whenever I try to go to a domain, the name is not being resolved. For example I can "ping 8.8.8.8" but I cannot "ping google.ca". This means that I can't download and install the GUI and use Network Manager to administer the eth0 settings. I'm currently getting an IP address via DHCP. I've reviewed various forums but can't figure out where or how to assign a DNS address. Please see information below. Please advise how I can correct my DNS issue for eth0.

---

### Post by SeijiSensei on 2015-07-23
Do you control the router/server that provides DHCP services?  If so, you should specify the DNS server(s) you want to use there.

---

### Post by sandyd on 2015-07-24
Hi, please do not drag/drop the images onto the post when attaching pictures/files. The files are encoded into base64, and end up being unreadable in the post.

If you want to attach screenshots/files, please use the 'Manage Attachments' button when submitting a post.

Thanks!

---

### Post by king_kong2 on 2015-07-25
Thanks, I'll look into this. Other DHCP devices don't have the same issue resolving reaching a DNS server. Is there not a place within Ubuntu that I can insert the DNS IP adresses or have I already accomplished it via the line "nameservers x.x.x.x" within the "interfaces" file?

---

### Post by king_kong2 on 2015-07-25
Thanks for the tip.

---

### Post by steeldriver on 2015-07-25
If you are referring to /etc/network/interfaces, then the correct keyword is dns-nameservers rather than simply nameservers I think e.g.

```

auto eth0
iface eth0 inet dhcp
dns-nameservers  8.8.8.8  8.8.4.4

```

However, as SeijiSensei noted, when using DHCP there should be no need to specify nameservers explicitly unless your DHCP is not providing them (or the dhclient is configured not to request them i.e. to ask for 'address only')

---

### Post by obake2 on 2015-07-26
Or you can change/insert DNS forwardings in your router, or you can also do in Network Manager Applet (I am not using Ubuntu, so I don't know if that is the one being used right now). Just right click on the network applet and choose "edit connections"; there you should be able to find a place to set the DNS

Here are my favourite DNS in no particular order:

23.226.230.72, 192.121.170.170, 104.245.33.185, 77.109.148.136, 77.109.148.137, 74.207.241.202, 107.150.40.234, 208.67.222.222, 208.67.220.220

[https://www.opennicproject.org/](https://www.opennicproject.org/)

---

### Post by HermanAB on 2015-07-26
...or, if Network Manager is NOT running, you can edit /etc/resolv.conf manually and insert the name server address in it.

TIMTOWTDI

---

