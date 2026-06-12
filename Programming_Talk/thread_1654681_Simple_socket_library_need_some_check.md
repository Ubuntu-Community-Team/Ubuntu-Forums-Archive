---
title: "Simple socket library need some check"
date: 2010-12-28
forum: Programming Talk
---

### Post by PC-BSD on 2010-12-28
I create this simple library to use in future, it can be compiled but when I use it it fail.
OpenSocket.h file:
```

#ifndef _OPENSOCKET_H_
#define _OPENSOCKET_H_

/* handle for socket */
typedef int hSOCK;

/* socket creation */
typedef struct __sock_s
 {
     int domain;
     int type;
     int protocol;
 } *sock_s;

/* struct to hold socket information */
typedef struct sockaddr_in *sock_i;


hSOCK socket_open(sock_s ssock);
void socket_init(sock_i tsock);
int socket_listen(hSOCK sock, sock_i tsock, int family, const char *address, unsigned int port);
hSOCK socket_accept(hSOCK sock, sock_i csock);
int socket_connect(hSOCK sock, sock_i tsock);
int socket_send_len(hSOCK csock, char *len, int flags);
int socket_send(hSOCK sock, char *data, unsigned int len, int flags);
int socket_recv_len(hSOCK sock, int flags);
char *socket_recv(hSOCK sock, int len, int flags);
int socket_close(hSOCK sock);

#endif

```OpenSocket.c:
```

#include<unistd.h>
#include<stdlib.h>
#include<string.h>
#include<sys/socket.h>
#include<sys/types.h>
#include<netinet/in.h>
#include<arpa/inet.h>

typedef int hSOCK;

/* socket creation */
typedef struct __sock_s
 {
     int domain;
     int type;
     int protocol;
 } *sock_s;

/* struct to hold socket information */
typedef struct sockaddr_in *sock_i;

/* Create socket and return handle */
hSOCK socket_open(sock_s ssock)
 {
     int fd;
     fd = socket(ssock->domain, ssock->protocol, ssock->type);
     if(!fd)
      return -1;
     else
      return (fd);
 }

/* Initializing socket */
void socket_init(sock_i tsock)
 {
     memset(&tsock, 0, sizeof(tsock));
 }

/* Setting socket information and listening in given port */
int socket_listen(hSOCK sock, sock_i tsock, int family, const char *address, unsigned int port)
 {
    int stat;
    tsock->sin_family = family;
    tsock->sin_addr.s_addr = inet_addr(address);
    tsock->sin_port = htons(port);
    stat = bind(sock, (struct sockaddr*)&tsock, sizeof(tsock));
    if(stat == -1)
     return (stat);
    stat = listen(sock, 5);
    if(stat == -1)
     return -2;
    else
     return (stat);
 }

/* Accept a connection from client and return handle to that */
hSOCK socket_accept(hSOCK sock, sock_i csock)
 {
    int hCLT;
    socklen_t len;
    len = sizeof(csock);
    hCLT = accept(sock, (struct sockaddr*)&csock, &len);
    if(!hCLT)
     return -1;
    else
     return (hCLT);
 }

/* Connect to a host */
int socket_connect(hSOCK sock, sock_i tsock)
 {
     int stat;
     stat = connect(sock, (struct sockaddr*)&tsock, sizeof(tsock));
     if(!stat)
      return -1;
     else
     return (stat);
 }
 
/* Send the next size of data to server */
int socket_send_len(hSOCK sock, char *len, int flags)
 {
     int stat;
     stat = send(sock, len, sizeof(len), flags);
     if(!stat)
      return -1;
     else
     return (stat);
 }

/* Send the actual data */
int socket_send(hSOCK sock, char *data, unsigned int len, int flags)
 {
     int stat;
     stat = send(sock, data, len, flags);
     if(!stat)
      return -1;
     else
      return (stat);
 }

/* Recieve the amount of data to recieve from the peer */
int socket_recv_len(hSOCK sock, int flags)
 {
     int stat;
     unsigned int len;
     char *Buffer = NULL;
     Buffer = (char*)malloc(sizeof(int));
     if(!Buffer)
      return -1;
     stat = recv(sock, Buffer, sizeof(int), flags);
     if(!stat)
      return -2;
     else
      {
          len = atoi(Buffer);
          return (len);
      }
 }

/* Receive data from the peer and return pointer to it */
char *socket_recv(hSOCK sock, int len, int flags)
 {
     int stat;
     char *Buffer = NULL;
     Buffer = (char*)malloc(sizeof(char)*len);
     if(!Buffer)
      return NULL;
     stat = recv(sock, Buffer, len, flags);
     if(!stat)
      return NULL;
     else
      return (Buffer);
 }
 
int socket_close(hSOCK sock)
 {
     return close(sock);
 }


```Makefile:
```

CC= cc
CFLAGS= -c -Wall
AR= ar
libSPLT.o: OpenSocket.c OpenSocket.h
    $(CC) OpenSocket.c $(CFLAGS)

install:
    $(AR) rc libOpenSocket.a OpenSocket.o
    cp libOpenSocket.a /usr/local/lib
    cp OpenSocket.h /usr/local/include/OpenSocket.h
uninstall:
    rm /usr/local/lib/OpenSocket.a
    rm /usr/local/include/OpenSocket.h
.PHONY: clean
clean:
    rm -f *.o
    rm -f *.a

```simple server, stest.c:
```

#include<stdio.h>
#include<sys/socket.h>
#include<sys/types.h>
#include<netinet/in.h>
#include<OpenSocket.h>

main()
{
sock_i Server;
sock_s socket;
hSOCK sock, stat;
socket->domain = AF_INET;
socket->type = SOCK_STREAM;
socket->protocol = 0;
socket_init(Server);
sock = socket_open(socket);
if(sock<0)
 printf("error to create socket\n");
stat = socket_listen(sock, Server, AF_INET, "127.0.0.1", 5000);
if(stat<0)
 printf("error in listening\n");
socket_close(sock);
return 0;
}

```gcc usage: **gcc -o stest stest.c -I/usr/local/include -L/usr/local/lib -lOpenSocket**

---

### Post by DangerOnTheRanger on 2010-12-28
Uhhhh, exactly *how *does it fail?

---

### Post by dwhitney67 on 2010-12-28
This is not wise:
```

typedef int hSOCK;

```
It makes the code a bit confusing.  If you want my $0.02, encapsulate as much relevant information about the socket into a structure.  You will need this information depending on the operation you are performing.

Consider
```

typedef struct
{
   int domain;
   int type;
   int protocol;

   int sd;       /* socket descriptor */
} Socket;

```

Objects of type Socket should be passed to your functions as necessary; for example:
```

int     socket_open(Socket* sock);
int     socket_listen(Socket* sock, const char* address, const unsigned short port, const int backlog);
Socket* socket_accept(Socket* sock, char** address, unsigned short* port);
...

```


P.S.
An example:
```

Socket listenSocket = { AF_INET, SOCK_STREAM, 0 };

if (socket_open(&listenSocket) != 0)
{
   /* fail */
}

if (socket_listen(&listenSocket, 0, 12345, 5) != 0)
{
   /* fail */
}

char*          clientAddr = 0;
unsigned short clientPort = 0;

Socket* clientSocket = socket_accept(&listenSocket, &clientAddr, &clientPort);

if (clientSocket)
{
   /* handle client */
}

```

---

