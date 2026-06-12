---
title: "crash on write to closed socket"
date: 2009-11-05
forum: Programming Talk
---

### Post by BipolarJunction on 2009-11-05
OK so I was writing a program that used the socks4 protocol, and I ran into something rather annoying.  If I create a TCP socket, once the remote host closes it if I try to call write() on the socket it straight up terminates my process rather than giving an error.  Paraphrased portion of code:

printf("Going to send new line...\n");
write(fd, "\n", 1);
printf("Sent new line.\n");

It would print the first message, but the program would terminate before the second line was printed.  Is there something I'm missing, or is write() not acting like it's supposed to?

---

### Post by dwhitney67 on 2009-11-05
Your code snippet looks fine, thus you are going to need to supply more code from your application.  write() should return a -1 on error.  The cause of the error can be analyzed through the value of errno.

Btw, what do you mean by sock4 protocol?  Do you mean IPv4?

Also, when sending data through sockets, write() is not the most favored function to use.  Try using send() or sendto().

---

### Post by BipolarJunction on 2009-11-05
I meant Socks4, the protocol a lot of open proxies use (I was doing a connection tunnelling experiment).

I tried switching everything to send(), but the same problem occurred.

I know the socket was up and running right because I was able to send data through it just fine, but once the connection's terminated on the other end any attempt to call write() or send() on the file descriptor of the socket just kills the program.

I also tried printing errno.  It was 0, all the way up until the program got stopped.

---

### Post by dwhitney67 on 2009-11-05
> **BipolarJunction said:**
> I meant Socks4, the protocol a lot of open proxies use (I was doing a connection tunnelling experiment).

I tried switching everything to send(), but the same problem occurred.

I know the socket was up and running right because I was able to send data through it just fine, but once the connection's terminated on the other end any attempt to call write() or send() on the file descriptor of the socket just kills the program.

I also tried printing errno.  It was 0, all the way up until the program got stopped.
What you are describing is not normal behavior for write() or for send().

Personally, I suspect that you are corrupting the stack (or possibly the heap) data using an operation somewhere else in your code.

P.S.  Post your code... show me how you create the socket, setup the connection (if using TCP), and are sending/receiving data.

---

### Post by BipolarJunction on 2009-11-05
Oh now there's a thought!  I'll check for buffer overflows and the like.

---

