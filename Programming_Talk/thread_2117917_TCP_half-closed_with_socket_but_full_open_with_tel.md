---
title: "TCP half-closed with socket but full open with telnet"
date: 2013-02-19
forum: Programming Talk
---

### Post by donalbane on 2013-02-19
I am using a C program to open a client socket to a server, send a query and read the response.  The write seems to work alright, but the read function just returns 0.  When I connect to the server with telnet and send the same query, there is an immediate response.  Does anyone have any idea why telnet would work but a read would not?  The socket is set as blocking.

Don

---

### Post by dwhitney67 on 2013-02-20
> **donalbane said:**
> Does anyone have any idea why telnet would work but a read would not?

Because telnet is a legacy application that has been tested thoroughly over many years (or should I say decades), whereas your application has not.

If you would post your code, I tell you where in fact the issue lies.  Otherwise you will need to deposit $0.25 into my crystal ball.

---

### Post by donalbane on 2013-02-20
The command the sequence that I follow with telnet is:
[1] telnet 192.168.128.100 1829
[2] type in the cmd string (AT+CREG?\n)
[3] see the response

The C code that I use to try the same thing is here:

```
    //create the socket
    sock = socket(AF_INET, SOCK_STREAM, 0);
    if(sock == -1)
    {
        printf("Unable to create socket: ");
        printf("%s\n",strerror(errno));
        exit(1);
    }
    else
        printf("Socket created.\n");

    //set socket to non-blocking
    flags = fcntl (sock, F_GETFL, 0);
    if(fcntl(sock, F_SETFL, flags | O_NONBLOCK)<0)
    {
        printf("Unable to set socket to non-blocking: ");
        printf("%s\n",strerror(errno));
        exit(2);
    }
    else
        printf("Socket set to non-blocking.\n");

    //define the server
    server.sin_addr.s_addr = inet_addr("192.168.128.100");
    server.sin_family = AF_INET;
    server.sin_port = htons(1829);

    //attempt to connect to server
    connect(sock, (struct sockaddr *)&server, sizeof(server));

    //check for established connection
    FD_ZERO(&wfds);
    FD_SET(sock, &wfds);
    tv.tv_sec = CONNECT_TIMEOUT_SEC;
    tv.tv_usec = 0;

    retval = select(sock+1 , NULL, &wfds, NULL, &tv);
    if(retval < 0)
    {
        printf("Unable connect to server: ");
        printf("%s\n",strerror(errno));
        exit(3);
    }
    else if(retval == 0)
    {
        printf("Timeout attempting to connect to server. Exiting.\n");
        exit(3);
    }
    else
        printf("Connection established.\n");
    FD_CLR(sock,&wfds);

    //set socket back to blocking
    flags = fcntl (sock, F_GETFL, 0);
    if(fcntl(sock, F_SETFL, flags & ~O_NONBLOCK)<0)
    {
        printf("Unable to set socket to blocking: ");
        printf("%s\n",strerror(errno));
        exit(4);
    }
    flags = fcntl (sock, F_GETFL, 0);
    if(!(flags & O_NONBLOCK))
        printf("Socket set back to blocking.\n");
 
    //send the query
    if(!ModemWrite(sock,cmd))
    {
        printf("Unable to send query to BGAN terminal: ");
        printf("%s\n",strerror(errno));
        exit(5);
    
    }
    else
        printf("Sent query.\n");

    //start timer for registration status query
    if(gettimeofday(&StartTime, NULL))
    {
        printf("Unable to start connect() timer: ");
        printf("%s\n",strerror(errno));
        exit(3);
    }
    if(gettimeofday(&CurrentTime,NULL))
    {
        printf("Unable to update connect() timer: ");
        printf("%s\n",strerror(errno));
        exit(3);
    }
    //look for response
    while((CurrentTime.tv_sec - StartTime.tv_sec) < MAX_RESPONSE_TIME)
    {
        //see if there is anything to read
        ioctl(sock,FIONREAD,&len);
        if(len > 0)//read the response
        {
            [...]//actually read what is there
        }
        if(gettimeofday(&CurrentTime, NULL))
        {
            printf("Unable to update reg status query timer: ");
            printf("%s\n",strerror(errno));
            exit(3);
        }
    }
[...]
```ModemWrite() basically just a wrapper for write() that uses select() to be able to timeout of a write to a blocking socket.  I've output the return of the write to verify that the expected number of writes IS going out.

len in ioctl() is just 0.  I've also just tried read and recv, but these just return 0 too.

---

### Post by dwhitney67 on 2013-02-20
I'm not sure why you are checking the connection in such a complicated manner:
```

...
    //attempt to connect to server
    connect(sock, (struct sockaddr *)&server, sizeof(server));

    //check for established connection
    FD_ZERO(&wfds);
    FD_SET(sock, &wfds);
    tv.tv_sec = CONNECT_TIMEOUT_SEC;
    tv.tv_usec = 0;

    retval = select(sock+1 , NULL, &wfds, NULL, &tv);
    if(retval < 0)
    {
        printf("Unable connect to server: ");
        printf("%s\n",strerror(errno));
        exit(3);
    }
    else if(retval == 0)
    {
        printf("Timeout attempting to connect to server. Exiting.\n");
        exit(3);
    }
    else
        printf("Connection established.\n");
    FD_CLR(sock,&wfds);
...

```

How about just doing something like this:
```

    //attempt to connect to server
    if (connect(sock, (struct sockaddr *)&server, sizeof(server)) != 0)
    {
        printf("Failure to connect to server.  Reason: %s [%d]\n",
               strerror(errno), errno);
        exit(3);
    }

```

There's also no need to play with the setting of the socket if you require it to be blocking; that is enabled by default.

Also, try using recv() to read from the socket.  I'm not sure what the behavior is of using the ioctl() call.

---

### Post by donalbane on 2013-02-20
> I'm not sure why you are checking the connection in such a complicated manner:

The application is running on an embedded system with a watchdog timer, so I don't want the connect() call to block (since that could result in the board rebooting).  Since the connect() call is non-blocking (because the socket is non-blocking at that point), I need a way to tell that the socket is actually ready for writing other than just checking the connect() return.

> Also, try using recv() to read from the socket.  I'm not sure what the behavior is of using the ioctl() call. 

Similarly, if I just use recv() it blocks and the program hangs because the socket is blocking (at that point in the code).  So, I use ioctl() see if there is anything in the socket to read.  I can also use select() to check if the socket is ready to read, but it just returns 0, which just means that the check for read readiness timed-out before there was anything to read.

Don

---

### Post by dwhitney67 on 2013-02-20
> **donalbane said:**
> The application is running on an embedded system with a watchdog timer, so I don't want the connect() call to block (since that could result in the board rebooting).  Since the connect() call is non-blocking (because the socket is non-blocking at that point), I need a way to tell that the socket is actually ready for writing other than just checking the connect() return.



Similarly, if I just use recv() it blocks and the program hangs because the socket is blocking (at that point in the code).  So, I use ioctl() see if there is anything in the socket to read.  I can also use select() to check if the socket is ready to read, but it just returns 0, which just means that the check for read readiness timed-out before there was anything to read.

Don
You are supplying system restrictions as this thread progresses.  It would have been helpful if you gave these upfront; otherwise one would think you are developing a trivial application on an Ubuntu desktop system.

You can prevent connect() from blocking your application for an extended period of time if you configure the send timeout period of the socket.  For example:
```

struct timeval timeout = { secs, usecs };

if (setsockopt(sock, SOL_SOCKET, SO_SNDTIMEO, (const void*) &timeout, sizeof(timeout)) < 0)
{
    // error
}

if (connect(...) != 0)
{
    // error
}

...

```
where 'secs' is the number of seconds, and 'usecs' represents microseconds.

As for recv(), it does indeed block.  You can either refrain from calling recv() until select() indicates that there is data to be received, or alternatively you can set the receive timeout period (similar to the code above) using the SO_RCVTIMEO flag.

---

### Post by donalbane on 2013-02-20
> You are supplying system restrictions as this thread progresses.  It  would have been helpful if you gave these upfront; otherwise one would  think you are developing a trivial application on an Ubuntu desktop  system.

My apologies.  I never know how much information to post upfront, since much of it may be irrelevant, and the huge information dump may cause readers' eyes to glaze over.

> As for recv(), it does indeed block.  You can either refrain from  calling recv() until select() indicates that there is data to be  received, or alternatively you can set the receive timeout period  (similar to the code above) using the SO_RCVTIMEO flag.   

Now we get back to the issue.  I have tried setting a receive timeout (10 seconds) with setsockopt() and recv() returns with -1, with corresponding strerror(errno) = "Resource temporarily unavailable". I've also tried just using select(), without setting the receive timeout through setsockopt(), and the select() always just returns 0 (i.e. it times out).  I'm wondering why this would be the case, when telnet gets a response almost right away.

---

### Post by dwhitney67 on 2013-02-20
> **donalbane said:**
> I'm wondering why this would be the case, when telnet gets a response almost right away.

Perhaps you are not correctly encoding the command that you issue to the device?

Btw, could you try this code out (naturally, the command string will need to be changed)...
```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <time.h>
#include <errno.h>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

static const char*          MODEM_IP = "192.168.128.100";
static const unsigned short PORT     = 1829;

int  sock_create();

void sock_setTimeout(int sock, const int attrib, const int secs, const int usecs);

void sock_connect(int socket, const char* address, const unsigned short port);

void sock_send(int sock, const unsigned char* data, const size_t dataLen);

int  sock_recv(int sock, unsigned char* buf, const size_t bufSize);


int main()
{
    unsigned char response[1024];

    int sock = sock_create();

    sock_setTimeout(sock, SO_SNDTIMEO, 2, 0);
    sock_setTimeout(sock, SO_RCVTIMEO, 2, 0);

    sock_connect(sock, MODEM_IP, PORT);

    unsigned char cmd[] = "[foo%%%#!@#$]";
    size_t cmd_length = sizeof(cmd) / sizeof(unsigned char);

    sock_send(sock, cmd, cmd_length);

    int bytesRcvd = sock_recv(sock, response, sizeof(response));

    printf("Received %d bytes of data.\n", bytesRcvd);

    //...

    return 0;
}


int sock_create()
{
    int sock = -1;

    if ((sock = socket(AF_INET, SOCK_STREAM, 0)) < 0)
    {
        fprintf(stderr, "Unable to create socket; reason: %s [%d]\n", strerror(errno), errno);
        exit(1);
    }

    return sock;
}

void sock_setTimeout(int sock, const int attrib, const int secs, const int usecs)
{
    struct timeval timeout = { secs, usecs };

    if (setsockopt(sock, SOL_SOCKET, attrib, (const void*) &timeout, sizeof(timeout)) < 0)
    {
        // error
    }
}

void sock_connect(int socket, const char* address, const unsigned short port)
{
    struct sockaddr_in sin;

    memset(&sin, 0, sizeof(sin));

    sin.sin_addr.s_addr = inet_addr(address);
    sin.sin_family      = AF_INET;
    sin.sin_port        = htons(port);

    if (connect(socket, (struct sockaddr*) &sin, sizeof(sin)) != 0)
    {
        fprintf(stderr, "Unable to connect; reason: %s [%d]\n", strerror(errno), errno);
        exit(1);
    }
}

void sock_send(int sock, const unsigned char* data, const size_t dataLen)
{
    int bytesSent = 0;

    while (bytesSent < dataLen)
    {
        int result = send(sock, data + bytesSent, dataLen - bytesSent, 0);

        if (result > 0)
        {
            bytesSent += result;
        }
        else if (result == 0)
        {
            // do nothing; try again
        }
        else
        {
            fprintf(stderr, "Unable to send data; reason: %s [%d]\n", strerror(errno), errno);
            exit(1);
        }
    }
}

int sock_recv(int sock, unsigned char* buf, const size_t bufSize)
{
    int result = recv(sock, buf, bufSize, 0);

    if (result == -1)
    {
        if (errno == EAGAIN || errno == EINTR)
        {
            result = 0;
        }
        else
        {
            fprintf(stderr, "Error while receiving; reason: %s [%d]\n", strerror(errno), errno);
        }
    }

    return result;
}

```

P.S.  Code above was compiled using GCC with -std=c99 option.

---

### Post by donalbane on 2013-02-20
> Perhaps you are not correctly encoding the command that you issue to the device?


I was thinking something similar, like perhaps telnet sends additional messages upon first connecting and after sending each message that are not immediately obvious.  I tried to run tcpdump to compare the difference between when telnet runs and when my socket client runs, but it isn't obvious to me which differences are significant (or real).

> Btw, could you try this code out (naturally, the command string will need to be changed)...

I ran your binary (although, I had to leave off the -std=c99 option, as it was wasn't understanding what struct timeval was with that), and it seems to experience the same issue.  The output was:

Received 0 bytes of data.

---

### Post by dwhitney67 on 2013-02-20
> **donalbane said:**
> 
I ran your binary (although, I had to leave off the -std=c99 option, as it was wasn't understanding what struct timeval was with that)...

Probably because I forgot to include <sys/time.h>

What's the protocol used by your device?  For example, can you please post the command string that you are using, or give a hint at what the documentation states.

---

### Post by donalbane on 2013-02-20
> Perhaps you are not correctly encoding the command that you issue to the device? 

That was it.

A co-worker suggested that I run **strace** on the telnet command and on my client application to see if I could determine what was happening differently.  I was able to see that telnet was inserting '\r' in before my '\n' in my command (AT+CREG?\n - a query for network registration status of a satellite phone terminal).  I put a '\r' in my command and both your application and mine work normally!

Whew.

Thank you so much for your patience and assistance!

Don

---

### Post by dwhitney67 on 2013-02-20
I'm glad you sorted out the issue.

Please don't forget to mark this thread as "solved". (Edit:  It looks like you already did.  :-) )

---

