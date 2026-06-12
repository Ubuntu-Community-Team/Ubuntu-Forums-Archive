---
title: "How do i assign ip address to socket in kernel"
date: 2008-09-27
forum: Programming Talk
---

### Post by akshata on 2008-09-27
Hi,
    I want to create a socket in the kernel fro client/server implementation. At the user level there are APIs like inet_aton() to convert the dotted decimal to integer. What is the corresponding function that i can use in the kernel to assign ip address to sock.sin_addr.s_addr ? Im tryin to implement udp client and server in the kernel.

---

### Post by CptPicard on 2008-09-27
I'm not much of a low-level network programmer, but according to my understanding, IPs are assigned to network interfaces, not individual sockets.

---

