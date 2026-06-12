---
title: "Socket access control"
date: 2010-06-03
forum: Programming Talk
---

### Post by soltanis on 2010-06-03
Hello,

I've been working with the sockets API in Python. I'm trying to extend a package I've been working on (it's a simple TCP signaling protocol) by implementing Access Control Lists, which basically allow connections from certain IP addresses and deny from others.

Normally I'd do:

```

  (client, addr) = sock.accept()

```

After listening on the socket. However, I would rather not have to accept the TCP connection if I am only going to find out later that addr isn't on my "accept connections from" list.

So my question is, is it possible to inspect the address of an incoming connection before accepting it (and possibly deny it) at the application level, or is would this only be possible by modifying the firewall rules?

---

### Post by soltanis on 2010-06-03
After doing more research and reading more manpages, it doesn't seem like you can "inspect" incoming connections before you've accepted them at the application level.

The solution to this problem seems to either be accept the connection, check the IP address against the ACL and then close the connection if it is not allowed, or otherwise to set your firewall rules to deny packets from certain hosts. According to the manpage for accept, though, a side-effect of setting firewall rules to deny is that you might try to accept() a connection that the firewall won't allow you to complete, in which case you'll get an invalid file descriptor and the operation will fail with EPERM.

Unless anyone has any other ideas.

---

