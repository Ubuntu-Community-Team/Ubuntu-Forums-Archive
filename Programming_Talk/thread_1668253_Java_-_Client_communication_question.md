---
title: "Java - Client communication question"
date: 2011-01-16
forum: Programming Talk
---

### Post by PaulM1985 on 2011-01-16
Hi

I am working on a program where two connected computers have to send information to each other fairly regularly.

I didn't want to have to set up one as a server and one as a client because that would mean at the server end I would have to make sure that the user would have port forwarding set up.

I thought that I could have the two computers connect to one independent server and the server could forward on the messages to each.

The problem is, what if I have thousands of communicating pairs of computers.  The server would act as a major bottleneck.

Is it possible for two computers to connect to a server and then the server allows the two computers to talk to each other directly.  Almost as if the server's only purpose is to allow the two computers to find each other and then they can have their "conversation" directly?  Without having to set up port forwarding on either of the communicating computers.

I want to be able to do this in Java.

Any comments appreciated.  Thanks.

Paul

---

### Post by PaulM1985 on 2011-01-16
Ok.  What I think I want to do is write something peer-to-peer with a server that allows the peers to get in touch.  Does anyone know of how to do this in Java?

I have found the JXTA project and some information about that but I am not sure if it is available or even works any more.  Does anyone know about JXTA?

Paul

---

### Post by Reiger on 2011-01-16
Well, no. If the server isn't going to act as message forwarding system then the clients must address each other directly. If the clients must address each other directly, the address must be “visible” from the Internet. If the address must be “visible” from the Internet this means either no NAT or port forwarding.

---

### Post by PaulM1985 on 2011-01-16
> **Reiger said:**
> If the clients must address each other directly, the address must be “visible” from the Internet. If the address must be “visible” from the Internet this means either no NAT or port forwarding.

I thought this was the point of P2P.  The clients are in direct contact.  In the past I have been able to use P2P software without the need for port forwarding.  Does this mean what I was using in the past wasn't exactly P2P?  Or am I miss-understanding what actually happens with P2P?

---

### Post by PaulM1985 on 2011-01-17
Bump.

Anyone got any idea on how I can achieve this?

1) I want to get two clients to connect to a server.
2) Missing step.
3) Clients can now talk directly to each other without either having to be running their own server or have port forwarding set up.

I don't necessarily need to be told the answer, just a push in the right direction would do.

Thanks

Paul

---

### Post by shadylookin on 2011-01-17
Someone has to initially have the server socket, so there's no way to get out of that. 

The reason you were able to use p2p services without port forwarding is probably because of "Universal plug and play" that your router most likely has. Unfortunately I don't know anything about manipulating it so that your p2p app can use it, but you can try looking into that.

---

### Post by PaulM1985 on 2011-01-17
> **shadylookin said:**
> Someone has to initially have the server socket, so there's no way to get out of that. 

Hmm, yeh, I can see that.

My app is supposed to be to help people who aren't very competent with computers.  The host runs the app and then a helper runs another that allows them to help out with the problem on the hosts system.  

The idea was that both apps, host and helper, connect to a server so that they can find each other.  I have found this problem very frustrating since the Socket class contains getInetAddress() and getLocalAddress(), so I thought that I have essentially all the information I needed for the host and helper to establish a connection with each other.
I don't want the server to forward the messages because this could cause a bottleneck for the system.

Paul

---

### Post by PaulM1985 on 2011-02-05
Hi

I have decided that I am going to implement a server which will forward the messages between the client and the host.  I will then look at expanding it further so that when the client and the server try to connect, they will be told to connect to a server which is the least busy.

Anyway, I wanted to know, what is the correct name for this kind of server that I am creating?  "Forwarding server", "Relay Server", ... ?

Thanks

Paul

---

### Post by trozamon on 2011-02-07
Can you make it so that the clients connect to the server, then get information about another client(i.e. their i.p. and port) and then connect them directly?

I haven't done much networking, so don't take my word for it.

---

### Post by Some Penguin on 2011-02-08
> **PaulM1985 said:**
> Hi

I have decided that I am going to implement a server which will forward the messages between the client and the host.  I will then look at expanding it further so that when the client and the server try to connect, they will be told to connect to a server which is the least busy.

Anyway, I wanted to know, what is the correct name for this kind of server that I am creating?  "Forwarding server", "Relay Server", ... ?

Thanks

Paul

Back in the early 90's when I was playing Netrek, the term for such a thing was 'metaserver'.

---

### Post by PaulM1985 on 2011-02-08
> **trozamon said:**
> Can you make it so that the clients connect to the server, then get information about another client(i.e. their i.p. and port) and then connect them directly?

I haven't done much networking, so don't take my word for it.

Unfortunately this is not possible.  The IP you get may be the IP of a router, in which case the router will not forward you on unless the router is set to have port forwarding, which in this case I am always going to use the assumption that it isn't.

> 
Back in the early 90's when I was playing Netrek, the term for such a thing was 'metaserver'.

Thanks for that Some Penguin.  I now have an appropriate term I can use for researching.

Paul

---

### Post by gmargo on 2011-02-08
> **shadylookin said:**
> The reason you were able to use p2p services without port forwarding is probably because of "Universal plug and play" that your router most likely has.

No, probably not.  It worked because you are initiating connections to other peers (who are port forwarding on their end).  No one calling from outside can get in, but you call out enough to get the job done.

---

