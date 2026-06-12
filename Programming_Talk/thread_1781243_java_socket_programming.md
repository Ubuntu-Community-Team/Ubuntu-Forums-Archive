---
title: "java socket programming"
date: 2011-06-13
forum: Programming Talk
---

### Post by manish411 on 2011-06-13
I am trying to build a simple chatting application 
I am making a socketserver using
```

   int port = 50001;
 ServerSocket   server = new ServerSocket(port);

```
 
the application is ready to listen to clients.
on the client side I am making 
a socket using
```

int port = 5001;
String servername = "localhost";
 Socket client=new Socket(servername,port);

```

I am able to fully work on my chat application if I am running 
both the client and server application on my laptop
now the Socket() constructor also takes as
public Socket(InetAddress object,int host)
1.How do I use this constructor if I want to connect to a computer where I have this server
running on ip address "192.168.1.2" on the LAN
2.What if I want to connect to the server on the gobal ip address "117.205.133.123" of the router
but with the internal ip address " 192.168.1.1" within the LAN

---

### Post by dwhitney67 on 2011-06-13
Your server socket is setup correctly to receive connections on all interfaces on port 50001.

As for your client, you need to specify the hostname (or IP address) of the server and the correct port number (you listed 5001).  You only use "localhost" (or 127.0.0.1) if you are connecting to a server on the local machine.

Your client can only connect to a port that is being listened on.  If you setup your router to accept activity on say, port 1234, you could always forward data coming through that port to your server, even if it is listening in on port 50001.  Your router would need to be configured with the server's IP (e.g. 192.168.1.30) and port number (e.g. 50001).

---

### Post by manish411 on 2011-06-14
> 
Your router would need to be configured with the server's IP (e.g. 192.168.1.30) and port number (e.g. 50001).

How do we configure our router. I have a SIEMENS modem and my connections IP address is
"117.205.130.240"

---

### Post by PaulM1985 on 2011-06-14
I am afraid that you are going to have to look on google or in the instructions manual for your router for the answer to that question.  I think usually your router will have some sort of default web page that you can access to sort out this kind of thing.

Look up "Port forwarding" and the make and model of your router.

Paul

---

### Post by dwhitney67 on 2011-06-14
> **manish411 said:**
> How do we configure our router. I have a SIEMENS modem and my connections IP address is
"117.205.130.240"

You should not need to divulge your IP address on this forum.  :-)


As for configuring your modem, please refer to your reference manual.  I personally have a Motorola (cable) modem, which is assigned an IP address, and then I have a Linksys router that I use to share that connection with other computers.

It is the Linksys router that I configure for my incoming connections, of which I only allow two:  HTTP and SSH.  Both of these a common services, and I have these directed to one of my computer behind the Linksys router.

If you do not have a router (which btw, also serves as a firewall), and instead have your computer hooked directly to your modem, you should not have to configure anything.  Connections to your computer should be possible by merely having someone on the outside use your IP address and port number.  The easiest way to verify that there is a server on your computer listening on a particular port is to use telnet.  Ask one of your friend or neighbors to try to connect to your system (e.g. telnet <IP> <port>).

---

### Post by manish411 on 2011-06-14
> **dwhitney67 said:**
>  instead have your computer hooked directly to your modem, you should not have to configure anything.  Connections to your computer should be possible by merely having someone on the outside use your IP address and port number.  rt>).

Yes I have access through wifi on my modem. Does that mean there is no need for configuration and all requests will be forwarded to my laptop. What if my home pc also
has access to the modem through LAN?

---

### Post by dwhitney67 on 2011-06-14
It seems that from what you are describing, you have a modem that also serves as a router.  Thus you are able to have multiple computers use the same modem for their internet access.

Computer that are "behind" the modem should each be assigned a unique IP address.  They should be able to ping each other.  If you open a service on one computer, another computer should be able to connect to it.

However, if a computer is outside of your home, say the one at your next door neighbour's house or perhaps the one on the other side of the Earth, they will need the IP address that is assigned to your _modem_ by your Internet Service Provider; do not confuse this IP address to the one assigned to your computer.  This external computer will also require the port number that the service is listening on.

Now the trick... just because an outside computer has the IP address (of your modem) and port, that does not imply that they will be able to connect to the service running on your computer.  The modem will need to be configured to _port-forward_ any connection requests to your server computer.

I personally do not know anything about the Siemens Modem; maybe someone on this forum can help you with that, or perhaps you have a reference manual that provides clues how to configure the modem.

I know that with a Linksys router (which is not the modem), it assigns IP address to computers using IP addresses in the range of 192.168.1.xxx.  Of course, 192.168.1.1 is reserved for the router itself; if I attempt to HTTP to that special address, I am prompted by my router for the admin user-id and password.  Perhaps your Siemens Modem has a similar interface.

---

