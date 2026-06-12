---
title: "Setting TOS field in IP header"
date: 2009-03-08
forum: Programming Talk
---

### Post by dwhitney67 on 2009-03-08
When messages are sent via TCP or UDP, the packets are prefaced with an IP header.

I am interested in building a test application that sets the TOS (DSCP) field of the IP header, and then sending them through a Cisco router that hopefully (if configured properly) will prioritize the routing of the messages based on the TOS value.

Does anyone know how or whether it is possible to configure the IP header in C or C++?

Btw, I do not want to set an option with the socket, because I want to assign different priorities based on the message type, and not just treat every message as if it were the same.

---

### Post by evymetal on 2009-03-08
> **dwhitney67 said:**
> 
Btw, I do not want to set an option with the socket, because I want to assign different priorities based on the message type, and not just treat every message as if it were the same.

Can you not open multiple sockets - one for each priority you want to set?

I don't do much C, but I think it's the setsockopt() function in socket.h

```

(setsockopt(sock, IPPROTO_IP, IP_TOS, &tos, sizeof(tos)) < 0)

```

---

### Post by dwhitney67 on 2009-03-08
One could do that, but I cannot.  I'm on the receiving end of the messages, not the sending.  Thus the best I can hope to do is configure the router and receive messages.

However before I can call it a day, I need to test the router configuration... and hence the need to create a test program that randomly sends out bursts of messages at different priorities.

I think I may have found something that can help me; unfortunately it is for TCP and only includes the client application.  Thus I will need to find a way to "translate" it to deal with with UDP, and also develop a server.  The help I found is located [here]("http://mixter.void.ru/rawip.html").

---

