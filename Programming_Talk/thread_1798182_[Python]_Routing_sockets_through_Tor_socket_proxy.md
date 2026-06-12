---
title: "[Python] Routing sockets through Tor socket proxy"
date: 2011-07-06
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-06
I'm hosting a text based game on Tor, which pays the user money (Through Paypal) if they win. (For everyone who has negative ideas about Tor, it's the only domain I could get which helps me keep my domain even when I'm not behind a static IP address and when I'm behind a firewall. Yes, I do know about DDNS. I just don't care for it) Anyway, the service is running smoothly through the Tor virtual port, but I need to run the client (What my users will be using) through Tor also. The server is in socks. Tor has a Socks proxy, but I don't know how to route sockets through a socks proxy using Python.

---

### Post by ki4jgt on 2011-07-06
[http://stackoverflow.com/questions/5148589/python-urllib-over-tor](http://stackoverflow.com/questions/5148589/python-urllib-over-tor)

Just found on Google, was using wrong search terminology. Finally just searched for Tor Python Sockets instead of python sockets proxy. Thanks guys.

---

