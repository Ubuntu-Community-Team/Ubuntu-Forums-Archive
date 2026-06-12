---
title: "Threaded UDP datagram server in C"
date: 2009-03-13
forum: Programming Talk
---

### Post by mdecler2 on 2009-03-13
Thanks for your help in advance!;)
 
I am trying to build a threaded datagram server in C. Datagram is another word for UDP.

UDP clients need a new thread to process their request to the server. This thread must have sends and receives in it.

Datagram sockets can't use listen() or accept() which would solve my problem: listening for queued incoming connections and accepting them by returning a new socket descriptor. The socket descriptor can then be passed to a thread where the connection is handled.

Any ideas about managing multiple UDP client packets with sends and receives in threads? Do I need to use multiple ports or can I use just one?

---

### Post by dwhitney67 on 2009-03-13
The app you describe is cake (i.e. easy to do).  I would help you, but you have not provided any evidence that you've tried to formulate a solution yourself, or whether this is a class assignment.

UDP is deemed "connectionless", but it can support a connection (to a server) if many messages need to be sent.

A single UDP socket can be used to receive and send data.  If you require two threads (one to receive and one to send), ensure that both have access to the UDP socket.  You can accomplish this by passing the socket descriptor via the thread arg parameter.

---

### Post by mdecler2 on 2009-03-13
Are you suggesting that I should have one receive thread and possibly 10 sending threads? This would require shared resources so as to pass data between the sending receiving threads.

I would like to have a single thread per client that would handle all sends and receives to that client, if possible, without shared resources.

Suppose I have 10 clients. There would be 11 threads. 10 are handling sends and receives to the client (ACKS, data, etc) and the last thread is the main thread which is listening for new clients.

I would like all of this to be done on a single port.

The only way I see how to have a socket descriptor for each client is by 
1) using different ports for each client XOR 
2) allocating shared resources that would involve concurrency issues using your solution.

---

### Post by dwhitney67 on 2009-03-13
> **mdecler2 said:**
> ... and the last thread is the main thread which is listening for new clients.

Huh???  A UDP server does not listen for connections.

Every time a client sends a UDP datagram, using sendto(), behind the scenes a connection to the server is made, the data sent, and the connection is then broken.  If many messages have to be sent, then obviously the connect/disconnect procedure is wasteful.  Hence the client can setup a connection prior to sending data; but the server is unaware of this.  Btw, if the client is connected, then the send() function can be used.

> **mdecler2 said:**
> ...
I would like all of this to be done on a single port.

The only way I see how to have a socket descriptor for each client is by 
1) using different ports for each client XOR 
2) allocating shared resources that would involve concurrency issues using your solution.
I have not offered a solution, because I am unaware of your application's requirements.

All I have stated is that you can use a single UDP socket to send and receive data.  I also indicated that if you use separate threads to send and receive data, and wish to use the same socket, then the socket must be shared between the two threads.

---

### Post by tneva82 on 2009-03-13
> **mdecler2 said:**
> Suppose I have 10 clients. There would be 11 threads. 10 are handling sends and receives to the client (ACKS, data, etc) and the last thread is the main thread which is listening for new clients.

I would like all of this to be done on a single port.

The only way I see how to have a socket descriptor for each client is by 
1) using different ports for each client XOR 
2) allocating shared resources that would involve concurrency issues using your solution.

Just a random thought but if you aren't totally determined for one port why not have system where you have one port for each client that does direction for both way. One port where clients send up message that they are creating session and server creates new port for said client(and thread handling said port) and sends port number in reply. Client then closes initial port and opens new one based on data.

Not sure how good idea this is. I gave up UDP for a while after trying to figure out network logic with unreliability of UDP in mind and switched to TCP for a while.

---

### Post by mdecler2 on 2009-03-13
> **dwhitney67 said:**
> Huh???  A UDP server does not listen for connections.

It may not be listen()'ing for incoming connections but recvfrom() is waiting for some packet on a specified port so it can write it into a buffer and return a sockaddr structure. You know this.

> 
Every time a client sends a UDP datagram, using sendto(), behind the scenes a connection to the server is made, the data sent, and the connection is then broken.  

I am actually quite interested in this. What exactly do you mean by "connection"?  

> 
If many messages have to be sent, then obviously the connect/disconnect procedure is wasteful.  Hence the client can setup a connection prior to sending data; but the server is unaware of this.  Btw, if the client is connected, then the send() function can be used.

I am in control of the development for both client and server. In the man pages you'll see that connect works with UDP as well as TCP sockets. When I call connect(), to what extent is the socket descriptor provided tied to the client in the sockaddr structure? As far as I know, connect() just allows you to use send()s and recv()'s instead of the sendto() and recvfrom().

What if the server connect()ed and the client connect()ed? Would that be helpful? What is actually going on?

> 
I have not offered a solution, because I am unaware of your application's requirements.

I told you the requirements for the specific question I asked. I must wait for new clients, kick off threads to process their request and  leave the main thread open for new client requests. Let "request" be defined as a specific type of packet that the server gets by recvfrom() on the port that the server has bound. Let me know if this is not clear.

---

### Post by dwhitney67 on 2009-03-14
For your server, you did not indicate how many messages you can expect to receive per second; let's assume 100.

I would have the main thread create the UDP interface (that is the socket), a thread-safe queue, and two threads: one to receive, one to process the incoming messages and reply (if necessary).

So....  RECV-THREAD ----> Q ----> PROCESS-THREAD

A socket is thread safe, since there are independent buffers within it for receiving and sending.

Alternatively, and this might be overly complex for your needs, you can create a pool of threads that sit in a queue, and when a message is received, you pass that message to the next available thread for processing.  When the thread is finished, then it gets placed back onto the queue (in lieu of getting destroyed).

Rather than focus on making your application multi-threaded, I would first determine if your application can function as a single-thread.  I would also question your choice of development languages; if you are fluent with C, why not dip into using C++ (including Boost) for the added benefits?

At a minimum, your server should:

1.  Open a socket
2.  Bind to that socket (using address and port)
3.  Wait on a select() (only if the process has other things to do)
4.  If activity detected on the socket, call recvfrom()
5.  Process the message
6.  Send a reply (if necessary)
7.  Return to step 3.

Your client, should at a minimum:

1.  Open a socket
2.  Optionally connect() to the server
3.  If connected to the server, send messages using send(); otherwise sendto().
4.  Wait for a response using recv() or recvfrom()
5.  Repeat step 3 if necessary.

If the client will only be sending one message, or maybe even a few, step two is really optional.

---

