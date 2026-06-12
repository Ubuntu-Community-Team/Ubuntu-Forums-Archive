---
title: "How to create socket over PPP connection and NOT over ethernet"
date: 2012-11-16
forum: Programming Talk
---

### Post by rdzurney on 2012-11-16
Greetings,

I have a system where there are two active physical network connections: Ethernet (eth0) and PPP over a USB serial device. I want to create a socket using the PPP connection. How do I "ignore" the ethernet device and only use the ttyUSBx device for the socket connection.  C/C++ application using Eclipse as the dev environment. Thanks much in advance.

Regards,
Ray.

---

### Post by rdzurney on 2012-11-16
Found the answer to this.  After creating the socket have to bind the raw socket to an interface using setsockopt() and then call bind() to bind to an address.

---

