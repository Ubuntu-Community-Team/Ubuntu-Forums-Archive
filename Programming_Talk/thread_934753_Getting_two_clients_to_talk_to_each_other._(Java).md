---
title: "Getting two clients to talk to each other. (Java)"
date: 2008-09-30
forum: Programming Talk
---

### Post by boopyg on 2008-09-30
-

---

### Post by dwhitney67 on 2008-10-01
Designating an application as a server or a client is merely semantics.  From what you describe, you want two client applications to share data.  Why not just use the same socket know-how you achieved with the server and client?  There is nothing written in stone that indicates that a client cannot be a client-server!

If your goal to have clients share data with each other, there are other ways too.  For instance, you can re-factor your client application to create multiple mini-client threads that all share the same data space.  Then sharing data is a breeze (just make sure the data areas are synchronized).

---

### Post by boopyg on 2008-10-01
-

---

### Post by dwhitney67 on 2008-10-01
Or you could just pass messaging traffic from one client to the another via the server.  Essentially the server functions as a switchboard.

The industry term generally used when a client connects to another client is "Point-to-Point" communications.  If a client connects to multiple clients, then you are dealing with Point-to-Multipoint communications.

I've worked on several project with similar purposes.  The only difference is that the server was in actuality a satellite (or a constellation of such), and the clients were a collection of land/ship/aircraft/hand-held radios... spread across the globe.

If you decide to employ this strategy, each message sent by a client will need to contain at a minimum the source ID of the sending client, the destination ID of the receiving client(s), along with the message itself.

Good luck with whatever strategy you choose.

---

