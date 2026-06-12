---
title: "Sockets in promiscuous mode"
date: 2011-03-08
forum: Programming Talk
---

### Post by 98174 on 2011-03-08
I am running the example socket code from the Python docs, [http://docs.python.org/library/socket.html]("http://docs.python.org/library/socket.html"):

# receive all packages
s.ioctl(socket.SIO_RCVALL, socket.RCVALL_ON)

However, some machines seem to be incapable of this and throw errors such as "socket.error: [Errno 10022] An invalid argument was supplied."

Does this mean the hardware does not support promiscuous mode?

Is there any way to get around this?  What if I were to use a third-party library such as WinPcap?

Thanks all.

---

