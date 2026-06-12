---
title: "[C++] Create socket o internet"
date: 2013-09-16
forum: Programming Talk
---

### Post by dima91 on 2013-09-16
[FONT=Ubuntu] hi to all!!
i'm trying to realize a simple server (and therefore also a client) with sockets..
i've been realized a simple server with the AF_UNIX's family sockets..but now i want to implement a server with the AF_INET's family socket..
to help me i have found this useful giude [http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm).. my problem is that i want to upload the socket on internet (to whatever site) to have an absolute address and let that way to clients to connect without problems to socket present on web..
is it possible?..if not, can you link me some guides or tell me what to do?..
tank you!!

---

### Post by dwhitney67 on 2013-09-16
You can use any ephemeral (available) port on your system for your server.  If your system sits behind a firewall, then you need to make sure that a client system can connect through the firewall to your server computer.

Before embarking on this (web) internet endeavor, let me suggest that you attempt to develop both a client and a server that runs on your local system.  Your server should use an ephemeral port, and bind the socket to all of your system's interfaces, or just the main network interface (usually the IP address returned by ifconfig eth0).

You should then be able to run your client and server on different systems, or alternatively on the same system, within your local area network.  If you wish for a peer to connect to your server from outside of your LAN, then you will need to give that person two pieces of information:  1) the IP address of your server, and 2) the port to connect to.  (Keep in mind that you will have to manage your firewall to allow traffic through that port!).

If you require additional information, here's the best guide that I have come across:  [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

