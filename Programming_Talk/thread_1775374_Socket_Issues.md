---
title: "Socket Issues"
date: 2011-06-04
forum: Programming Talk
---

### Post by djohnson3278 on 2011-06-04
Hello all,

I'm having a bit of an issue using UDP sockets...I'm not new to network programming, and I have a solution for this issue, but I'm wondering why it didn't work the way I intended.

It's a simple setup:

The server creates a UDP socket, then binds it to a local address and port (127.0.0.1:50543).  It then blocks in recvfrom, waiting for a packet.  The client, which simply creates a socket(), then does a hard-coded sendto(), whisks a packet off to the server.  The server recieves it and everything is fine so far.

When the server does recieve the packet, it uses the address it got from recvfrom.  I create another udp socket, and use connect() with the address to create a default destination. I then send() (not sendto()) a packet through this "connected" socket (it's just a default address), and it works perfectly.

The issue starts when the client sends another packet.  According to documentation, the connected socket is only allowed to communicate with that one peer, which implies it can recieve packets from that peer ( read [http://kerneltrap.org/node/7491](http://kerneltrap.org/node/7491) ).  However, there is also another socket in the server that can recieve that packet...the catchall 127.0.0.1:50432 bind()'d one.  Which socket recieves the packet...or do they both, or none since there's a conflict?

*EDIT*  Sometimes, I'll get the packet on the locally bound socket, and sometimes I'll get it on the connected socket.  It seems like it depends on the kernel's mood....

With much appreciation,
djohnson3278

---

### Post by dwhitney67 on 2011-06-04
Based on the setup you described, I threw together some code that emulates the applications you are testing.

However, I was not able to duplicate the anomaly that you describe, thus the only thing I can think of is that either 1) I did not understand the problem well enough, or 2) you have a bug in your application(s).

Below are my Server and Client apps; you will not be able to compile them, but let me know if I assumed something incorrectly.  Hopefully the comments and the gist of what these apps do is intuitively obvious.

Server.cpp:
```

#include <Socket/UDPSocket.hpp>
#include <iostream>
#include <cstring>

int main()
{
   using namespace socketpp;

   try
   {
      UDPSocket sock1;
      sock1.bind(9000);

      char           buffer[1024];
      std::string    sourceAddr;
      unsigned short sourcePort;

      // Initial receive from Client.
      int bytes = sock1.recv(buffer, sizeof(buffer) - 1, sourceAddr, sourcePort);
      buffer[bytes] = '\0';

      std::cout << "Received message from " << sourceAddr << ":" << sourcePort << std::endl;

      // Setup second socket, which is "connected" to the Client's address and port.
      UDPSocket sock2;
      sock2.connect(sourcePort, sourceAddr);

      for (int i = 0; true; ++i)
      {
         sock2.send(buffer, strlen(buffer));

         // Toggle receiving from second socket and the first socket.
         if (i % 2 == 0)
         {
            bytes = sock2.recv(buffer, sizeof(buffer), sourceAddr, sourcePort);
         }
         else
         {
            // When attempting to receive on socket 1, the application blocks
            // indefinetely because by now, the Client is only sending data to
            // the address and port from where it received data.
            bytes = sock1.recv(buffer, sizeof(buffer), sourceAddr, sourcePort);
         }
         buffer[bytes] = '\0';

         std::cout << "Received message from " << sourceAddr << ":" << sourcePort << std::endl;
      }
   }
   catch (SocketException& e)
   {
      std::cout << "Caught Exception: " << e.what() << std::endl;
      return -1;
   }
}

```

Client.cpp:
```

#include <Socket/UDPSocket.hpp>
#include <iostream>
#include <cstring>
#include <unistd.h>

int main()
{
   using namespace socketpp;

   try
   {
      UDPSocket      sock1;
      char           buffer[1024];
      std::string    sourceAddr;
      unsigned short sourcePort;
      const char*    message = "Hello World";

      sock1.send(message, strlen(message), "localhost", 9000);

      while (true)
      {
         int bytes = sock1.recv(buffer, sizeof(buffer) - 1, sourceAddr, sourcePort);
         buffer[bytes] = '\0';

         std::cout << "Received message from " << sourceAddr << ":" << sourcePort << std::endl;

         sleep(2);
         sock1.send(buffer, strlen(buffer), sourceAddr, sourcePort);
      }
   }
   catch (SocketException& e)
   {
      std::cout << "Caught Exception: " << e.what() << std::endl;
      return -1;
   }
}

```

---

### Post by djohnson3278 on 2011-06-05
This is very strange....

So, the connected socket takes precedence because that socket is the one that sent the data...

Which would mean the other socket is bound to a different port entirely?

---

### Post by dwhitney67 on 2011-06-05
> **djohnson3278 said:**
> This is very strange....

So, the connected socket takes precedence because that socket is the one that sent the data...

Which would mean the other socket is bound to a different port entirely?

The server has two sockets; one that was explicitly bound to a port and address (or INADDR_ANY), the other which is configured to specifically communicate with a particular address and port (i.e. that of the client).

As for the client, it initially sends a message to the server's first socket using the defined address/port.  Now, does it continue to issue messages indefinitely to that same address/port, or does it start utilizing the address/port information it gets from messages that it receives (from the server's second socket)?

Since UDP is a connection-less protocol, thus when a message is received, any replies are generally sent straight back to the sender using the appropriate information obtained from the recvfrom() call.  This is not a steadfast rule; there's always the possibility that port-forwarding may take place.  But for simple server/client applications, one generally does not open up a second socket.  But there's nothing saying that you cannot (say you want to handle many clients in a multi-threaded application).

---

### Post by djohnson3278 on 2011-06-05
Exactly.

The client doesn't use any information, it literally only sends packets to one address, and that's the server's bound port.  I'm wondering if, on the server, the bound socket or the implicitly bound "connected" one recieves any other packets.  The client simply sends to the same port throughout the entire transaction.

*EDIT* I think I know why I'm confused.

You can't have two sockets with the same local address and port...so whywould there be a conflict? When I call connect(), I'm establishing a default peer address and port...but when I send() after that, could it be that the socket is actually being bound to a DIFFERENT port?  I'd test it but I'm using the loopback interface, which wireshark won't monitor since the destination is the same address.

I actually tried setting the first socket's options to allow reuse (SOL_REUSEADDR), and then bound the second socket to the same address as well.. There weren't any errors.  Then I get strange behavior, so I think I might just be thinking about this the wrong way.

---

### Post by djohnson3278 on 2011-06-06
*BUMP*

I need a solution to this :/  I can create code to replicate the problem all I want, but how do I solve it?

Details to add:

The server now has the two sockets bound to the same local address/port pair, through using SOL_REUSEADDR.  It's acting strange.  The whole deal for this experiment is that the server has two sockets that "match" the client's packet.  The catch-all one bound to port 50432, and now the connected one, also bound to 50432.  Which one receives it?

---

### Post by dwhitney67 on 2011-06-06
> **djohnson3278 said:**
> *BUMP*

I need a solution to this :/  I can create code to replicate the problem all I want, but how do I solve it?

Details to add:

The server now has the two sockets bound to the same local address/port pair, through using SOL_REUSEADDR.  It's acting strange.  The whole deal for this experiment is that the server has two sockets that "match" the client's packet.  The catch-all one bound to port 50432, and now the connected one, also bound to 50432.  Which one receives it?

Was is it that you are really trying to accomplish?

Say the Server wishes to receive UDP packets on port 50432.  The Server would then bind INADDR_ANY to port 50432, then blocks on a recvfrom(), awaiting a packet from the Client.

The Client sends a UDP packet to 127.0.0.1:50432.  The Server receives the packet.  Now what?

Are you stating that the Server opens a second socket and "connects" it to INADDR_ANY:50432 (or 127.0.0.1:50432)?  Or does the Server connect the new socket to the Client's IP address and port?  Note that when the client sends a packet to the Server, it will have a unique (ephemeral) port number.

In either case, what are trying to accomplish?  If the Client always sends to the same IP/port (the Server's original), then the Server had better receive on the socket that has been bound to receive from the IP/port pair.  Attempting to receive on the new socket will merely cause the Server to block.

P.S.  If the Server and Client run on the same system, they both utilize 127.0.0.1 for their respective IP addresses when sending.  If Server and Client are on distinct systems, then their IP addresses will be different.

---

### Post by djohnson3278 on 2011-06-07
It's the architecture I was going to implement in my network engine...it really is trivial.  I don't much care if the packet goes through, I'm just wondering WHAT socket receives it.  I think you are misunderstanding what I'm asking...

The server, at first, has ONE socket.  It is bound using bind() to 127.0.0.1:50432.  There is a client, it could be from the same address, any address, doesn't matter, but it just creates a socket(), then it uses sendto() to send a packet.  The kernel does an implicit bind to some port on the system, but that isn't important.

When the server gets the packet, it receives it on the original bound socket, obviously.  BUT THEN, I create a NEW socket, bind it to the same local address (which I'm able to do using SOL_REUSEADDR on both sockets) as the first, and then simply connect() that socket to the address I got in recvfrom, which would obviously be the client.

Now, at that point, if the client were to send another packet....what socket on the server would it go to?  They both match the criteria.  Both sockets point to 127.0.0.1:50432 *LOCALLY*, and both sockets can receive from that same client, because the connected one is "connected" to that address (meaning it's default peer is the client), and the other socket can receive from any address.

So what I'm asking is, WHAT socket obtains the packet?  I'm not concerned about anything else.  Just where the packet goes after the kernel drivers are done processing the packet.


*EDIT*

As a side note, this type of behavior I'm implementing mimics the behavior of TCP sockets, because I'm essentially doing the same thing.  Don't give me a lecture on the difference between TCP and UDP, I know the difference, and every time I say this I get lectured on UDP not being the same as TCP.  When you listen() on TCP, that is what the behavior of my first socket is implementing; it just listens for any packet on that port.  When you accept() in TCP, it creates a new socket, but that new socket has the SAME LOCAL ASSOCIATION.  That's exactly what I'm accomplishing...creating a new socket, binding it to the same local address.  But that new socket also gets a remote association, aka an implicit connect() to the address that contacted the first listen()ing socket (exactly what I do here).  The difference with TCP is that obviously, the kernel manages connection state and uses keep alives to make it persistent.  In UDP's case, it's a way to emulate the behavior of TCP without actually implementing all the fluff that goes on at the transport level.  I hope that clears things up a tad.

I know it might be useless, but I'm trying to answer this to satisfy my curiousity.

---

### Post by dwhitney67 on 2011-06-07
Thanks for the clarification.

Tell me, how were you able to bind the second socket to a particular address/port, if the first socket has already been bound to this same address/port?  AFAIK, this is not possible... well, at least not on my Ubuntu system.

In other words, this is not possible:
```

int socket1 = socket(...);
struct sockaddr_in sin;
...
int rtn = bind(socket1, (struct sockaddr*) &sin, sizeof(sin));

assert(rtn == 0);

...

int socket2 = socket(...);
rtn = bind(socket2, (struct sockaddr*) &sin, sizeof(sin));

assert(rtn == 0);  // the bind() will fail

connect(socket2, ...);

...

```
As indicated above, the second call to bind() will fail; even if you set the socket1 option to enable SO_REUSEADDR.


P.S.  It would be immensely helpful if you posted the code you are using.

P.S. #2  When you refer to SOL_REUSEADDR, did you mean SO_REUSEADDR?

---

