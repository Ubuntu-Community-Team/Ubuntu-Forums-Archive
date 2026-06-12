---
title: "Establish VPN Connection"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by mebomechanicno1 on 2012-07-15
I am trying to establish a VPN Connection to my Office Server (Exchange 2011).  In the Gateway do I put \\ immediately before the IP address of my server, or simply insert the IP address, and do I simply put the IP address or do I then put \name of directory to be accessed\my directory?

PS I am now using 12.04, not 11.10 as shown to the side.

---

### Post by GreatDanton on 2012-07-15
In Ip box, just put your Ip address without //.

---

### Post by mebomechanicno1 on 2012-07-15
Thanks, connection established

---

### Post by GreatDanton on 2012-07-15
I am glad it solved your problem. Now just click on thread tools and mark thread as solved.

---

### Post by d4m1r on 2012-07-15
If you are talking about a straight connect to a VPN server then yes, you just use the IP.

The  slashes only come into play if you are trying to access a hard drive or partition enabled for sharing on a Windows machine. For example, you would do:

\\windows.server.name\shared.hdd.name

---

