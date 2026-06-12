---
title: "TCP chat program"
date: 2010-02-10
forum: Programming Talk
---

### Post by kwyto on 2010-02-10
Hi guys, I'm doing a chat program in C\C++ for Windows using Visual Studio. It's a very simple program. The server receives a message from a client and echoes it to the other clients. The server side creates a socket and accepts all incoming connections. So I went and save the the socket file descriptor in a array, in order to access all of them. I'm using the same socket for all of them, the system creates a virtual port and keeps the connection. Oh, every time a new connection is accepted, the server spawns a new thread. The thread, is supposed to take care of the sending and receiving of messages. Do I need to create a separate socket for all the different connections? The server just hangs in recv(), even though it accepts a connection. Should I look in the threads creation. Guys, any help is much appreciate it. Thank you for your time.

---

### Post by dwhitney67 on 2010-02-10
Great, another Chat application on the horizon.

I never understood why TCP is favored over UDP, but whatever.

If you plan to use your server as the central hub for all communications between clients, then you will need to define a protocol which will enable a client to specifically direct his messages to another client, and not all clients.  Perhaps you have thought of this already; or perhaps you plan to broadcast a client's message to all connected clients?

As for the server, it will need to accept connections from one or more clients.  Spawning a thread to handle each client is a good idea, but not necessary.  When a client connects, a unique socket descriptor is created (by the kernel) for it to communicate with the server.  Do _not_ confuse this socket descriptor with the listen socket descriptor used by the server to accept connections.

You can easily maintain a list of connected clients using FD_SET.  Using this set, in conjunction with select(), should enable you to determine which client is sending a message at any given time.  Note that it is possible to include your server's listen socket in this set too.

If your ultimate intent is to develop a Peer-to-Peer (P2P) chat application, then your model could be refined.  Each client would need to support its own listen socket, so that another client (once aware of another client), can connect directly to its peer.  In such a model, the server mainly serves as the broker that notifies other clients when a new client is aboard and ready for connections.

If you have specific questions, please let me know.  Having worked with the M$ socket API, I know there are some minor differences between it and the Linux API.

---

### Post by kwyto on 2010-02-10
It's for understanding purposes. Basically, the server echoes every message to everybody connected. And yes, I was confusing the listening socket and the socket returned by the accept() function. I fixed that. Now, I have read some about select() and non-blocking sockets. Can I use select() with blocking sockets? Any tutorial or reference would help. Also, I need to do the same for UDP. So no worries, no one is forgotten

---

### Post by dwhitney67 on 2010-02-10
select() works with both blocking & non-blocking sockets; in other words, it doesn't care.

select() itself is a blocking call; of course, you can specify a timeout period so that your app can perform other tasks if there is no activity within the specified period on any of the sockets that you are monitoring.

select() is documented in the Linux man-pages (and includes an example), or you can Google for it.

---

