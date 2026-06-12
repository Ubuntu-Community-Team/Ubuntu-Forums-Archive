---
title: "[c Socket]problems with the accept()"
date: 2015-04-24
forum: Programming Talk
---

### Post by srinidhi2 on 2015-04-24
I am new to socket programming. As an assignment , I had to create a FTP sever-client program. I created two ports for my sever and client, one for data and the other for commands. I created 2 diff sockets for this . Both programs compiled properly but they but they are unable to connect with each other. After running through gdb, I found out that the accept() in my server program wasn't able to accept connection from the client . The exact message is as follows :
Program received signal SIGPIPE, Broken pipe. 0x00007ffff7b104fd in __libc_send (fd=3, buf=0x7fffffffcea0, n=2, flags=-1) at ../sysdeps/unix/sysv/linux/x86_64/send.c:27 27    ../sysdeps/unix/sysv/linux/x86_64/send.c: No such file or directory.
 
help anyone??

---

### Post by dwhitney67 on 2015-04-25
It appears from the error you posted, that the issue is occurring with a send() operation, not the accept() operation.  It might be easier to analyse the issue if you post the code of your server.

Btw, is this a kernel-level programming assignment, or merely user-level programming?

P.S.  A socket server (written in C) should always perform the following:  create socket, bind socket, set up listen, and then accept client connections.  When the server is running, test it with a simple client (e.g. telnet).

---

