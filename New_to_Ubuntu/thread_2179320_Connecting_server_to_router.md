---
title: "Connecting server to router?"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by nosto53 on 2013-10-07
I would like to learn/test/have fun with my 'old' 2008 desktop (Athlon6000+ 3GHz, 4GB, 36GB Raptor, 250GB Barrcuda)
as a 12.04LTS Server.  With LAMP to play with development of web stuff.

Q: Where is the best place to put my server?

Local Area Net is: 
my ISP(Comcast) cable modem - TO - my Router(8 ports+wifi) - TO - 3 laptops, 2 desktops, 2 tables, 1 printer and the 'old' (soon) server.

Thanks,
RickO

---

### Post by sandyd on 2013-10-07
Add it to the router - and if your router supports it, set a static DHCP for the server

---

### Post by DuckHook on 2013-10-07
Since your question involves the topology of networking, you might find the following links useful:

As originally recommended by @*slickymaster*
[http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf](http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf)
[http://ftacademy.org/files/materials/fta-m2-admin_gnulinux-v1.pdf](http://ftacademy.org/files/materials/fta-m2-admin_gnulinux-v1.pdf)
[http://debian-handbook.info/download/stable/debian-handbook.pdf](http://debian-handbook.info/download/stable/debian-handbook.pdf)

---

### Post by Amorphous Serendipity on 2013-10-08
Hi nosto53,

If you are keeping this local, you should be fine  plunging it into your router. If you plan to make this a public site, do  not plug your server directly into your router (that's asking for trouble).

Please see the link below for a brief overview of a secure network topology:
[http://cae2y.morainevalley.edu/compete/Resources/PrinciplesNetworkSecurityDesign.pdf](http://cae2y.morainevalley.edu/compete/Resources/PrinciplesNetworkSecurityDesign.pdf)

You may also wish to set everything up virtually (building a virtual network for the web server) to save hardware costs.

For that I would look into ProxMox VE (as I don't think VMWare ESXi will support your AMD processor [could be wrong]):
[http://www.proxmox.com/](http://www.proxmox.com/)

I hope this helps you get started.

---

### Post by CharlesA on 2013-10-08
> **AhKmNPs said:**
> Hi nosto53,

If you are keeping this local, you should be fine  plunging it into your router. If you plan to make this a public site, do  not plug your server directly into your router (that's asking for trouble).

Please see the link below for a brief overview of a secure network topology:
[http://cae2y.morainevalley.edu/compete/Resources/PrinciplesNetworkSecurityDesign.pdf](http://cae2y.morainevalley.edu/compete/Resources/PrinciplesNetworkSecurityDesign.pdf)

That seems more tailored to a business or enterprise than a home user who will probably not have the hardware or knowledge to set up their network like that.

Doesn't make it bad advise though. ;)

---

