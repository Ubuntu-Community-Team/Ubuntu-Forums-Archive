---
title: "[CPP] Using a socket from multiple threads"
date: 2008-10-12
forum: Programming Talk
---

### Post by sillv0r on 2008-10-12
Hi,

I'm pretty new at cpp socket stuff, so if I'm going about this the wrong way, please enlighten me.

I'm trying to use multiple threads to service my socket descriptors. Note that the sockets are blocking sockets.

A general question would be:

 Q: Are the functions associated with sockets threadsafe? (i.e. **recv**, **send**, **accept**) see clarification below.

Clarification: I don't think that they are threadsafe within themselves (sending data on the same socket descriptor from different threads), but I was thinking that I could do a **recv** on one thread at the same time as a **send** from another thread on the same socket descriptor.

---

