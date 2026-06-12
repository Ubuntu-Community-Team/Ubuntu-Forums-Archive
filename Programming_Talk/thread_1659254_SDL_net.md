---
title: "SDL_net"
date: 2011-01-03
forum: Programming Talk
---

### Post by roadkillguy on 2011-01-03
I've been experimenting with SDL_net lately and was wondering if it was possible to make a client and a server run on the same machine. Does the client necessarily have to bind the socket to the port?

Some general info would be great.  I have little experience in this area.

---

### Post by dwhitney67 on 2011-01-03
Sure, the client and server can run on the same host.  And no, the client does not have to bind to an addr/port; it generally just connects to a addr/port, if using TCP, or just skips this step and sends away, if using UDP.

It is the server, regardless whether using TCP or UDP, that binds the port.


P.S.  A UDP client can "connect" to a addr/port if it expects to sends lots of messages to this addr/port, and wishes to do so more efficiently.

---

### Post by roadkillguy on 2011-01-04
The only problem I see is the fact that both client and server will need to send data back and fourth.  Can they still use the same port?  I'll probably use TCP.

---

### Post by dwhitney67 on 2011-01-04
> **roadkillguy said:**
> The only problem I see is the fact that both client and server will need to send data back and fourth.  Can they still use the same port?  I'll probably use TCP.

It is not a problem; TCP and UDP both have bi-directional avenues for communication.

You should consider perusing this very helpful, but non-SDL-net related, guide: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by roadkillguy on 2011-01-13
After a few tests, I got it all sorted out.  It makes perfect sense now.  Thanks for all the info!

---

### Post by roadkillguy on 2011-01-13
After a few tests, I got it all sorted out.  It makes perfect sense now.  Thanks for all the info!

---

