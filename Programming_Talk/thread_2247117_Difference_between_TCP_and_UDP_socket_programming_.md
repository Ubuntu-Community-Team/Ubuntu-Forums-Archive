---
title: "Difference between TCP and UDP socket programming in C"
date: 2014-10-05
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-05
Hello,
 I would like to know the differences between socket programming in C for TCP and UDP.

I read a few resources and the only difference I could see is,
To create a TCP socket, you would do
```
[COLOR=#000000][FONT=Consolas]/* create a TCP/IP socket */	if ((svc = socket(AF_INET, SOCK_STREAM, 0)) < 0) {		perror("cannot create socket");		exit(1);	}[/FONT][/COLOR]
```

Whereas, to create a UDP socket, you would do,
```
[COLOR=#000000][FONT=Consolas] /* create a UDP socket */        if ((fd = socket(AF_INET, SOCK_DGRAM, 0)) < 0) {                perror("cannot create socket\n");                return 0;        }[/FONT][/COLOR]
```

Are there any differences in the system calls if I'm trying to create a client-server application where the server responds to different requests from the client, and I'm doing this for both TCP as well as UDP.

Thanks.

---

### Post by T.J. on 2014-10-06
Yes.  One is a stream one is a datagram.   [http://unixhelp.ed.ac.uk/CGI/man-cgi?socket+2](http://unixhelp.ed.ac.uk/CGI/man-cgi?socket+2)

---

### Post by IAMTubby on 2014-10-11
> **T.J. said:**
> Yes.  One is a stream one is a datagram.   [http://unixhelp.ed.ac.uk/CGI/man-cgi?socket+2](http://unixhelp.ed.ac.uk/CGI/man-cgi?socket+2)
Thanks T.J
Let me just summarize saying that since TCP requires a connection, it needs the following APIs on server and client
server : socket(), bind(), **listen(), accept(),** recv(), send()
client  :  socket(), **connect(),**            send(), recv()

And since UDP is a connectionless protocol, it does not require connect() on the client and listen() and accept() on the server
server : socket(), bind(), recvfrom(), sendto()
client  :  socket(),            sendto(),    recvfrom()

Thanks.
Marking the thread as solved.

---

