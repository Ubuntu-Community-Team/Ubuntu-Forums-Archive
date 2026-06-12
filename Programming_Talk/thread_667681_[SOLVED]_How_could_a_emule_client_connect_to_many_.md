---
title: "[SOLVED] How could a emule client connect to many other clients?"
date: 2008-01-14
forum: Programming Talk
---

### Post by fyplinux on 2008-01-14
Hi, A single emule client only open a TCP port and a UDP port, but normally, hundreds of other clients would connect to the client,I am wondering how could emule handle this?

Another use case is an instant messenger could talk to many others, how is this be done?

What is the common application architecture of such applications?thanks.

---

### Post by Tuna-Fish on 2008-01-14
You probably should read up on how sockets are used. It is trivial to build an application that can service as many clients as it wants on a single socket.

---

### Post by fyplinux on 2008-01-15
two possible way I know now:

1.  put all the connection in a queue, serve the connection sequentially.
2. multi-thread

---

