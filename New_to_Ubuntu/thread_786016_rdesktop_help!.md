---
title: "rdesktop help!"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by nintendorulz55 on 2008-05-07
im just learning how to use rdesktop and i can successfully control my desktop computer from my laptop using IP address 192.168... I tried to control a friend's computer to see if it would work, but no luck. I get an error that says "no route to host". I figure i need to connect to their internet, because obviously everyone has 192.168.1.something. is there another IP address or something? i could be totally off and its something completely different, but anyway, can someone help?!

---

### Post by Austin_KW on 2008-05-07
192.168.x.y is a private address. 
Their NAT router redirects their public internet address and port to a private address and port.

To access a pc behind a NAT router you need the public ip address. You also need to configure the remote router to map a port on the public address to the private address.

---

### Post by scorp123 on 2008-05-07
> **nintendorulz55 said:**
>  I tried to control a friend's computer to see if it would work, but no luck. I get an error that says "no route to host".  Your friend's computer is in the same subnet / LAN / network as your other computers?

If not it obviously can't work unless your friend configures his Internet connection to let your RDP connection into his network ... which is dangerous anyway unless you know what you do and how you do it, e.g. SSH-tunnelling and so on.

> **nintendorulz55 said:**
>  everyone has 192.168.1.something. is there another IP address or something? You may wish to read about "Private Range" addresses. It's a standard. Everybody can use those addresses in their network.

[http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html)

---

