---
title: "recv() and send() in two different threads"
date: 2010-06-26
forum: Programming Talk
---

### Post by dawwin on 2010-06-26
Hello everyone, it's my first post here

I've got following situation:
I want to create two threads - first to read data from socket (using blocking function recv()) and second to send data to the same socket using send() function.

Is it okay to use send() when recv() is locked on the same socket?

---

### Post by dwhitney67 on 2010-06-26
Yes.


P.S.  IMHO, you should avoid calling recv() unless you have been notified that there is data to be read on the socket.  Look at the man-page for select(), for this will assist you in determining when there is data to be read.

---

### Post by dawwin on 2010-06-26
Thanks

---

