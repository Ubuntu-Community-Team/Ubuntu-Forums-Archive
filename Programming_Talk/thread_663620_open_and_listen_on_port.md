---
title: "open and listen on port"
date: 2008-01-10
forum: Programming Talk
---

### Post by tocleora on 2008-01-10
I would like an app that's fairly easy to use that I can open a port and communicate with it.  I have extensive knowledge of Visual Basic and PHP so hopefully something that is similar I can use fairly easily.  So if you could tell me the name of the programming tool and possibly the code to invoke this I'd appreciate it! :)

---

### Post by ghostdog74 on 2008-01-10
you can try [netcat]("http://netcat.sourceforge.net/")

---

### Post by tocleora on 2008-01-10
I should probably clarify what I'm wanting to use it for... we have a game server that our gamers are complaining that when our admins aren't on people are causing trouble, using foul language, etc.  So what I'd like to accomplish is a way to watch for foul language and potentially issue commands I might typically issue to kick the gamer who used foul language. I figured my first step though would be to create a program that would at least let me connect to the server and see what kind of results I get back.  something premade I'm guessing wouldn't work unless it somehow allows me to send data in correspondance to data received...

---

### Post by LaRoza on 2008-01-10
Python, C and Java (among others) can do that. It is not what I usually program, so I can't offer any specific advice.

---

### Post by sznurek on 2008-01-10
Some examples:
Java: [http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html](http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html)
C++:
[PHP]
#include <arpa/inet.h>

#include <netdb.h>
#include <netinet/in.h>
#include <unistd.h>
#include <iostream>

#define MAX_MSG 100
#define LINE_ARRAY_SIZE (MAX_MSG+1)

using namespace std;

int main()
{
  int listenSocket, connectSocket, i;
  unsigned short int listenPort;
  socklen_t clientAddressLength;
  struct sockaddr_in clientAddress, serverAddress;
  char line[LINE_ARRAY_SIZE];

  cout << "Enter port number to listen on (between 1500 and 65000): ";
  cin >> listenPort;

  // Create socket for listening for client connection requests.
  listenSocket = socket(AF_INET, SOCK_STREAM, 0);
  if (listenSocket < 0) {
    cerr << "cannot create listen socket";
    exit(1);
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
    cerr << "cannot bind socket";
    exit(1);
  }

  // Wait for connections from clients.
  // This is a non-blocking call; i.e., it registers this program with
  // the system as expecting connections on this socket, and then
  // this thread of execution continues on.
  listen(listenSocket, 5);
  
  while (1) {
    cout << "Waiting for TCP connection on port " << listenPort << " ...\n";

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
      cerr << "cannot accept connection ";
      exit(1);
    }
    
    // Show the IP address of the client.
    // inet_ntoa() converts an IP address from binary form to the
    // standard "numbers and dots" notation.
    cout << "  connected to " << inet_ntoa(clientAddress.sin_addr);

    // Show the client's port number.
    // ntohs() converts a short int from network byte order (which is
    // Most Significant Byte first) to host byte order (which on x86,
    // for example, is Least Significant Byte first).
    cout << ":" << ntohs(clientAddress.sin_port) << "\n";

    // Read lines from socket, using recv(), storing them in the line
    // array.  If no messages are currently available, recv() blocks
    // until one arrives.
    // First set line to all zeroes, so we'll know where the end of
    // the string is.
    memset(line, 0x0, LINE_ARRAY_SIZE);
    while (recv(connectSocket, line, MAX_MSG, 0) > 0) {
      cout << "  --  " << line << "\n";

      // Convert line to upper case.
      for (i = 0; line[i] != '\0'; i++)
        line[i] = toupper(line[i]);

      // Send converted line back to client.
      if (send(connectSocket, line, strlen(line) + 1, 0) < 0)
        cerr << "Error: cannot send modified data";

      memset(line, 0x0, LINE_ARRAY_SIZE);  // set line to all zeroes
    }
  }
}
[/PHP]
From: [http://sage.mc.yu.edu/kbeen/teaching/networking/resources/sockets.html](http://sage.mc.yu.edu/kbeen/teaching/networking/resources/sockets.html)

Python: [http://www.amk.ca/python/howto/sockets/](http://www.amk.ca/python/howto/sockets/)

Hope this help.

---

### Post by amo-ej1 on 2008-01-11
You said you have extensive knowledge of php, well php lets you also write command line applications  and  has socket support. So you could potentially write it yourself.

---

