---
title: "peer to peer library"
date: 2008-01-16
forum: Programming Talk
---

### Post by fyplinux on 2008-01-16
Hi, I am looking for a C library that could programming in a peer to peer approach for a distributed system. 

Any related library or suggestion would be welcome. thanks.

---

### Post by PaulFr on 2008-01-19
If you are trying to build up a new peer-to-peer application, you will probably need:

1. For the information sharing (which node has what pieces), you will probably need a **_[http://en.wikipedia.org/wiki/Distributed_hash_table](http://en.wikipedia.org/wiki/Distributed_hash_table)_** (see the Chord, Tapestry, Kademlia or Pastry project web sites for source code) or any such similar distributed data infrastructure.

2. For the actual data transfer and integrity checking, you can use any protocol you want.

If, on the other hand, you only want to write an application without bothering about the actual protocols/data sharing, you may want to look at libraries like JXTA-C (the C binding of the JXTA project), or the libraries below the various open source BitTorrent clients.

Hope this helps.

---

### Post by fyplinux on 2008-01-21
It's a pretty old post now. 

 I also wandering how to use other protocols? Could I use other protocols directly or I read the protocol 's document, then implement it by myself?

---

