---
title: "Sockets and Streams JAVA"
date: 2013-06-19
forum: Programming Talk
---

### Post by Greenbald on 2013-06-19
Hi guys. I did a program to use a API from a site, and get this output information to rehearse to another machine, and this machine will print this information in the console. So, i can make the connection between two computers that are in a internal network. But i cant connect a computer to another computer outside the network, it gives me a error. I'm using sockets....Someone know how to solve this problem?!

---

### Post by zobayer1 on 2013-06-20
> **Greenbald said:**
> Hi guys. I did a program to use a API from a site, and get this output information to rehearse to another machine, and this machine will print this information in the console. So, i can make the connection between two computers that are in a internal network. But i cant connect a computer to another computer outside the network, it gives me a error. I'm using sockets....Someone know how to solve this problem?!

Sockets have nothing to do with the issue, if machine A and B are not reachable from each other (which is reachable for LANs but most of the case not reachable through internet because of not having any globally known IP) you cant do anything. What you can do is put up an intermediate server in the internet which can be accessed by both machines, and this server then can be used to redirect messages from one machine to another. If they are not in the same network, I don't think there is a way of doing it without using any intermediate server.

---

