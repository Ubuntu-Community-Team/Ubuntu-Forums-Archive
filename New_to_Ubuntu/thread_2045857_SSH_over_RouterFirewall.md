---
title: "SSH over Router/Firewall"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by cheatos on 2012-08-22
Hi there,

I was wondering if it is possible to connect to a computer that is behind a router from outside the router's network because I have my desktop behind a router and can get to it via ssh without any problems when I'm in the same network. However I can't acccess it from outside the network as it would have another IP i suppose.

As in the header, the router also has a firewall built-in don't know if that would affect the ssh connection.

Thanks for your help!

---

### Post by sanderj on 2012-08-22
It depends.

If you can forward a port in the router/firewall, forward the SSH port 22 to the LAN computer.

Or use IPv6: on the LAN computer, "sudo apt-get install miredo", and then visit test-ipv6.com to see what it says.

---

