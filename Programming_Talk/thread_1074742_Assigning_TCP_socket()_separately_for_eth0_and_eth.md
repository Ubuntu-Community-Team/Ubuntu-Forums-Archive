---
title: "Assigning TCP socket() separately for eth0 and eth1 using c/c++"
date: 2009-02-19
forum: Programming Talk
---

### Post by akvseiji on 2009-02-19
I have **two NC** (Network Card): **eth0 and eth1** on same machine (PC).
Both have **different IP** address.

What I'm trying to do is to program eth0 as tcpserver and program eth1 as tcpclient using C programming. *//is it posible?* :o

Before this, I have only one NC (eth0), and I program it to be tcpserver and I run it using Terminal command line. When my tcpclient program connect to this tcpserver (run using IDE (Integrated Development Environment)), it work successfully.

**My question** is how to assign **eth0 as tcpserver**, and **eth1 as tcpclient** simultaneously? So that external PC can connect to my tcpserver, and my tcpclient can connect to external PC.

Example on my tcpserver program using only one NC:
my eth0 IP: 192.15.2.40
and I using port 2000.
```
sockfd = socket(AF_INET, SOCK_STREAM, 0);

serv_addr.sin_family = AF_INET;
serv_addr.sin_addr.s_addr = INADDR_ANY;
serv_addr.sin_port = htons(2000);

bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
listen(sockfd, 3);
accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);
```

Example on my tcpclient program:
```
sockfd = socket(AF_INET, SOCK_STREAM, 0);

serv_addr.sin_family = AF_INET;
serv_addr.sin_port = htons(2000);
serv_addr.sin_addr.s_addr = inet_addr("192.15.2.40");

connect(sockfd, (struct sockaddr *)&serv_addr, sizeof(serv_addr));
```

---

### Post by johnl on 2009-02-19
You will need to change:

```

serv_addr.sin_addr.s_addr = INADDR_ANY;

```

To listen only the IP address associated with the network card you want to listen on.   INADDR_ANY, appropriately, listens on all interfaces.

---

### Post by akvseiji on 2009-02-20
Hi johnl...
Thanx for the idea..

I change:
```

serv_addr.sin_addr.s_addr = INADDR_ANY;

```

to:
```

serv_addr.sin_addr.s_addr = "192.15.2.40";
//eth0 IP.

```

in tcpserver. It works!!! so far... :D

By doing that, only eth0 IP will be bind in socket.

---

### Post by dwhitney67 on 2009-02-20
> **akvseiji said:**
> Hi johnl...
Thanx for the idea..

I change:
```

serv_addr.sin_addr.s_addr = INADDR_ANY;

```

to:
```

serv_addr.sin_addr.s_addr = "192.15.2.40";
//eth0 IP.

```

in tcpserver. It works!!! so far... :D

By doing that, only eth0 IP will be bind in socket.

I'm surprised that works.  The struct member 's_addr' is declared as an 32-bit unsigned int in /usr/include/netinet/in.h:
```

typedef uint32_t in_addr_t;
struct in_addr
  {
    in_addr_t s_addr;
  };

...

struct sockaddr_in
  {
    __SOCKADDR_COMMON (sin_);
    in_port_t sin_port;                 /* Port number.  */
    struct in_addr sin_addr;            /* Internet address.  */

    ...
  };


```

I may be wrong, but I believe the proper way to setup s_addr is:
```

  sockaddr_in addr;
  hostent*    host = gethostbyname("192.15.2.40");

  if (host == 0)
  {
    // error
  }
  else
  {
    memset(&addr, 0, sizeof(addr));

    addr.sin_family      = m_AF_INET;
    addr.sin_addr.s_addr = *((unsigned long *) host->h_addr_list[0]);
    addr.sin_port        = htons(2000);
  }

```

P.S.  It appears that gethostbyname() is an obsoleted function; apparently either getaddrinfo() or getnameinfo() should be used instead.  I will need to look further into this.

---

### Post by akvseiji on 2009-02-22
Opps... seems like I make a little mistake.. I forgot to write inet_addr(). Due to excitement. :popcorn:

What I means is to do like this:
```
serv_addr.sin_addr.s_addr = inet_addr("192.15.2.40");
// eth0 IP

```

*To dwhitney67:*
Is it ok??

---

### Post by dwhitney67 on 2009-02-23
> **akvseiji said:**
> Opps... seems like I make a little mistake.. I forgot to write inet_addr(). Due to excitement. :popcorn:

What I means is to do like this:
```
serv_addr.sin_addr.s_addr = inet_addr("192.15.2.40");
// eth0 IP

```

*To dwhitney67:*
Is it ok??

yes.

---

### Post by akvseiji on 2009-02-23
How do I know which NC my tcpclient connect to?? (eth0 or eth1?)

I write my tcpserver and tcpclient in same program. At first I run tcpserver at other PC (IP = 192.15.2.50). 
My tcpclient successfully connect with that server, but an error occur when initialize my tcpserver. :
*Transport endpoint is already connected*
error happen at bind();

Perhaps I show you my program:
```

int main()
{
    int n, sockfd, sersockfd, clisockfd;
    int buflen = 256;
    char buffer[buflen];

    bzero(buffer, buflen);

    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd == -1)
        error("\nERROR socket!!\n");

    tcpcliInit(sockfd);
    tcpserInit(sockfd);

    //read...
    //write...

    return 0;
}

int tcpcliInit(int sockfd)
{
    int cliPortno, clisockfd;
    char cliIPaddr[15] = "192.15.2.50";
    char cliPort[4] = "2020";
    struct sockaddr_in cli_addr;

    cliPortno = atoi(cliPort);
    bzero((char *) &cli_addr, sizeof(cli_addr));

    cli_addr.sin_family = AF_INET;
    cli_addr.sin_port = htons(cliPortno);
    cli_addr.sin_addr.s_addr = inet_addr(cliIPaddr);

    clisockfd = connect(sockfd, (struct sockaddr *)&cli_addr, sizeof(cli_addr));
    if (clisockfd != 0)
        error("\nClient: ERROR Connect!!\n");

    return clisockfd;
}

int tcpserInit(int sockfd)
{
     int sersockfd, serPortno, sern, addrlen;
     char serIPaddr[15] = "192.15.2.40";
     char serPort[4] = "2030";
     struct sockaddr_in serv_addr, addr;

     bzero((char *) &serv_addr, sizeof(serv_addr));
     serPortno = atoi(serPort);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = inet_addr(serIPaddr);
     serv_addr.sin_port = htons(serportno);

     sern = bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
     if (sern != 0)
        error("\nServer: ERROR Bind!!\n");

     sern = listen(sockfd, 5);
     if (sern != 0)
         error("\nServer: ERROR Listen!!\n");

     addrlen = sizeof(addr);

     sersockfd = accept(sockfd, (struct sockaddr *) &addr, &addrlen);
     if (sersockfd == -1)
         error("\nServer: ERROR Accept!!\n");

     return sersockfd;
}

```

---

### Post by dwhitney67 on 2009-02-23
akvseiji -

If you start up your server, then terminate it, and few moments later you wish to start it up again but cannot because of a bind() error, then I bet it is because you need to specify that the socket is reusable.

Insert the following code after you open your server socket; it does not matter if it is before or after the bind(), but obviously it must be after the call to socket():
```

...
const int optVal = 1;
const unsigned int optLen = sizeof(optVal);

if (setsockopt(sockfd, SOL_SOCKET, SO_REUSEADDR, (void*) &optVal, optLen) < 0)
{
  // error
}
...

```

Concerning your code, it would appear that your client is attempting to connect to a port that differs from the one used by your server (2020 vs. 2030).

Concerning bzero(), I've seen it used long, long ago, in a galaxy far, far away.  It has been deprecated for as long as I can remember.  You should consider using memset() instead.  From the bzero() manpage:
```

CONFORMING TO
       4.3BSD.  This function is deprecated (marked as LEGACY in POSIX.1-2001):  use  mem-
       set(3) in new programs.

```

---

### Post by akvseiji on 2009-02-23
Let me make it more clear...

[IMG]http://img519.imageshack.us/img519/8027/screenshot1.png[/IMG]

I want to send some data from PC3 to PC2 to PC1 (**same data**) using TCP/IP. 
Then PC1 send data to PC2 then PC2 send data to PC3 (receive same data).

**Let say..** PC3 send "A" to PC2, then PC2 send that "A" to PC1,
then PC1 send back that "A" to PC2, then PC2 send back that "A" to PC3.

In **PC1**, tcpserver running **successfully**. In **PC3**, tcpclient running **successfully**. 
But I having **problem in PC2**. 

**How can I run tcpserver and tcpclient on the same time in one program?**

I've tried to run both tcpserver and tcpclient at the same time in one program, 
but an error occur. Seems like only one tcp (server or client) can running at one time.

If I run tcpserver first, it run successfully, but when initialize tcpclient, 
it give error: *Transport endpoint is already connected*.

If I run tcpclient first, it run successfully, but when initialize tcpserver, 
it give error at **bind()**: *Socket already in use*.

**I can run** tcpserver and tcpclient in PC2 successfully if I separate them in two programs.
But the question is.. 

**How can I pass arguments from tcpserver to tcpclient in two separate programs?**

any ideas???

---

### Post by dwhitney67 on 2009-02-24
Your client and your server should be using a different socket descriptor, as returned from the socket() call, not the same as shown previously in your example.

As far as merging the client and the server functionality into one application, it is doable.  Just use fork()... the parent process remains as the server (which you always want to start first), the child process will be the client.

From the diagram you presented, the client on PC2 will need to connect to two servers... one on PC1 and the other on PC2.  When it receives messages from PC2, forward these to PC1, and vice versa.  I recommend that you use select() to determine which server is communicating with the client at any given time.

P.S.  I just posted some code on another thread less than a day ago where someone was having issues with their TCP client application.  Look it up; there's some code that can help you get started quickly.

---

### Post by akvseiji on 2009-02-24
Hi **dwhitney67**,

Thank you, thank you, thank you very much for your help..
I just use different socket descriptor and it work perfectly.
Hahaha... thanx again.. :KS


Now to make it more better..
how can server know the IP address of client that connected to it??
without client send it's IP manually.

---

### Post by dwhitney67 on 2009-02-25
> **akvseiji said:**
> Hi **dwhitney67**,

Thank you, thank you, thank you very much for your help..
I just use different socket descriptor and it work perfectly.
Hahaha... thanx again.. :KS

You're welcome!

> **akvseiji said:**
> 
Now to make it more better..
how can server know the IP address of client that connected to it??
without client send it's IP manually.
You lost me on this question... the server undoubtedly knows its IP address (or is using "localhost") and its port number; it is the client that needs to be made aware of these values.

Once the client connects to the server, using the server hostname and port number, then the server should be aware of this connection.  The socket descriptor (id) that is returned by the accept() call should be used by the server to communicate with the client.  (communicate = receive/send messages).

If for whatever reason your server needs to know the IP address and port of the client (for record keeping, or whatever), then getpeername() may be used.  Here is example usage of this library function:
```

struct sockaddr_in addr;
socklen_t          addrLen = sizeof(addr);

if (getpeername(client_sd, (struct sockaddr*) &addr, &addrLen) < 0)
{
  // error
}

const char*    address = inet_ntoa(addr.sin_addr);
unsigned short port    = ntohs(addr.sin_port);

```

---

### Post by akvseiji on 2009-02-26
> **dwhitney67 said:**
> 

If for whatever reason your server needs to know the IP address and port of the client (for record keeping, or whatever)
this is exactly what I mean..


> **dwhitney67 said:**
> ```

struct sockaddr_in addr;
socklen_t          addrLen = sizeof(addr);

if (getpeername(client_sd, (struct sockaddr*) &addr, &addrLen) < 0)
{
  // error
}

const char*    address = inet_ntoa(addr.sin_addr);
unsigned short port    = ntohs(addr.sin_port);

```
I have a warning with this code: 
*warning: initialisation makes pointer from integer without a cast*
at **const char*    address = inet_ntoa(addr.sin_addr);**
that leads to *Segmentation fault* while running.

I found another example for getpeername:
```
struct sockaddr_in peer;
   int peer_len;

   peer_len = sizeof(peer);

   if (getpeername(sockfd, &peer, &peer_len) == -1)
   {   //error   }

   printf("Peer's IP address is: %s\n", inet_ntoa(peer.sin_addr));
   printf("Peer's port is: %d\n", (int) ntohs(peer.sin_port));

```this code works, no problem on IP but port number is different from what I declared.

This is what I declare.
**char cliPort[4] = "2020";**

This is what I get from getpeername example.
**Peer's port is: 52117**

and that value change every time I rerun the program.

---

### Post by dwhitney67 on 2009-02-26
The example I provided and the one you provided are identical, except for the variable names and the cast I used for the struct sockaddr_in variable.  I've used the code the way I presented (in a C++ app), and never had troubles.

Concerning your other question, once again I must reiterate that a simple client does not use a port number for its own needs.  Typically a client should only be supplied the address and the port number _of the server_.

Thus for your client code, you should _not_ need a declaration such as
```

char cliPort[4] = "2020";

```
(Btw, the array is declared too small!!!  Should be 5, not 4.  I'm not even sure why you declared it as a string, but whatever.)

The only time a client needs its own port is when it will act as a client/server (i.e. support two roles).

The port number 52117 (or other value) that is available for communicating between your client and the server, is determine by the system when the client connects to the server.  The port is created when the server successfully accepts() the client connection.

In theory, while your server and client are communicating, your server should also continue listening for other connections on its primary socket port.  If another client connects, it will be assigned a unique port number that differs from the one the server uses and from the one the first client is using.

I hope all this makes sense.

------------------------------------

Edit:

I had to satisfy my curiosity, so I created a test program again to verify the use of getpeername().  Here it is:
```

#include "TCPSocket.h"
#include <arpa/inet.h>
#include <stdio.h>


int main(int argc, char** argv)
{
  int sd = CreateSocket();

  Bind(sd, "127.0.0.1", 50000);
  Listen(sd, 5);
  ReuseSocket(sd, 1);

  int client_sd = Accept(sd);

  if (client_sd > 0)
  {
    struct sockaddr_in addr;
    socklen_t          addrLen = sizeof(addr);

    getpeername(client_sd, (struct sockaddr*) &addr, &addrLen);

    const char*          clientAddr = inet_ntoa(addr.sin_addr);
    const unsigned short clientPort = ntohs(addr.sin_port);

    printf("clientAddr = %s\n", clientAddr);
    printf("clientPort = %u\n", clientPort);

    // ...

    CloseSocket(client_sd);
  }

  return 0;
}

```
It ran like a charm (i.e. no segfaults).

---

### Post by manjappa on 2010-01-13
Assigning TCP socket() separately for eth0 and eth1 .... if u have code plz send to [email]manjappahb@yahoo.co.in[/email]

---

### Post by dwhitney67 on 2010-01-13
> **manjappa said:**
> Assigning TCP socket() separately for eth0 and eth1 .... if u have code plz send to [email]manjappahb@yahoo.co.in[/email]

Sorry, but I doubt anyone will do your work for you.

If you have two sockets, and two Ethernet interfaces (NICs), use bind() to assign the sockets to each interface.  Typically, in a configuration as you describe, the NICs will be assigned a static IP address.

The other "half" of the bind() requires that you specify a port number.  Either guess & choose two unique port numbers that are unused, or use a library call (I can't recall which) to search for an ephemeral port (ie. the next available one).

P.S.  This is as far as my answer will go unless I see a genuine effort on your part to put together some code.  Setting up a server is awfully trivial, and this thread or undoubtedly others like it that I have contributed to, offer lots of insights/code.

---

### Post by manjappa on 2010-01-15
i tryed a lot ..i getting binding error..
both the port in single board i have to run one in background....
server is waiting for client... but when i run the client it giving error ...

---

### Post by dwhitney67 on 2010-01-15
> **manjappa said:**
> i tryed a lot ..i getting binding error..
both the port in single board i have to run one in background....
server is waiting for client... but when i run the client it giving error ...

This is the most unhelpful reply.  What error(s) are you getting?

---

