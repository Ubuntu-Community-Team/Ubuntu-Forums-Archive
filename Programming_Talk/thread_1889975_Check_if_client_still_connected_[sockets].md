---
title: "Check if client still connected [sockets]"
date: 2011-12-02
forum: Programming Talk
---

### Post by cotzy on 2011-12-02
Hello.

I know this has probably been discussed over and over, but I have searched the net yesterday the whole day, and I haven't found a solution to my problem.

So I have this "server" which keeps a record [simple linked list] of all the clients that are connected, it only stops when i signal it with SIGTSTP, (I used the signal function). The "server" sends a message to all the clients that are still connected, so I want to check if a client is still connected, and if not, I want to delete it from my list. If i try to write to a invalid socket I get SIGPIPE signal, which would by alright if I could delete my node that holds the socket descriptor when handling the signal, but I can't. I tried to read first, but if the client is  still connected it won't pass the read function unless the client writes something to the server.
I have also tried using getpeername, but it returns 0 even if the client has disconnected.  

So what other ways are there to test if a socket descriptor is still valid ( in other words, if the client has disconnected), before writing to it.

Thank you, sorry for my poor English.

---

