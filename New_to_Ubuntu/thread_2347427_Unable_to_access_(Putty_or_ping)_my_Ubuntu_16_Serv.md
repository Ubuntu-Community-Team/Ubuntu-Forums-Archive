---
title: "Unable to access (Putty or ping) my Ubuntu 16 Server from outer connection"
date: 2016-12-24
forum: New to Ubuntu
---

### Post by milan89 on 2016-12-24
I have installed an Ubuntu 16 Server and I have it connected via LAN to my modem. I have a Windows PC also connected to the same network and I can easily ping or Putty into the server and can also manipulate with the SQL database and whatnot.

The problem is, even though I have forwarded the relevant port (22) with the IP address of the server, I can't seem to ping it from any outer connection. I have confirmed that the port is indeed opened via that web thingy - [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Does anyone have any ideas why this may be?

---

### Post by papibe on 2016-12-24
Hi milan89.

A few thoughts...

In order for the ping to work you need (1) a router that allows outbound ICMP and the inbound responses, and (2) proper forwarding rules. My guess is right now the router is receiving and ignoring the pings.

In order to test remote ssh access to your server, you need to do it from outside your network. The easiest way would be to use an ssh client on your phone when the latter is not connected to your LAN (using  your provider 3G/4G service).

Does that help? Let us know how it goes.
Regards.

---

### Post by milan89 on 2016-12-24
So I would need a router that can specifically target ICMP, as opposed to TCP?

---

### Post by papibe on 2016-12-24
More like in addition to TCP/UDP. However, that's only for ping, which I imagine is not that important. In other words, a working ping is not requisite for ssh to work.

Did you try to connect using ssh from outside your network?

Regards.

---

### Post by milan89 on 2016-12-24
Yeah, tried with Putty while hotspotted thru my cell phone.

---

### Post by papibe on 2016-12-24
I'm going to guess it didn't work? or it did?

Try using a port in the dynamic range: 49152 through 65535. For instance, 55555. Forward that port to the server's 22.

You'll need to adjust a parameter on putty to use a non default port (55555).

Is your server using a static IP, or a DHCP reservation from the router? A reservation works better, assuming your router is your DHCP server. In the latter case, the router will absolutely 'know' how to get to your server.  If you set up a static address within Ubuntu itself, try pinging the router so the router updates its arp table.

Hope it helps. Let us know how it goes.
Regards.

---

