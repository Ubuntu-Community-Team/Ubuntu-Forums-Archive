---
title: "GUFW Port Transmission Bittorent"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by BigCityCat on 2013-06-28
I have never done any torrenting before. Transmission Bittorrent, preferences, network, test port 51413 says its closed even when I have allowed this port through the firewall. If I turn the firewall off completely it shows as open. Is there something I'm missing?

Nevermind

---

### Post by papibe on 2013-06-28
Hi BigCityCat.

That port is for incoming traffic, in other words, it is used for other peers to connect to you.

In order to be able to 'share' data, you need to both forward it from the router to your machine, and have it open for incoming connections in your firewall.

Does that help?
Regards

---

### Post by coldraven on 2013-06-29
I'm not using UFW but Transmission works for me and I'm not sure why.
My router settings (attached) seem to show that UPnP is deactivated, even when Transmission is running.
I hope that someone will explain all :)

---

### Post by papibe on 2013-06-29
Transmission, or any other bittorrent client, doesn't need any setting in the router in order to download data from other peers. This is because the local machine itself initiate the requests, and most, if not all, routers work in stateful mode.

When a peer from outside your LAN makes a request for data, by default the router will block the request. This can be change either by setting a forwarding rule, by letting transmission open the port using NAT PMP or UPnP, or by setting a DMZ.

@coldraven, are you able to upload (share) data?

Regards.

---

