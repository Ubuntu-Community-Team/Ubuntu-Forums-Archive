---
title: "How to listen on a socket for only 10 seconds"
date: 2007-06-18
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-18
Hi,

I read the following code which open a server socket for client request.
However,  i would like to know how can I change it so that i just listen for client requestfor 10 seconds, after that, it bows out?


```
 // Create socket for listening for client connection requests.
  listenSocket = socket(AF_INET, SOCK_STREAM, 0);
  if (listenSocket < 0) {
    std::cout << "cannot create listen socket";
    return;
  }
  
  // Bind listen socket to listen port.  First set various fields in
  // the serverAddress structure, then call bind().
  // htonl() and htons() convert long integers and short integers
  // (respectively) from host byte order (on x86 this is Least
  // Significant Byte first) to network byte order (Most Significant
  // Byte first).
  serverAddress.sin_family = AF_INET;
  serverAddress.sin_addr.s_addr = htonl(INADDR_ANY);
  serverAddress.sin_port = htons(listenPort);
  
  if (bind(listenSocket,
           (struct sockaddr *) &serverAddress,
           sizeof(serverAddress)) < 0) {
    std::cout << "cannot bind socket";
    return;
  }

  // Wait for connections from clients.
  // This is a non-blocking call; i.e., it registers this program with
  // the system as expecting connections on this socket, and then
  // this thread of execution continues on.
  listen(listenSocket, 10);
      
  int count = 0;

    while (1) {
    std::cout << "Waiting for TCP connection on port " << listenPort << " ...\n";

    // Accept a connection with a client that is requesting one.  The
    // accept() call is a blocking call; i.e., this thread of
    // execution stops until a connection comes in.
    // connectSocket is a new socket that the system provides,
    // separate from listenSocket.  We *could* accept more
    // connections on listenSocket, before connectSocket is closed,
    // but this program doesn't do that.
    clientAddressLength = sizeof(clientAddress);
    connectSocket = accept(listenSocket,
                           (struct sockaddr *) &clientAddress,
                           &clientAddressLength);
    if (connectSocket < 0) {
      std::cout << "cannot accept connection ";
      return;
    }
```

Thank you.

---

### Post by brooksbp on 2007-06-18
you'd have to implement a 'clock' in the software.  Instead of while(1) do a time check to make sure that the loop stops once 10 seconds have been reached.

---

### Post by hod139 on 2007-06-18
You can include time.h, and do the following:
```

  clock_t finish;
  finish = clock() + 10*CLOCKS_PER_SEC;
  while (clock() < finish); 

```

---

### Post by kpatz on 2007-06-18
Look up select() in the man pages.  The select() function lets your program wait for an event (such as a connection request) on one or more file descriptors (sockets in your case).  There is a timeout parameter that you can use to achieve your 10 second timeout as well.

The advantage of using select over a while loop with a non-blocking listen call is that your program will sleep for the 10 seconds (or until a connection request is received on the socket) rather than looping and consuming CPU cycles.

Select is also handy for handling multiple connections in a single thread.  Say if you have a daemon listening on a socket, and multiple clients connect to the socket, select() will return which socket(s) have pending actions on them so your program can act on them.

---

