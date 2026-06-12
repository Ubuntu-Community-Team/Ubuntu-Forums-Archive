---
title: "Open the ports"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by jebaearnest on 2012-02-17
How to open the port 80. I heard that ports below 1024 are privileged ports. 

Is there anything to do with IPTABLES ?or UFW ?

---

### Post by haqking on 2012-02-17
> **jebaearnest said:**
> How to open the port 80. I heard that ports below 1024 are privileged ports. 

Is there anything to do with IPTABLES ?or UFW ?

technically speaking you dont really open or close a port.  You allow traffic destined for that port through a firewall or out or not.

Priveleged ports are ports assigned to well known applications so you cant assign them to other things (well you could but you would likely break things)

If you mean you have a webserver running (on port 80) and need to access it through your firewall then you need to setup rules too allow that if rules are in place, otherwise as soon as you setup or install a service that uses a given port it is already listening on that port and therefore open

However to help you we need more information.

Do you have a firewall setup ?
Are you running a webserver ?

Is this what you are trying to achieve due to blocked traffic somewhere ?

---

### Post by jebaearnest on 2012-02-17
Can you guide me how to enable port 80.

Actually i have configured Tomcat 7 on port 8080.
Then i googled and did it for Port 80.

Problem here is I am not able to access outside the Network.


Thanks in advance.

---

### Post by jebaearnest on 2012-02-17
Thanks a lot for your Quick Response.

Actually i am trying to configure Tomcat on port 80.
Problem here is after changing the configuration to port 80 from port 8080,
when i do the [http://localhost/](http://localhost/), its returning unable to connect.

when i again change configuration to port 8080 from port 80, it got worked.

How to change it.

Please correct me if i am wrong.


> **haqking said:**
> technically speaking you dont really open or close a port.  You allow traffic destined for that port through a firewall or out or not.

Priveleged ports are ports assigned to well known applications so you cant assign them to other things (well you could but you would likely break things)

If you mean you have a webserver running (on port 80) and need to access it through your firewall then you need to setup rules too allow that if rules are in place, otherwise as soon as you setup or install a service that uses a given port it is already listening on that port and therefore open

However to help you we need more information.

Do you have a firewall setup ?
Are you running a webserver ?

Is this what you are trying to achieve due to blocked traffic somewhere ?

---

### Post by haqking on 2012-02-17
> **jebaearnest said:**
> Thanks a lot for your Quick Response.

Actually i am trying to configure Tomcat on port 80.
Problem here is after changing the configuration to port 80 from port 8080,
when i do the [http://localhost/](http://localhost/), its returning unable to connect.

when i again change configuration to port 8080 from port 80, it got worked.

How to change it.

Please correct me if i am wrong.

if you change ports you need to append to the address to create the socket.

[http://localhost:8080](http://localhost:8080)

you append a port with :<portnumber> as above

---

### Post by jebaearnest on 2012-02-17
Yes you are right. If i give [http://localhost:80/](http://localhost:80/) its not showing up.

---

### Post by haqking on 2012-02-17
> **jebaearnest said:**
> Yes you are right. If i give [http://localhost:80/](http://localhost:80/) its not showing up.

no worries, remember to mark the thread as solved using thread tools.

cheers

---

### Post by jebaearnest on 2012-02-17
no man. what i meant to say is even after appending port 80. i am not able to access.

---

### Post by The Cog on 2012-02-17
A firewall would not normally block connections from a PC to itself. That's not your problem. I think your problem is that as you said, ports below 1024 are privileged, meaning only root is allowed to open listening services on those ports. You probably have a "permission denied" or similar somewhere in the tomcat logs. 

Most webservers get round this by being launched by root either as part of systen startup or as a command under sudo. They also normally change their user id to a less powerful one as soon as they have opened all the files and sockets they need, so that they can't do so much damage if they are hijacked by a vulnerability exploit. I don't remember if tomcat changes userid, but if you want it to listen on port 80 then you will have to launch it as root.

> technically speaking you dont really open or close a port. You allow traffic destined for that port through a firewall or out or notThat's right, if you are talking about firewalls. Opening ports is what happens when an application tells the OS to open a listening socket, and closing ports is what happens when the application closes the port again (probably as it exits). I would say that what a firewall does is to permit or deny access to the port, regardless of whether it happens to be open or closed at the time. Imagine a guard standing outside a doorway - the door may or may not be locked, but the guard gets to choose if you are even allowed to try the handle. It's unfortunate that people use open/close in the context of both application and firewall, because they really are different things and this causes confusion.

---

### Post by haqking on 2012-02-17
> **The Cog said:**
> A firewall would not normally block connections from a PC to itself. That's not your problem. I think your problem is that as you said, ports below 1024 are privileged, meaning only root is allowed to open listening services on those ports. You probably have a "permission denied" or similar somewhere in the tomcat logs. 

Most webservers get round this by being launched by root either as part of systen startup or as a command under sudo. They also normally change their user id to a less powerful one as soon as they have opened all the files and sockets they need, so that they can't do so much damage if they are hijacked by a vulnerability exploit. I don't remember if tomcat changes userid, but if you want it to listen on port 80 then you will have to launch it as root.

That's right, if you are talking about firewalls. Opening ports is what happens when an application tells the OS to open a listening socket, and closing ports is what happens when the application closes the port again (probably as it exits). I would say that what a firewall does is to permit or deny access to the port, regardless of whether it happens to be open or closed at the time. Imagine a guard standing outside a doorway - the door may or may not be locked, but the guard gets to choose if you are even allowed to try the handle. It's unfortunate that people use open/close in the context of both application and firewall, because they really are different things and this causes confusion.

I agree.

I was referring to firewalls in general as the OP originally refered to IPTables and UFW.

Peace

---

### Post by kevdog on 2012-02-17
How do you want to do this? ufw, iptables -- all are very easy to do.

---

### Post by haqking on 2012-02-17
are you behind a router ?

if so go to router and port forward port 80 to the IP of the server.

---

### Post by jebaearnest on 2012-02-17
Port 80 works fine inside the network.Outside the network I am not able to acess the same.
But if i change to 8080 again, it works outside also

I am not able to access one Public DNS outside the network.
But the same  Public DNS is working inside the network.

Do i need to change any settings ?

---

### Post by oldos2er on 2012-02-17
Threads merged. Please do not open more than one thread per problem/question.

---

### Post by jebaearnest on 2012-02-17
sure. But, Kindly let me know to resolve the issue.
Port 80 works fine inside the network.Outside the network I am not able to acess the same.
But if i change to 8080 again, it works outside also

I am not able to access one Public DNS outside the network.
But the same  Public DNS is working inside the network.

Do i need to change any settings ?

---

