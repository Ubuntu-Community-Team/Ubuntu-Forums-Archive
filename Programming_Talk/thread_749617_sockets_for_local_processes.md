---
title: "sockets for local processes"
date: 2008-04-08
forum: Programming Talk
---

### Post by careca on 2008-04-08
How do I communicate between processes, with sockets?

I wrote a program that returns bind() error
"Cannot assign requested address"
I don't understand bind() function.
Can I use IPv4 for communication between processes on the same machine?
I saw some examples that use INETADDR_ANY, but this, as I read, receives messages to a specific port, and does not cares about address. I need a program that I'll run several times on the same machine, with different addresses, to test middleware algorithms.

Thank you for any information.

---

### Post by ruy_lopez on 2008-04-08
Use unix domain sockets instead.

See "man unix".

EDIT: [Here's]("http://www.ecst.csuchico.edu/~beej/guide/ipc/usock.html") how to use Unix sockets.

You can either use a path (such as "/tmp/socket") or abstract namespaces. I haven't tried the abstract namespaces before. Depending upon how many separate addresses you need, the abstract namespaces might be useful.

---

