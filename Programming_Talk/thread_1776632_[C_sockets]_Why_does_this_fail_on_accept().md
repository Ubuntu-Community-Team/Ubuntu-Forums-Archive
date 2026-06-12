---
title: "[C sockets] Why does this fail on accept()"
date: 2011-06-06
forum: Programming Talk
---

### Post by donsy on 2011-06-06
Totally new to socket programming, I'm trying to get this Echo Server to work but it fails on the accept(): 
```

//TCPEchoServer.c
#include <stdio.h>      // for printf() and fprintf()
#include <sys/socket.h> // for socket(), bind(), and connect()
#include <arpa/inet.h>  // for sockaddr_in and inet_ntoa()
#include <stdlib.h>     // for atoi()
#include <string.h>     // for memset()
#include <unistd.h>     // for close()

#define  MAXPENDING  5  // Maximum outstanding connection requests

void DieWithError( char *errorMessage );
void HandleTCPClient( int clntSocket );

int main( int argc, char *argv[] )
{
    int servSock;  // Socket descriptor for server
    int clntSock;  // Socket descriptor for client
    struct sockaddr_in echoServAddr;  // Local address
    struct sockaddr_in echoClntAddr;  // Client address
    unsigned short echoServPort;      // Server port
    size_t clntLen;             // Length of client address data structure
    
    if (argc != 2)
    {
        fprintf(stderr, "Usage: %s <Server Port>\n", argv[0]);
        exit(1);
    }

    echoServPort = atoi(argv[1]); // First arg: local port
    
    // Create socket for incoming connections
    if ((servSock = socket(PF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0)
        DieWithError("Socket() failed");
        
    // Construct local address structure
    memset( &echoServAddr, 0, sizeof(echoServAddr) ); // Zero out structure
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(INADDR_ANY); // Any incoming interface
    echoServAddr.sin_port = htons(echoServPort);      // Local port
    
    // Bind to the local address
    if (bind(servSock, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr)) < 0)
        DieWithError("bind() failed");
        
    for(;;) // Run forever
    {
        // Set the size of the in-out parameter
        clntLen = sizeof(echoClntAddr);
        
        // Wait for a client to connect
        if ((clntSock = accept(servSock, (struct sockaddr *) &echoClntAddr, &clntLen)) < 0)
            DieWithError("accept() failed");
            
        // clntSock is connected to a client
        
        printf("Handling client %s\n", inet_ntoa(echoClntAddr.sin_addr));
        
        HandleTCPClient(clntSock);
    }
    // NOT REACHED
}
```Helper modules are:
```

//DieWithError.c
#include <stdio.h> // for perror()
#include <stdlib.h> // for exit()

void DieWithError( char *errorMessage )
{
    perror( errorMessage );
    exit(1);
}
``````

//HandleTCPClient.c
#include <stdio.h>      // for printf() and fprintf()
#include <sys/socket.h> // for recv() and send()
#include <unistd.h>     // for close()

#define  RCVBUFSIZE  32 // Size of receive buffer

void DieWithError( char *errorMessage );  // Error handling function

void HandleTCPClient( int clntSocket )
{
    char echoBuffer[ RCVBUFSIZE ];  // Buffer for echo string
    int recvMsgSize;                // Size of received message
    
    // Receive message from client
    if ((recvMsgSize = recv(clntSocket, echoBuffer, RCVBUFSIZE, 0)) < 0)
        DieWithError("recv() failed");
        
    // Send received string and receive again until end of transmission
    while (recvMsgSize > 0)  // Zero indicates end of transmission
    {
        // Echo message back to client
        if (send(clntSocket, echoBuffer, recvMsgSize, 0) != recvMsgSize)
            DieWithError("send() failed");
        
        // See if there is more data to receive
        if ((recvMsgSize = recv(clntSocket, echoBuffer, RCVBUFSIZE, 0)) < 0)
            DieWithError("recv() failed");
    }
    
    close(clntSocket);  // Close client socket     
}

```When I compile all three of the files together and execute TCPEchoServer on port 50000 (127.0.0.1) I get this error message:
     "accept() failed: Invalid argument"
But the arguments look OK as far as I can tell.

---

### Post by johnl on 2011-06-06
You need to call listen() on your server socket prior to trying to accept connections:

```

if (listen(servSock, MAXPENDING) < 0) {
    /* error handling */
}

```

With this added right after the bind, your program works swell.

Also, your **clntLen** variable should be of type **socklen_t**, but this is probably not a show stopper.

---

### Post by donsy on 2011-06-06
> **johnl said:**
> You need to call listen() on your server socket prior to trying to accept connections:

```

if (listen(servSock, MAXPENDING) < 0) {
    /* error handling */
}

```With this added right after the bind, your program works swell.

Also, your **clntLen** variable should be of type **socklen_t**, but this is probably not a show stopper.

 TCPEchoServer seems to work fine now thanks to your suggestions, but now I don't get any response when I execute TCPEchoClient with the arguments 127.0.0.1 Hello 50000
```

//TCPEchoClient.c
#include <stdio.h>      // for printf() and fprintf()
#include <sys/socket.h> // for socket(), connect(), send(), and recv()
#include <arpa/inet.h>  // for sockaddr_in, and inet_addr()
#include <stdlib.h>     // for atoi()
#include <string.h>     // for memset()
#include <unistd.h>     // for close()

#define  RCVBUFSIZE  32

void DieWithError( char *errorMessage );

int main( int argc, char *argv[] )
{
    int sock;
    struct sockaddr_in echoServAddr;
    unsigned short echoServPort;
    char *servIP;
    char *echoString;
    char echoBuffer[ RCVBUFSIZE ];
    unsigned int echoStringLen;
    int bytesRcvd, totalBytesRcvd;
    
    if (( argc < 3) || (argc > 4))
    {
        fprintf( stderr, "Usage: %s <Server IP> <Echo Word> [Echo Port]\n",  argv[0] );
        exit(1);
    }
     
    servIP = argv[1];     // First arg: server IP address (dotted quad)
    echoString = argv[2]; // Second arg: string to echo
    if ( argc == 4 )
        echoServPort = atoi(argv[3]); // Use given port, if any
    else
        echoServPort = 7; // 7 is the well-known port for the echo service
        
    // Create a reliable, stream socket using TCP
    if ((sock = socket(PF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0 )
        DieWithError("socket() failed");
    
    // Construct the server address structure
    memset( &echoServAddr, 0, sizeof(echoServAddr) ); // Zero out structure
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = inet_addr(servIP);
    echoServAddr.sin_port = htons(echoServPort);
    
    echoStringLen = strlen(echoString);
    
    // Send the string to the server
    if (send(sock, echoString, echoStringLen, 0) != echoStringLen)
        DieWithError("send() sent a different number of bytes than expected");
        
    // Receive the same string back from the server
    totalBytesRcvd = 0;
    printf("Received: ");
    while (totalBytesRcvd < echoStringLen)
    {
        // Receive up to the buffer siize (minus 1 for null char) bytes from the sender
        if ((bytesRcvd = recv(sock, echoBuffer, RCVBUFSIZE - 1, 0)) <= 0)
            DieWithError("recv() failed or connection closed prematurely");
        totalBytesRcvd += bytesRcvd;  // Keep tally of total bytes
        echoBuffer[bytesRcvd] = '\0'; // Terminate the string!
        printf("%s", echoBuffer);
    }
    
    printf("\n"); // Print a final linefeed
    close( sock );  
    exit(0);
}
```

---

### Post by johnl on 2011-06-06
You need to call **connect()** with the echoServAddr struct you create prior to calling send.

```

if (connect(sock, (struct sockaddr*)&echoServAddr, sizeof(echoServAddr) < 0) {
    /* error */
}

```

That should likely solve your problems.

Here's a quick rundown (for TCP at least):

**Server:** socket() -> bind() -> listen() -> accept() -> send()/recv() -> close()
**Client:** socket() -> connect() -> send()/recv() -> close()

---

### Post by donsy on 2011-06-06
> **johnl said:**
> You need to call **connect()** with the echoServAddr struct you create prior to calling send.

```

if (connect(sock, (struct sockaddr*)&echoServAddr, sizeof(echoServAddr) < 0) {
    /* error */
}

```That should likely solve your problems.

Here's a quick rundown (for TCP at least):

**Server:** socket() -> bind() -> listen() -> accept() -> send()/recv() -> close()
**Client:** socket() -> connect() -> send()/recv() -> close()

 [SIZE=2]Works great! Thanks a lot for all your help.[/SIZE]

---

