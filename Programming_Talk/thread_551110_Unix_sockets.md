---
title: "Unix sockets"
date: 2007-09-14
forum: Programming Talk
---

### Post by Rij on 2007-09-14
I have 3 processes: A, B and C.

The objective is all communication between B and C to go through A. So I want to open a socket between A and B and A and C.

All 3 processes have a sender and a listener thread. The code running is as follows:

--------------------------------------------------------------------------
listener thread:

... ....
#define SOCK_PATH "mysocket"
struct sockaddr_un local;

listener = socket(AF_UNIX, SOCK_STREAM, 0);
local.sun_family = AF_UNIX;
strcpy(local.sun_path, SOCK_PATH);
unlink(local.sun_path);
int len = strlen(local.sun_path) + sizeof(local.sun_family);
bind(listener, (struct sockaddr *)&local, len) ;
... ...

-------------------------------------------------------------------------------

sender thread has:
... ....

#define SOCK_PATH "mysocket"
struct sockaddr_un remote;

sockfd = socket(AF_UNIX, SOCK_STREAM, 0);
remote.sun_family = AF_UNIX;
strcpy(remote.sun_path, SOCK_PATH);
int len = strlen(remote.sun_path) + sizeof(remote.sun_family);
connect(sockfd, (struct sockaddr *)&remote, len) ;
... ...

-----------------------------------------------------------------------------------

Now my question is about the name field. As you can see, I am using the name "mysocket".  I **think** if the above code runs on all 3 processes, then the sockets are identified by a single name. So lets assume B wants to send data to C. It sends data on "mysocket" and it reaches A fine. Now if A wants to send it to C, how will it know which socket to send? If A sends on "mysocket" who does it reach? B? C? or comes back to itself, that is A?

Please help!

---

### Post by slavik on 2007-09-14
have you tried to run the code? I am pretty sure that the kernel will not confuse them as it tries to keep all processes separate. IOW, the kernel knows who reffers to "mysocket" and makes sure not confuse them.

note: I am 90-95% positive there is no problem :)

---

### Post by psusi on 2007-09-14
What is the "..." in the listener?  After the bind the listener needs to call accept() on the socket, and when a client connects, accept() will return a new socket that is connected to that client.  If you want to accept connections from more clients, you need to keep accept()ing on the original socket.

---

### Post by dwhitney67 on 2007-09-15
> **Rij said:**
> 
Now my question is about the name field. As you can see, I am using the name "mysocket".  I **think** if the above code runs on all 3 processes, then the sockets are identified by a single name. So lets assume B wants to send data to C. It sends data on "mysocket" and it reaches A fine. Now if A wants to send it to C, how will it know which socket to send? If A sends on "mysocket" who does it reach? B? C? or comes back to itself, that is A?

Please help!
Have you considered using unique names, or alternatively, a port numbers.  In fact, A requires at a minimum _only one socket_ that both B and C can share.  Each time a client (B or C or whatever) connect, then you have a _unique connection socket descriptor_ for the connecting client.  This unique socket descriptor can be used to receive and send data to the client.  The client, also with a socket descriptor, sends and receives data.

If you are still confused, think of this analogy.  Both server (A) and the clients (B and C) each have their own "highway".  However there isn't a bridge  connecting these highways until a connect() is performed by the client and the server accepts().  Once the bridge is in place, then you can have traffic flowing in both directions.

To summarize, A should be acting as server.  It really only needs to open one socket, bind(), and then accept() when a client connects.  Alternatively, you can also choose to create dedicated sockets, one for each client that you expect will connect to the server, but this is not necessary.  I personally recommend using port numbers in lieu of socket names.

The clients, B and C, also need to open a socket using the known port ID that the server has chosen, and also using a hostname where the server is located.  The hostname can be 127.0.0.1 (or "localhost"), or another IP address or alias.

The clients will connect() to the server using their socket descriptor.  This socket descriptor is used for send() and recv().

The unique socket descriptor managed by the server is also used for send() and recv().

Let me know if you still have other questions.  This subject of TCP sockets used to engulf my interest a lot, but with many projects using message queues (or files!), I do not tend to get into it that much anymore.

---

### Post by psusi on 2007-09-15
> **dwhitney67 said:**
> Have you considered using unique names, or alternatively, a port numbers.  In fact, A requires at a minimum _only one socket_ that both B and C can share.  Each time a client (B or C or whatever) connect, then you have a _unique connection socket descriptor_ for the connecting client.  This unique socket descriptor can be used to receive and send data to the client.  The client, also with a socket descriptor, sends and receives data.

Port numbers only exist in the world of TCP or UDP.  Unix domain sockets have names within the filesystem that you can see with ls and direct applications that operate on files to open and read/write to.  Assuming a SOCK_STREAM type socket, like TCP or UNIX, the server initially has only one socket, but the only thing it can do with that socket is accept() a connection, creating a new socket for that connection.  After accepting connections from two clients, you then have 3; the listening one and the two active ones.  If you use a SOCK_DRAM type of protocol like UDP, then the server only needs one socket that it can recvfrom() on to get messages from any number of clients, but then the clients need to bind() their own socket for you to sendto() back to.

---

### Post by dwhitney67 on 2007-09-15
You're right, I wasn't thinking.  AF_UNIX vs. AF_INET.  There are some subtle differences.

---

### Post by Rij on 2007-09-16
> **psusi said:**
> Port numbers only exist in the world of TCP or UDP.  Unix domain sockets have names within the filesystem that you can see with ls and direct applications that operate on files to open and read/write to.  Assuming a SOCK_STREAM type socket, like TCP or UNIX, the server initially has only one socket, but the only thing it can do with that socket is accept() a connection, creating a new socket for that connection.  After accepting connections from two clients, you then have 3; the listening one and the two active ones.  If you use a SOCK_DRAM type of protocol like UDP, then the server only needs one socket that it can recvfrom() on to get messages from any number of clients, but then the clients need to bind() their own socket for you to sendto() back to.

Ok. I seemed to have mixed up the socket fds. It works. But I have a different problem. After my clients (B and C) connect to A (successfully), I get first the msg: 
error: socket 3 hung up (the sock id corresponds to the server). 
Then client throws an error:
 recv: Connection refused; 
followed by:
 select: Bad file number

Any idea what's going on? I suspect I might have stale sockets and the kernel has run out of file numbers to be issued to me. If thats the case, how do I find out the stale sockets? I tried lsof but I don't seem to have permission on our school server to do this. Or is there something else going on?

---

### Post by dwhitney67 on 2007-09-17
Examine the code you have written for the server.  It appears that it is closing the socket after it receives something from a client.  In reality though, I can't really tell unless you post your code (in its entirety), or provide pseudocode or something similar.

A few things you should consider:

1) On both the server and client side, you should consider blanking-out (i.e. setting to all zeroes) the sockaddr_un object using memset() prior to initializing it with values.  Also in lieu of the arithmetic you use to compute "len" that is used in bind() and connect(), use SUN_LEN().  This function/macro needs a pointer to the sockaddr_un object.  So something like:
```
connect( s, (sockaddr*) &addr, SUN_LEN(&addr));
```

2) When your server terminates, it should unlink() the socket file.  If it never terminates (because say for example it is in an infinite-loop accepting connections), then after you abort the server, unlink the socket files manually using the "unlink" command.  Preferable though, if it is a server that never terminates, it should handle a SIGHUP signal that tells it to restart, and thus unlink any socket file(s) it may control.

3) The use of strcpy() is frowned upon these days.  Use strncpy() instead.

4)  How are you doing your threads?  Are you using boost, or do you have your own implementation (or wrappers) for the pthread library suite?  Either case, you should define you SOCK_PATH in the main thread and pass it as an arg to the sender/receiver threads.  Thus it is assured that they are always using the same name.

5) I recommend that process A (the server) maintain two sockets... one for the interface with B, the other for C.  If A is multi-threaded (i.e. there is a sender & receiver threads for B and similarly for C), that you create the sockets in the main thread, and then pass the appropriate socket descriptor as an arg to your individual threads.  This also applies to your design for B and C.


Concerning comment 5, since I have absolutely no idea what your project will morph into, the design suggestion I provided may not be applicable for your needs.  If you have any questions or want to bounce any ideas around, let everyone know.

Good luck.

---

### Post by Rij on 2007-09-17
Ok, maybe I should provide the entire premise and code for you to understand and help me better with my work.

The idea is to build a simulator for a networked system. So there are N nodes which are simulated by N processes. And then there is another process that simulates the pkt fwding along the links of the network. Initially, I have a main that forks and excve  N+1 processes.

Now, every "node" process will send the packet to the "network" process using a unix socket. The "network" will then send the pkt to the appropriate "node", again using unix sockets. 

A "node" has a sender and a listener thread. Ditto for the "network". They have an egress and ingress queue. I use POSIX threads. Also, there is a shared memory segment that holds some state information (for example rouitng table) that is shared by all. Note, this is read only segment.

In the "node", I first establish the connection with "network". Then I use the sockfd in the listener and sender threads:

struct sockaddr_un remote;
memset(remote, '\0', sizeof(struct sockaddr_un);
if ((sockfd = socket(AF_UNIX, SOCK_STREAM, 0)) == -1) { exit(1); }
remote.sun_family = AF_UNIX;
strncpy(remote.sun_path, SOCK_PATH, sizeof(SOCK_PATH));
int len = strlen(remote.sun_path) + sizeof(remote.sun_family);
int retry = 0; int maxtry = 10;  
  while (TRUE) {
    if (connect(sockfd, (struct sockaddr *)&remote, len) == -1) {
           if (retry++ <= maxtry) continue;
           perror(err_msg);
          exit(1);
    }
    else break;
    }


Also, in the "network", I save the socket fd corresponding to each "node" so that the "network" knows which fd to use when communicating with the corresponding node.

Finally, I have not shown some mem alloc code and error handling but I believe I have them ok. 

My questions:
1) Is my design sensible?
2) The code runs sometimes and not at other times. My previous posting, about stale sockets, was fixed when I fixed some mem alloc error. Now, I am having the following error msgs:
I defined my 5 node network like this with a pkt from 1 to 4. Also, my sockfds are as follows:
3 -- listener on network
4,5,6,.. -- sockfd on node 0, 1, .. etc
               1
            /
          /
        0 -------------- 2
                             /  \
                          /       \
                        3        4
 
And I get the foll. error:
listener = 3
network ready to acept
1: made connection on skt = 3
network ready to acept
2: made connection on skt = 3
network ready to acept
error from client data
Network: socket 5 hung up
network ready to acept
0: made connection on skt = 3
network ready to acept
3: made connection on skt = 3
network ready to acept
4: made connection on skt = 3
network ready to acept
error from client data
Network: socket 4 hung up
network ready to acept
error from client data
Network: socket 5 hung up
network ready to acept
error from client data
Network: socket 6 hung up
network ready to acept
error from client data
Network: socket 7 hung up
         
Boy, that took me an hour to write up. Please help! Please feel free to criticize (however scathing) and/or suggest(however obvious).

Thanks folks.

Here is the code.
----------------------------------------------
Network Listener thread:

void *ListenerT(void *null) {
    fd_set master, read_fds;
    struct sockaddr_un myaddr, remoteaddr;
    int fdmax, listener, newfd, i, nbytes;
    socklen_t addrlen;

    FD_ZERO(&master);    // clear the master and temp sets
    FD_ZERO(&read_fds);
    memset(&myaddr, '\0', sizeof(struct sockaddr_un));
    memset (&remoteaddr, '\0', sizeof(struct sockaddr_un));

    // get the listener
    if ((listener = socket(AF_UNIX, SOCK_STREAM, 0)) == -1) exit(1);
    // lose the pesky "address already in use" error message
    if (setsockopt(listener, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1) { perror("setsockopt"); exit(1);}

    // bind
    myaddr.sun_family = AF_UNIX;
    strcpy(myaddr.sun_path, SOCK_PATH);
    unlink(myaddr.sun_path);
    int len = strlen(myaddr.sun_path) + sizeof(myaddr.sun_family);
    if (bind(listener, (struct sockaddr *)&myaddr, len) == -1) { exit(1);}

    // listen
    if (listen(listener, 10) == -1) { perror("listen"); exit(1); }

    // add the listener to the master set
    FD_SET(listener, &master);

    // keep track of the biggest file descriptor
    fdmax = listener; // so far, it's this one

    // main loop
    for(;;) {
        read_fds = master; // copy it
        if (select(fdmax+1, &read_fds, NULL, NULL, NULL) == -1) exit(1); 
        // run through the existing connections looking for data to read
        for(i = 0; i <= fdmax; i++) {
            if (FD_ISSET(i, &read_fds)) { // we got one!!
                if (i == listener) { // handle new connections
                    addrlen = sizeof(remoteaddr);
                    if ((newfd = accept(listener, (struct sockaddr *)&remoteaddr, &addrlen)) == -1) perror("accept");
                    else {
                        FD_SET(newfd, &master); // add to master set
                        if (newfd > fdmax) {  fdmax = newfd; }  // keep track of the maximum
                    }
                }
                else {
                   SendPkt *recvd_pkt; pktPoolMgr(ALLOC, &recvd_pkt);
                    // handle data from a client
                    nbytes = recv(i, recvd_pkt, sizeof(SendPkt), 0);
                        if (nbytes == 0) // connection closed
                        else if (nbytes < 0) { 
                            perror("recv");
                            close(i); FD_CLR(i, &master);
                            pktPoolMgr(FREE, &recvd_pkt);
                        }
                       else {
                        // we got some data from a client
                    } // end if/else for nbytes
                } // end if/else for connection/data
               // cout << "finished processing the got one FD\n";
            } // end FD_ISSET
        } // end for loop
    } // end main for loop

}
----------------------------------------------

Network Sender thread:
void *SenderT(void *null) {

while (TRUE) {
pthread_mutex_lock(&egress_mutex);
if (egress.size() <= 0) pthread_cond_wait(&egress_cond, &egress_mutex);
SendPkt* __pkt = egress[0];
egress.erase(egress.begin());
pthread_mutex_unlock(&egress_mutex);

int pktlen = sizeof(SendPkt);
int sent_len = send(sockets[__pkt->next_hop], __pkt, pktlen, 0);
if (sent_len < 0) { cout << "Send failed!\n"; }
else if (sent_len < pktlen) cout << "Not entire packet sent.\n";
else cout << "Packet sent successfully.\n";
pktPoolMgr(FREE, &__pkt);
}
}

----------------------------------------------

Node Listener thread:
void *ListenerT(void *null) {
    int nbytes;
    fd_set master, readfds;
    FD_ZERO(&readfds); FD_ZERO(&master);
    FD_SET(sockfd, &master);
    // main loop
    for(;;) {
          readfds = master; // copy it
          if (select(sockfd+1, &readfds, NULL, NULL, NULL) == -1) exit(1);
          if (FD_ISSET(sockfd, &readfds)) { // we got one!!
                SendPkt *recvd_pkt; pktPoolMgr(ALLOC, &recvd_pkt);
                nbytes = recv(sockfd, recvd_pkt, sizeof(SendPkt), 0);
               if (nbytes == 0)  ... // connection closed
               else if (nbytes <0) { perror("recv"); close(sockfd); }
               else {	
                        pthread_mutex_lock(&ingress_mutex);
                        ingress.push_back(recvd_pkt);
	pthread_cond_signal(&ingress_cond);
	pthread_mutex_unlock(&ingress_mutex);
                }
         }
    } // end main for loop

}
----------------------------------------------

Node Sender thread:

void *SenderT(void *null) {

while (TRUE) {
     pthread_mutex_lock(&egress_mutex);
    if (egress.size() <= 0) pthread_cond_wait(&egress_cond, &egress_mutex);
    SendPkt *__pkt = egress[0];
    egress.erase(egress.begin());
    pthread_mutex_unlock(&egress_mutex);


   int pktlen = sizeof(SendPkt);
   int sent_len = send(sockfd, __pkt, pktlen, 0);
   if (sent_len < 0) { cout << ID << ": Send failed!\n"; }
   else if (sent_len < pktlen) cout << "Not entire packet sent.\n";
   else cout << ID << ": Send success\n";
   pktPoolMgr(FREE, &__pkt);
}
}

---------------------------------------------

---

### Post by dwhitney67 on 2007-09-17
Your design seems reasonable, however I would try to pretty up the code.  It is a little hard to follow.

I would use boost for your pthread needs.  If you do want to use boost, then consider creating wrapper classes that encapsulate the pthread libraries.

Also try to focus on things that could potentially not be thread-safe.  For instance cout.  Also check the thread-safeness of pktPoolMgr() as well.

Lastly, and you probably already know this, ensure that your "consumers" (i.e. the receive threads) are started before any of the "producers" (i.e. send threads).

I have written applications in the past that dealt with multi-threading and the use of TCP ports, but never with Unix Sockets.  The concept however is very similar.  I will PM you with a link to a TCP/UDP library suite (that I tinker with now and then) that may be of use to you.

---

### Post by psusi on 2007-09-17
Ok, I will start with specific problems with your existing code, then get into the design:

First, you must remember that recv and send do not have to, and often do not, send or receive all of the bytes requested.  If you ask receive to return 30 bytes, but only 15 are currently in the buffer, then you only get 15.  You must check the return code and if you need more bytes to continue, call recv again with the address incremented by the number of bytes received and the size decremented by the number of bytes received.  

Second, it sounds like you meant for each "client" to have its own ingress queue of messages, but it looks like are using a single global queue and lock.  

As for the design, if this is just for practice, then all is well and good, but for real world use, the primary reason for using unix domain sockets is so that non sockets aware applications can be told to open that file and be connected to the server.  That and for client processes launched later to connect to a server process that has been running already on a well known file name.  

If you just want to have threads or forked child processes communicate, you might be better off with a socketpair() or a pair of pipe() fds instead.  They are much easier to create, do not pollute the filesystem, and are faster.  

Another thing to consider is that rather than make your own "router" thread, you could just let the network layer in the kernel handle that for you.  Instead of connecting to the server thread, each node could just connect directly to whichever other node it wishes to communicate with, or if you want to do broadcast type messages you could use a SOCK_MSG type socket of PF_UNIX or PF_INET, then use sendto() to send messages to an individual address assigned to each node, or to a broadcast address that they all are listening on.

---

### Post by Rij on 2007-09-18
I am glad you brought up socketpairs. I did consider it. But consider my case in which I will have thousands of "nodes" connected to the "network". Doesn't a socketpair correspond to a file? Which is better, in terms of both performance and resource utilization, thousands of open socketpairs or thousands of open socket connections. An insight into this will be very helpful.

---

### Post by psusi on 2007-09-18
socketpairs are lighter weight than unix domain sockets, and pipes are lighter still.  Also select() does not scale well into the thousands of fds.  poll() and epoll() do much better with large numbers like that.

If you can just let the kernel route the messages instead of reading and writing back and forth in the "router" thread, it will also be much faster.

---

