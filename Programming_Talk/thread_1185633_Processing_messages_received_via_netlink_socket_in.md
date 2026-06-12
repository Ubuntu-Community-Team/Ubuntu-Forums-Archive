---
title: "Processing messages received via netlink socket in the kernel"
date: 2009-06-12
forum: Programming Talk
---

### Post by ranthal on 2009-06-12
Hey all,

I've been working on a kernel module for an embedded platform that is interacting with two other processes on the platform-one a net device driver built around an ASIC and the other a user-space daemon.  The main interaction occurs between my module and the ASIC driver to run encrypt/decrypt on data while the interaction with the daemon is essentially to support the xcrypt by providing keys etc.

So here's the issue:
The examples I have seen with netlink sockets are good but the actual core of the program in the examples creates the socket and simply waits to receive an skb on the socket which I can't do.  Instead I need to come up with a good design that separates the functions so that I create the socket in my init function, have a function that is called when the input module wakes up the socket, and in the exit function it releases the socket.

If this is unclear fire questions away since this is really a design issue so probably the more I talk about it and think through it the better it will come together.

Thanks

---

