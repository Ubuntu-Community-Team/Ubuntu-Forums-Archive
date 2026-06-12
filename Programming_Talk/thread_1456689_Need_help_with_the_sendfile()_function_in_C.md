---
title: "Need help with the sendfile() function in C"
date: 2010-04-17
forum: Programming Talk
---

### Post by rchan0021 on 2010-04-17
Say a server performs:

sendfile(socketY, filedes, &offset, stat_buf.st_size);

where socketY is the socket your connected on. What function would you have to use on the client side to receive the file?



Thanks in Advance.

---

### Post by heikaman on 2010-04-17
On second thought, splice !

---

### Post by rchan0021 on 2010-04-17
huh?

---

### Post by heikaman on 2010-04-17
sendfile copies data in kernel space and so does splice, I think you can use it for both sending/receiving, if not then just use it for receiving, see the man pages.

---

### Post by gmargo on 2010-04-17
> **rchan0021 said:**
> What function would you have to use on the client side to receive the file?

The sendfile(2) function is nothing special; it's just more efficient than a functionally equivalent read(2)/write(2) loop.  The receiving side would use a read(2) loop, just like reading from any socket.

---

