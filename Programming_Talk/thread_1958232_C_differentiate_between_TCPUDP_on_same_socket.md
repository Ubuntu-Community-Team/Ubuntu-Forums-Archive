---
title: "C differentiate between TCP/UDP on same socket"
date: 2012-04-13
forum: Programming Talk
---

### Post by Xender1 on 2012-04-13
I am writing a server.c in which on the same socket I am allowing TCP and UDP connections. Currently my TCP works fine and much of the core of the structure is very similar to this websites examples: [http://www.tenouk.com/Module41.html](http://www.tenouk.com/Module41.html).

I see how to set up the UDP and to use a datagram, but I am really confused on what information I know when a client connects (mainly do I go to my TCP function to handle info or do I go to my UDP function to handle info). Just need help figuring out how a client has connected for which protocol to use.

Thanks!

---

### Post by dwhitney67 on 2012-04-14
> **Xender1 said:**
> I am writing a server.c in which on the same socket I am allowing TCP and UDP connections. Currently my TCP works fine and much of the core of the structure is very similar to this websites examples: [http://www.tenouk.com/Module41.html](http://www.tenouk.com/Module41.html).

I see how to set up the UDP and to use a datagram, but I am really confused on what information I know when a client connects (mainly do I go to my TCP function to handle info or do I go to my UDP function to handle info). Just need help figuring out how a client has connected for which protocol to use.

Thanks!

UDP is a connectionless protocol; that is, you do not require a connection to the server to send a datagram.  All that is required is the server's IP and the port number that the server has bound its socket to.

I've never tried to send a UDP datagram to a TCP socket.  In fact, I have doubts that it will even succeed.  When working with TCP, the server has one or more "listen" sockets that are for accepting client connections.  Once a connection has been established, the server and the client use a different socket in which to communicate.  The "listen" socket is not (typically) used for information exchange.

Now, since UDP does not support the concept of connecting to a server, I don't see your plans going anywhere.  The website you indicated shows very simplistic examples (which are oftentimes helpful), however when I read the comments in the code, I got the impression that the author was choosing his words very poorly.  Treat the code with caution.

Here's a good guide:  [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)


P.S.  When sending many messages via a UDP socket, it can be more efficient to rely on the usage of send() versus using sendto().  The latter, as you know, requires the specification of a sockaddr_in structure containing information about the destination (IP/port info).  The function send() can be used if you call connect() on the UDP socket with that same sockaddr_in data.  However, don't think of this as actually connecting to a server!  All it is doing is configuring the underlying socket.

---------------------------------

Edit:

I just tested whether a UDP client could connect to a TCP server -- the answer is definitively no.

---

### Post by Xender1 on 2012-04-14
True, I think I may have used poor wording because I dont mean 'socket' more as a C server listens on a certain port, and binded to that port is a TCP listener and a UDP listener. I have seen an example in java using a channel to determine weather its TCP or UDP here ([http://www.java2s.com/Code/Java/Network-Protocol/HandlesTCPandUDPconnectionsandprovidesexceptionhandlinganderrorlogging.htm](http://www.java2s.com/Code/Java/Network-Protocol/HandlesTCPandUDPconnectionsandprovidesexceptionhandlinganderrorlogging.htm)). I have used the website you linked in the past and agree the wording there is much better and understandable. I am going to play with bindings and seeing what info I can print out when a client connects (tcp) or sends a datagram (udp) over the port to determine if its possible to differentiate between them in order to send a message back or to everyone.

---

### Post by callmemahavir on 2012-04-15
It depends upon what parameters are passed to socket function call.
I doubt that a socket connection can do both UDP or TCP.
[SIZE=3][COLOR=#0000FF][FONT=monospace][/FONT][/COLOR][/SIZE]You can make separate code in same program one to handle the UDP and another TCP.
So that program runs both UDP and TCP.

---

