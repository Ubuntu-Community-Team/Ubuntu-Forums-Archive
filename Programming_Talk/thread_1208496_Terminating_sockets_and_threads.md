---
title: "Terminating sockets and threads"
date: 2009-07-09
forum: Programming Talk
---

### Post by night_fox on 2009-07-09
I have a program which uses sockets to communicate to another machine.
It has a listening thread which spends most of the time in the read() command. Various other threads in the program write() through the socket.

When you try to close a socket during a read command, the read command never returns. How do I close the socket instantly during a read command?

---

### Post by dwhitney67 on 2009-07-09
If I understand correctly, one of your threads is blocked while performing a recv(), and yet when you close the socket, it remains there locked up in that call.

If this is the case, then this contradicts the normal behavior for recv(), which normally would return, indicating that zero bytes were read.

Is it possible that you are stuck in another loop someplace?

P.S.  Which flavor of socket are you using:  TCP or UDP?

P.S.S.  I just re-read your post; why are you using read() and write().  Consider using recv() and send(), or for UDP, recvfrom() and sendto().

---

### Post by night_fox on 2009-07-09
OK, thanks for replying, I've fixed my bug now, firstly, I wasn't actually closing the socket, but I've changed to send/recv, and I had to do call shutdown before calling close.

Thankyou

P.S. I wrote this just before I found the bug, but I'll post it anyway cos forums are free and typing takes time:

> Hi, and thanks for replying. I'm using TCP sockets, and the reason I was using read/write was because I piked the code from someones example. I'm now using send and recv, and the recv call also blocks in the same way. This is definitely happening because I've used gdb to debug it

When the remote end hangs up, the recv/read call both return with 0 length read, but if you close the socket from a different thread from the one recv/read is running on, neither recv nor read ever return.

---

