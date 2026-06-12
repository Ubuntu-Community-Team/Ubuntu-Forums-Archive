---
title: "get hosts in my LAN listening on a specific port"
date: 2012-04-25
forum: Programming Talk
---

### Post by chuchi on 2012-04-25
I am developing a network game in C under Linux, so the users in the LAN can play with each other. Therefore a server is running in each host, listening in a specific port.

So a client must realize a scanning of all the hosts in the same LAN listening the port. I could use nmap, but nmap will yield too much information that I will have to compute with a pipe, isn't it??

Please, let me know if you think the following idea is suitable.

If I knew my own IP address, I would know the type of IP address, A B or C, and also I would know the part of the IP aimed for hosts. So using the socket system call “connect” to the specified port I am able to know all the hosts in my network offering this service.

What do you think is better??

Thank you very much!!!

---

