---
title: "IO::Socket help!"
date: 2010-05-18
forum: Programming Talk
---

### Post by hellert88 on 2010-05-18
I am working on a socket for work but when I try to use the timeout argument it doesn't seem to work.  No matter what time I use it keeps timeing out at about 30 seconds.  I looked online and people seem to be having the same problem but no real solid answer on how to fix it.  Any help?
Thanks!

---

### Post by slavik on 2010-05-18
I use INET sockets ...

can you show a piece of code?

---

### Post by hellert88 on 2010-05-19
$sock = new IO::Socket::INET(
        LocalHost => [ip address],
        LocalPort => 3000,
        Listen => 1,
        Reuse => 1,
        Proto => 'tcp') || die "Error creating socket: $!";

 
I use to have 
timeout => 20,
but noticing that that did nothing for me I just left it out.

---

### Post by soltanis on 2010-05-19
Wrap your code in [code] tags, makes it easier to read, thanks.

What operation are you waiting for a timeout on? Connecting?

---

### Post by slavik on 2010-05-19
err, you're listening on a socket ... why would that ever time out? timeout is for creating sockets ...

---

### Post by soltanis on 2010-05-20
Yeah, socket listens don't block (accept does). If you want to kill a listener after no one connects after a certain amount of time, then you can do multiple things:

1) create the socket, use select() with a timeout with the listener socket set as one of the sockets you are polling for input. If after select() returns, the listener socket is not in the list of "ready" sockets, then no one has attempted to connect. Otherwise, you should accept() on the pending connection.
2) run two threads. In one thread, try to accept() a connection on the socket, and in the other, run a timer. If after the timer expires, the first thread has not returned from accepting the connection, then you handle it.

---

### Post by hellert88 on 2010-05-20
Nevermind guys I figured out the problem.  The device that was sending the information had a timeout after so long.  Thanks for the help though!

---

### Post by hellert88 on 2010-05-20
Scratch that....
In my program I want to verify that what one of my devices readings are acurate to what the people are scanning.  The problem is that the socket will stay open.  How can I have the socket close after it receives a stream?

---

