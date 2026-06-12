---
title: "require ethernet as stdin stream"
date: 2007-04-19
forum: Programming Talk
---

### Post by Ne0z on 2007-04-19
Hi, 

I'm not sure whether am i asking the right thing but here it goes,
im running a program that requires data from the ethernet or a wireless device.
How can i set up a stream such that its the stdin for my program?



thanks ! 

regards

---

### Post by amo-ej1 on 2007-04-20
Well could you specify more exactly what you want to do because you question can be interpreted in many ways.  What kind of application are you referring to ? Do you want online data or offline data ? Can it handle streams or can the application also handle devices ? What data format does it require ?

---

### Post by Ne0z on 2007-04-20
hi, 

sorry if i was a bit ambiguous. I haven't done this before so i'm not sure how should i ask. 

the program i have currently just receives data from a USB connection. 
data that it receives are just single characters. 

and now this single characters would be transmitted from a wireless device instead of USB. 
So i guess i first have to connect to a server through my own wireless device (using sockets ?)
through a TCP/IP connection. Then wait for data to be sent by the server. 

I'm not sure how should i initiated whatever i receive from the server as the stdin to my program. 



thanks ! :)

---

### Post by amo-ej1 on 2007-04-20
Well to be honest you are still ambiguous. How do you define a wireless link ? wlan ? irda ? bluetooth ? Hell it can even be DVB-T or DAB.

But suppose the wireless link is wlan, then you will probably get your characters over an IP link, so probably it will be a UDP or TCP stream, if this is still the case you could make use of netcat to listen to a port on an interface and to transform the characters to a simple text stream 
If this isn't the case then details would be nice ;)

---

### Post by Ne0z on 2007-04-20
really sorry for the confusion amo-ej1 !!

yes its wlan and it would be a tcp stream.

but i need to open up this stream in C code for my program. Does this mean sockets ?

---

### Post by russell.h on 2007-04-20
As far as I know, yes, it means sockets. But you might look into using a library to abstract a lot of that stuff, I tried it once and it is a **pain.**

---

### Post by jeremyh on 2007-04-20
If you are wanting to communicate over a network (either internal or over the internet) then yes you would use sockets.

If you are wanting to capture data going across a network then it's a little more complicated. You can look at the tcpdump utility and more importantly the libpcap library ( [http://www.tcpdump.org/](http://www.tcpdump.org/) ).

Hope that helps,
Jeremy

---

### Post by amo-ej1 on 2007-04-21
Ah okay in that case it' really easy ;). So since it's a TCP stream you would (in this order) require the following calls:

a) open the socket:
- man 7 socket
- typically int fd =  socket(PF_INET, SOCK_STREAM, 0); will give you a file descriptor 

b) bind on the given port
- man 2 bind, here you specify the socket settings, the port to listen on etc etc

c) listen for incommning connections
- man 2 listen  listen(fd,0);

d) accept incoming connections:
- man 2 accept; accept incoming connections and return a filedescriptor that can be used

e) read() and write() from the given filedescriptor

f) close when finished

---

### Post by amo-ej1 on 2007-04-21
Here is a sample implementation of a c application which handles a TCP connection:

Basicly it llistens on all interfaces on port 6667, when somebody connects to it, it reads all the data until end of stream occurs. All the data get echo'ed to standard out and when the connection terminates the application also ends.

```

//
// TCP connection example, handles
// one connection.
//
// by Elie De Brauwer - 20070421
// 


#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

#define PORT 6667
#define BUFSIZE 100

int main(int argc, char **argv)
{

    //
    //  Open socket
    //
    int sock = socket(PF_INET,SOCK_STREAM,0);
    if(sock == -1)
    {
        printf("%m\n");
        exit(1);
    }

    //
    // Bind to port ander interface
    //
    struct sockaddr_in sa;
    sa.sin_family = AF_INET;
    sa.sin_port = htons(PORT);
    sa.sin_addr.s_addr=htons(INADDR_ANY);
    int res = bind(sock, (struct sockaddr *) &sa, sizeof(sa));
    if(res != 0)
    {
        printf("%m\n");
        close(sock);
        exit(1);
    }

    //
    // Start listening
    //
    res = listen(sock,0);
    if(res != 0)
    {
        printf("%m\n");
        close(sock);
        exit(1);
    }

    //
    // Accept incoming connection (TCP only)
    // 
    struct sockaddr_in clientSa;
    int size=sizeof(clientSa);
    int clientSock = accept(sock,(struct sockaddr *) &clientSa, &size);
    if(clientSock == -1)
    {
        printf("%m\n");
        close(sock);
        exit(1);
    }

    //
    // Connection established
    //
    printf("Incoming connection from %s port %d\n", inet_ntoa(clientSa.sin_addr) , ntohs(clientSa.sin_port)); 

    //
    // Read the data
    //
    char data[BUFSIZE];
    res = read(clientSock,data,BUFSIZE-1);
    while(res > 0)
    {
        data[res]=0;
        printf("%s\n",data);
        res = read(clientSock,data,BUFSIZE-1);
    }

    // Close the socket
    close(clientSock);
    close(sock);

}


```

---

### Post by amo-ej1 on 2007-04-21
Oh yeah, i already meantion netcat earlier, well if you don't like to play around with sockets (sockets are really easy to work with, they're just simple filedescriptors which need some extra calls to set them up properly). netcat is an application which already provides this functionality. So you could for example do the following :

```

root@rogue:/home/edb# netcat -l -p 6667

```

This will do the same as the application posted above, if will listen for tcp connections on port 6667 and dump whatever comes in to stdout. (to try telnet localhost 6667) and than you can simply pipe the output from netcat to your applicaiton and read it from there. Surely one wouldn't want to do this in a production environment but it is very suitable as a 'quick 'n dirty' hack ;)

---

### Post by cwaldbieser on 2007-04-22
> **amo-ej1 said:**
> Oh yeah, i already meantion netcat earlier, well if you don't like to play around with sockets (sockets are really easy to work with, they're just simple filedescriptors which need some extra calls to set them up properly). netcat is an application which already provides this functionality. So you could for example do the following :

```

root@rogue:/home/edb# netcat -l -p 6667

```

This will do the same as the application posted above, if will listen for tcp connections on port 6667 and dump whatever comes in to stdout. (to try telnet localhost 6667) and than you can simply pipe the output from netcat to your applicaiton and read it from there. Surely one wouldn't want to do this in a production environment but it is very suitable as a 'quick 'n dirty' hack ;)

Could you elaborate a little bit on why this would not be a good idea in a production environment?  I am curious what kind of problems there would be.

---

