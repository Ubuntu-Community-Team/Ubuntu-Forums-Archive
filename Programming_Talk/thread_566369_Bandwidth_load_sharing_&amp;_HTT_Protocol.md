---
title: "Bandwidth load sharing &amp; HTT Protocol"
date: 2007-10-03
forum: Programming Talk
---

### Post by SadaraX on 2007-10-03
I am looking for something to help share the outgoing bandwidth of a server. The server is serving pictures to a lot of users, and the owner is having trouble paying for the bandwidth. This is not sharing the process load of the server, just the file-uploads.

***If there is a system like this already, please tell me. Otherwise, I am going to try to program it.***

The system is to share the uploads (file serving) of the server, and the end user never knows the difference.

Basically, this is the model. There is the main server, and volunteers offer their own servers and bandwidth as nodes with mirrors of the main server.

**How it works**: A 3rd party user asks the server for a file. The server tells the nodes to fulfill the request. The user never knows the difference.

[[IMG]http://img221.imageshack.us/img221/3563/drawingge8.th.png[/IMG]](http://img221.imageshack.us/my.php?image=drawingge8.png)

There are a few things I want to know:

[LIST=1]
[*]I want the user's browser to browse the website(s) like normal and it does not even know the server is having the nodes fulfill the requests. Can this be done with HTTP (the server and the nodes would have different IP addresses)?
[*]If number 1 is possible, can someone give me information about where to begin programming with HTTP? I would like to write this is C++. I will probably need to know some Apache stuff too (oh boy, that's going to be work).
[/LIST]

---

### Post by aks44 on 2007-10-03
> **SadaraX said:**
> I want the user's browser to browse the website(s) like normal and it does not even know the server is having the nodes fulfill the requests. Can this be done with HTTP (the server and the nodes would have different IP addresses)?

It can't be done with standard HTTP. Load balancing requires the servers to be on the same subnet. What you're trying to do is some kind of P2P, which web browsers / servers are not designed for.

---

### Post by Mathiasdm on 2007-10-03
Just make the DNS server do the load balancing.
A request first goes to a DNS server that asks for the IP address of your server. If you put up several servers (you mention other servers mirroring the main server), you can let the DNS server alternate between the different servers.

---

### Post by SadaraX on 2007-10-04
> **Mathiasdm said:**
> Just make the DNS server do the load balancing.
A request first goes to a DNS server that asks for the IP address of your server. If you put up several servers (you mention other servers mirroring the main server), you can let the DNS server alternate between the different servers.

That sounds like a good idea. Can you give me an idea where to start researching or learning about doing this? I am good with programming, but I do not know a lot about writing C++ for HTTP protocol or servers or DNS.

---

