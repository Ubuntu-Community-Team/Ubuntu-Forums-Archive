---
title: "doubt about select call for sockets"
date: 2012-05-07
forum: Programming Talk
---

### Post by chuchi on 2012-05-07
Hi everyone!!! I have a doubt about the select call for concurrent  sockets. Surfing the net I have read that using select I can deal with  many clients at the same time, and that I can use this call instead of  fork to create a child to deal with a client.
 
But taking this pseudo code as an example
 
   ```
 res=select (maxfd,readfs,NULL,NULL);//select blocks newsockfd=accept(listeningsock);  server_response_client(); /*suppose this communication between this server and client takes 10 seconds*/

```  if during server_response_client(), a new client connects immediately  to the server, this new client will have to wait 10 seconds until the  server has finished with the first client. Am I right??
 
So this is the same scenario as the system call listen(sockfd, LISTEN_Q);, and then accept(sockfd)
 
I have another question. select is aimed to manage several read/write  descriptors, but if I am only to use a very only one descriptor (the [[COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]server [/FONT][/FONT][/COLOR][FONT=Verdana][COLOR=blue !important][FONT=Verdana]socket[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") descriptor) Why is select useful for me??
 
Thank you very much!!!

---

### Post by dwhitney67 on 2012-05-07
Typically when I use select(), it is to monitor activity from the server's listen socket and any activity from the client's that may have already connected.

If you are designing a trivial server that will handle several clients, I would suggest that you fork a new process, or use a separate thread, to handle each client.

If the application is something more complex, then use threads from a thread-pool.

As for select(), you missed the final parameter in your example, which is the timeout.  It can be NULL (no timeout considered), or some other value.

---

### Post by chuchi on 2012-05-07
Hi dwhitney67! Thank you very much for reply. It is only that I wanted to be sure about what select could make for me.
 

 In my case I am going to develop an iterative server which will deal only with a client at a time. So if several clients arrive at the same time, they will be dispatched iteratively, as the call to listen(sockfd, backlog) will set the maximum number of clients.
 

 Thank you very very much!

---

### Post by dwhitney67 on 2012-05-07
> **chuchi said:**
> Hi dwhitney67! Thank you very much for reply. It is only that I wanted to be sure about what select could make for me.
 

 In my case I am going to develop an iterative server which will deal only with a client at a time. So if several clients arrive at the same time, they will be dispatched iteratively, as the call to listen(sockfd, backlog) will set the maximum number of clients.
 

 Thank you very very much!

listen() does not control the number of clients that can connect to the server.  It only controls how many can be waiting before accept() is called by the server to handle a connection from a client.

---

