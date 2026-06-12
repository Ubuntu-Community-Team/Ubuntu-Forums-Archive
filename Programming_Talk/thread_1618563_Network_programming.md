---
title: "Network programming"
date: 2010-11-10
forum: Programming Talk
---

### Post by jtmurphree on 2010-11-10
I need to create a server program that listens for a connection on a multicast address of 234.5.6.7. I am having trouble doing this. I have set up the server to listen on this address with th following code
```

/* build address data structure */
    bzero((char *)&servin, sizeof(servin));
    servin.sin_family = AF_INET;
    servin.sin_port = htons(SERVER_PORT);
    inet_aton("234.5.6.7", &servin.sin_addr);

```

Server will compile and run but I can't connect from the client.
I tried the following code
```

    inet_pton(AF_INET, "234.5.6.7", &ipv4addr);
    hp = gethostbyaddr(&ipv4addr, sizeof ipv4addr, AF_INET);

    if(!hp)
    {
        //display error message for unknown host and exit
        fprintf(stderr, "simplex-talk: unknown host: %s\n", host);
        exit(1);
    }

```

Can anyone let me know whats is wrong?

---

### Post by dwhitney67 on 2010-11-10
Not without seeing more of your code, specifically the server side.  But from what you have posted, I don't believe you have programmed the server correctly to setup a multicast socket.  It would appear as if you are attempting to set up a regular socket, not a multicast one.

P.S. The IP address you have chosen is in the correct range.

---

### Post by ziekfiguur on 2010-11-11
I don't really know about multicast, but shouldn't a server just bind to 0.0.0.0 and than be run on the machine with address 234.5.6.7?

---

### Post by The Cog on 2010-11-11
> **ziekfiguur said:**
> I don't really know about multicast, but shouldn't a server just bind to 0.0.0.0 and than be run on the machine with address 234.5.6.7?

No. You cannot assign a multicast address to a server. The application has to open a multicast socket explicitly, and join the multicast group. I think this must be a UDP socket, not TCP.

And as far as I know, you cannot "connect" to a multicast address using TCP, you have to use UDP datagrams and send to the multicast group.

---

### Post by dwhitney67 on 2010-11-11
> **The Cog said:**
> No. You cannot assign a multicast address to a server. The application has to open a multicast socket explicitly, and join the multicast group. I think this must be a UDP socket, not TCP.

And as far as I know, you cannot "connect" to a multicast address using TCP, you have to use UDP datagrams and send to the multicast group.
You are correct on all of the above.

Here's the gist on how to setup a server to use a UDP socket for multicasting (btw, the code is in C++):
```

...
  const unsigned short SERVER_PORT     = 12345;
  const char*          MULTICAST_GROUP = "225.0.0.35";

...

    UDPSocket sock;

    struct ip_mreq mreq;
    memset(&mreq, 0, sizeof(mreq));
    mreq.imr_multiaddr.s_addr = inet_addr(MULTICAST_GROUP);
    mreq.imr_interface.s_addr = htonl(INADDR_ANY);

    setsockopt(sock.getSocketDesc(), IPPROTO_IP, IP_ADD_MEMBERSHIP, &mreq, sizeof(mreq));

    /*
    int enable = 1;
    setsockopt(sock.getSocketDesc(), IPPROTO_IP, IP_MULTICAST_LOOP, &enable, sizeof(enable));

    int ttl = 0;
    setsockopt(sock.getSocketDesc(), IPPROTO_IP, IP_MULTICAST_TTL, &ttl, sizeof(ttl));
    */

    sock.enableReusePort();
    sock.bind(SERVER_PORT);

    ...

```

The client would do something like:
```

  const unsigned short SERVER_PORT     = 12345;
  const char*          MULTICAST_GROUP = "225.0.0.35";

...

    UDPSocket sock;
    string    msg;

    for (;;)
    {
      cout << "Enter a message to send, or press <RETURN> to exit:\n";
      getline(cin, msg);

      if (msg.size() == 0) break;

      cout << "Sending this message: " << msg << endl;
      sock.send(msg.c_str(), msg.size(), MULTICAST_GROUP, SERVER_PORT);
    }

```

Some additional information:
```

   The following is borrowed (w/o permission!) from:  Antony Courtney (antony@scrg.cs.tcd.ie)

   Notes about Multicasting:

   Multicast Addresses are restricted to the following ranges:

          224.0.0.0 to 239.255.255.255

   although some of these addresses are reserved for multicasting routing information.
   Applications should not use these reserved addresses, which are:

          224.0.0.0 to 224.0.0.255

   Time-to-Live (TTL) for Multicast Packets are by default restricted to the current
   subnet (TTL=1).  Below are the supported multicast TTL thresholds:

          0   restricted to the same host
          1   restricted to the same subnet (default)
         32   restricted to the same site
         64   restricted to the same region
        128   restricted to the same continent
        255   unrestricted

    The TTL can be changed using setsockopt().  For example:

        unsigned char ttl = 32;
        setsockopt(sock.GetSocketDesc(), IPPROTO_IP, IP_MULTICAST_TTL, &ttl, sizeof(ttl));

```

---

### Post by jtmurphree on 2010-11-11
ok thanks for your help. Just to make sure I am clear, you do not establish a connection with UDP right? Basically you just set up the socket, send something over it and hope it gets there.

---

### Post by dwhitney67 on 2010-11-11
That is correct.

---

### Post by jtmurphree on 2010-11-13
Thanks for your help. Going on the info you gave I was able to get something that worked. I only have one problem now. At this time I am running both the client and server program on my laptop and a lot of the time I am where I do not have internet connection. However, in order for the multicast to work I have to have my wifi card on and connected. I am guessing that this is because the server is listening on a certain interface as opposed to a socket defined in the code. I understand why the card has to be on but not why it has to be connected. Is there any way I can set it up so that I can run and test the software even though I don't have an actual connection?

---

### Post by dwhitney67 on 2010-11-13
Your server should be binding its port to INADDR_ANY.  That way the socket will be bound to both the network card (if any) AND to the local interface (lo) which is ALWAYS available.

To assist you a bit further:
```

struct sockaddr_in sin;

memset(&sin, 0, sizeof(sin));

sin.sin_family      = AF_INET;
sin.sin_addr.s_addr = htonl(INADDR_ANY);
sin.sin_port        = htons(port);

bind(socketdesc, (struct sockaddr*) &sin, sizeof(sin));

```

---

### Post by jtmurphree on 2010-11-13
I am doing that per the following code

```

/* build address data structure */
    bzero((char *)&servin, sizeof(servin));
    servin.sin_family = AF_INET;
    servin.sin_addr.s_addr = htonl(INADDR_ANY);
    servin.sin_port = htons(SERVER_PORT);
    
    

    /*setup passive open*/
    if((listener = socket(AF_INET, SOCK_DGRAM, 0)) < 0)
    {
        perror("simplex-talk: socket");
        exit(1);
    }

    if (bind(listener,(struct sockaddr *) &servin,sizeof(servin)) < 0) 
    {
          perror("bind");
          exit(1);
         }
    

    //set socket options and notify user if error occurs

    if (setsockopt(listener,SOL_SOCKET,SO_REUSEADDR,&true,sizeof(int)) == -1) {
            perror("Setsockopt");
            exit(1);
        }

     /* use setsockopt() to request that the kernel join a multicast group */
         mreq.imr_multiaddr.s_addr=inet_addr(GROUP);
    mreq.imr_interface.s_addr = INADDR_ANY;

         if (setsockopt(listener,IPPROTO_IP,IP_ADD_MEMBERSHIP,&mreq,sizeof(mreq)) < 0) 
    {
        perror("setsockopt");
          exit(1);
         }

```

However, the mreq in this code is an ip_mrez struct which, from what I read, is needed to listen for multicast traffic. I believe the problem I mentioned is due to the setting of the inerface addres for mreq.

---

### Post by dwhitney67 on 2010-11-13
It's been awhile since I have played around with multicasting, but something is telling me perhaps you _will_ have an issue if you do not have a network interface available.  For regular UDP sockets, having the local interface is sufficient, however IIRC, multicast is different.  I'm sorry to lead you to believe otherwise.

If you think about it, there's no point to multicast a message when you are on an isolated system.

---

