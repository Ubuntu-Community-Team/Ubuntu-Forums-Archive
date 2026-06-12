---
title: "closing a tcp connection without close or shutdown"
date: 2010-04-19
forum: Programming Talk
---

### Post by nikhilbhardwaj on 2010-04-19
i've been reading the sockets api
i know that we can close a socket with 
close from unistd.h
or using shutdown from sys/socket.h

but i saw a question 
how can you close a tcp connection without close or shutdown??

cant seem to figure this out
anybody knows how

---

### Post by Iowan on 2010-04-19
Is this a C-programming question? I presume you're talking something different than just downing the interface (ie. via **ifconfig**).

---

### Post by nikhilbhardwaj on 2010-04-20
yes indeed
it is a c programming question

---

### Post by Iowan on 2010-04-20
Moved to Programming Talk forum.

---

### Post by pconroy on 2010-04-20
> **nikhilbhardwaj said:**
> i've been reading the sockets api
i know that we can close a socket with 
close from unistd.h
or using shutdown from sys/socket.h

but i saw a question 
how can you close a tcp connection without close or shutdown??

cant seem to figure this out
anybody knows how

This is confusing - the post is in a programming forum, and you mention you've been reading the "API".

Which API - Berkley, TLI, POSIX?


If some program called "socket()", "bind()", "listen()", "accept()", "read()", and "write()" -- what is preventing it from calling the "close()" function?


It also depends on what you have as a resource when you refer to your TCP connection.  "socket()" returns a file descriptor. "close()" accepts a file descriptor.


To close a TCP connection, it needs to be done gracefully and then system resources need to be deallocated.

---

### Post by Cracauer on 2010-04-20
exit(42);

kill(getpid(), 9);

system("/sbin/halt");

---

### Post by pconroy on 2010-04-21
> **Cracauer said:**
> exit(42);


There's my bug!
I'd been using exit( 43 );

Doh!
:)

---

### Post by nikhilbhardwaj on 2010-04-22
> **pconroy said:**
> This is confusing - the post is in a programming forum, and you mention you've been reading the "API".

Which API - Berkley, TLI, POSIX?


the one in richard stevens unix network programming.

nothing prevents it from calling close() or shutdown()
but i wanted to know if there was another system call.


i understand the answers given by Cracauer
but they seem to involve terminating the program
and as a result the kernel closing all the open file descriptors.

also could you explain what exit(42) does.

---

