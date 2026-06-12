---
title: "Multicast Packets Looping Back in Java"
date: 2010-01-07
forum: Programming Talk
---

### Post by JCoster on 2010-01-07
I'm currently building a distributed server system and am having a problem with multicast DatagramPackets looping back to the local system.  

I basically have several servers which are to run this application and will periodically send a multicast message over the network informing the other servers that it is still online.  I have a listening thread running on each server which reacts whenever a packet is received on the MulticastSocket.

However, I am having a problem with each server receiving its own multicast messages.  I have set the multicast socket loopback mode to false but still have the issue.  It would not be an issue could I detect the LAN address of the machine as I could just set it to ignore any packets from its own address, yet calling [multicast]socket.getLocalAddress() it just returns 127.0.0.1, or 0.0.0.0.  

Any help is greatly appreciated.
Cheers,
JC

---

### Post by iharrold on 2010-01-07
I'm a little confused... socket.getLocalAddress() should return 127.0.0.1 (IPv4) and possibly 0.0.0.0 if that is how the system is configured (I believe /etc/hosts).   Or 0:0:0:0:0:0:0:1 in IPv6.

---

### Post by JCoster on 2010-01-07
Ok then, so how can I get the actual address on the network of the server?  I understand it's tricky to get as there may be more than one (i.e. if the machine has multiple NICs) but is there a way to return a set of InetAddresses?
Alternatively, how can I actually stop the multicast socket receiving it's own multicast messages?
Cheers for your quick reply,
JC

---

### Post by JCoster on 2010-01-07
Ok so I've fixed it.  It turns out that *[multicast]socket.setLoopbackMode(false)* did the complete opposite of what I wanted it to.
By setting the loopbackMode value to true, it eliminates packets being looped back to the originating socket.
Looks like I need to read APIs more carefully.
Thanks for your help,
JC

---

### Post by iharrold on 2010-01-07
I'm not sure why you need this with a UDP (datagram) broad cast scenario described.  

[http://java.sun.com/j2se/1.4.2/docs/api/java/net/MulticastSocket.html](http://java.sun.com/j2se/1.4.2/docs/api/java/net/MulticastSocket.html)

As datagrams are for the most part to be considered "connectionless" in that clients just listen for the broadcast.  But I believe the MulticastSocket.getNetworkInterface() method is what you want.  I am not positive though, never used it.

As far as the server's receiving their own datagrams, you'll need to recognize they are local and ignore or unjoin the group... but then you'll need a group for server individually.

The DatagramPacket.getAddress() would return the address of the sender and if == localhost then ignore.

Hope that helps, but Java isn't my forte, I'm c++ kind a guy ;)

---

### Post by Axos on 2010-01-10
> **JCoster said:**
> It turns out that *[multicast]socket.setLoopbackMode(false)* did the complete opposite of what I wanted it to.

Yes, that's what you call a brain-dead API. setLoopbackMode(boolean disable) is about as backwards and unintuitive as they come. :D

But the real reason I'm posting on this two-day-old thread is because neither true nor false will disable loopback on my two computers. Behaves the same on either interface (Ethernet or wireless). Strange. So if you are writing a program other people will eventually be using, you should probably find a way to ignore your own packets even if disabling loopback works on your computers.

---

### Post by JCoster on 2010-01-10
It does seem incredibly unintuitive.  

This may seem obvious (so sorry if you already are!) but are you sending and listening multicast packets from the same instance of the socket?  Originally I had 2 objects of multicast socket, one with a port bound and one without (i.e. it would broadcast on any available port to a specified port).  However, I now broadcast on the same socket I listen on.

Sorry if that's hard to follow- I fear I rambled.  

JC

---

### Post by dwhitney67 on 2010-01-10
> **JCoster said:**
> It does seem incredibly unintuitive.  

This may seem obvious (so sorry if you already are!) but are you sending and listening multicast packets from the same instance of the socket?  Originally I had 2 objects of multicast socket, one with a port bound and one without (i.e. it would broadcast on any available port to a specified port).  However, I now broadcast on the same socket I listen on.

Sorry if that's hard to follow- I fear I rambled.  

JC

You lost me now; the title indicates that you were Multicasting, and then the paragraph above indicates that you are Broadcasting.  Which is it?

P.S.  When I have a client send a multicast message, the server receives it once, regardless if both apps are running on the same system.  If the client is elsewhere, then the behavior is the same.

---

### Post by JCoster on 2010-01-10
Yeah sorry I mean multicasting.

What we're saying is that should a server multicasting a packet also be running a multicast listener thread, we do not wish the server to receive its own multicasted packet.

---

### Post by dwhitney67 on 2010-01-10
I think the issue you are having is related to an issue I had at work the other day.

At work I was involved in an attempt to tighten the system's firewall so as to prevent multicast packets coming from the outside (that is, outside the server's system).  Our client app's and server app run on the same system.

One thing I noticed, no matter what I tried, was that the client message source address was *not* 127.0.0.1 as one would expect, but was the IP address of the eth0 interface.

I would imagine that the same is occurring on your system, even if it is the server that is sending the message.

Thus the loopback settings you fiddled with would have no effect, unless you were using unicast or broadcast?

Another colleague in my office did some research, and found that it is not possible to spoof multicast messages with a source address of 127.0.0.1.

I have not taken the time to confirm this myself, so if you know of a way, please let me know.

---

### Post by JCoster on 2010-01-10
The loopback settings did work on my system, but i assume because i only run one instance of the server on it?

---

### Post by Kungalm on 2010-01-10
Since I have written a couple of reliable multicast api in Java before I would recommend that you use something that is already available, like JGroups. If you want to communicate the state of various participants distributed of a network you must make sure the communication is always correct, I.E. no package loss etc. This wasn't really an answer to your specific problem rather me just sharing my experience. Good Luck with your project.

---

### Post by dwhitney67 on 2010-01-10
> **JCoster said:**
> The loopback settings did work on my system, but i assume because i only run one instance of the server on it?

The loopback setting works on a per-socket basis.  Regardless of this, if your server is binding to a port, it is unlikely that another instance of the server would be able to do the same (on the same port, that is).

---

### Post by JCoster on 2010-01-10
Yeah it can't- the system is designed purely to run one instance-per-machine.

---

### Post by Axos on 2010-01-10
> **JCoster said:**
> are you sending and listening multicast packets from the same instance of the socket?  Originally I had 2 objects of multicast socket, one with a port bound and one without (i.e. it would broadcast on any available port to a specified port).  However, I now broadcast on the same socket I listen on.

Yes, I am using only one MulticastSocket for both sending and receiving. This is how I initialize it:

MulticastSocket multicast = new MulticastSocket(PORT);
multicast.setTimeToLive(TTL);
multicast.joinGroup(inetAddr);
multicast.setLoopbackMode(true);

---

### Post by JCoster on 2010-01-10
Hmm that looks pretty much identical to my code.  Have you tried testing it on a different system to rule out whether it is the code or the system?

---

### Post by Axos on 2010-01-10
I have condensed my code into one single-threaded method to make it suitable for posting and analysis. The goals are succinctness and simplicity, not efficiency and reality. :D

I'll be very happy if someone finds a mistake. No, I am not an expert at multicasting. I learned a lot while writing this.

```

public void example(String name, InetAddress addr, int port, int ttl, int timeout) throws IOException {
    MulticastSocket sock = new MulticastSocket(port);
    sock.setTimeToLive(ttl);
    sock.joinGroup(addr);
    sock.setLoopbackMode(true);
    sock.setSoTimeout(timeout);

    long lastSendTime = 0;
    byte[] recvBuf = new byte[32];
    DatagramPacket sendPacket = new DatagramPacket(name.getBytes(), name.length(), addr, port);
    DatagramPacket recvPacket = new DatagramPacket(recvBuf, recvBuf.length);
    for (;;) {
        if (System.currentTimeMillis() - lastSendTime >= timeout) {
            lastSendTime = System.currentTimeMillis();
            sock.send(sendPacket);
        }
        try {
            sock.receive(recvPacket);
            System.out.println("received datagram from " + recvPacket.getAddress() + ": " +
                    new String(recvPacket.getData(), recvPacket.getOffset(), recvPacket.getLength()));
        } catch (SocketTimeoutException ex) {
        }
    }

}

```

Running this on two different computers over either Ethernet or wireless produces the following result on one computer:

```

received datagram from /192.168.1.99: mario
received datagram from /192.168.1.98: luigi
received datagram from /192.168.1.99: mario
received datagram from /192.168.1.98: luigi
received datagram from /192.168.1.99: mario
received datagram from /192.168.1.98: luigi

```

And on the other...

```

received datagram from /192.168.1.98: luigi
received datagram from /192.168.1.99: mario
received datagram from /192.168.1.98: luigi
received datagram from /192.168.1.99: mario
received datagram from /192.168.1.98: luigi
received datagram from /192.168.1.99: mario

```

---

### Post by Axos on 2010-01-11
I think I've figured it out. There are apparently a ton of multicast bugs in Java which are specific to multi-homed Linux systems. It looks like they are going to be fixed in 6u18 (the current release is 6u17 at the time I'm writing this).

I wrote a C program today which has none of the problems my Java program has. That's when I finally got the "bright" idea to do some Googling. First hit I got was one of the bugs.

---

### Post by dwhitney67 on 2010-01-11
> **JCoster said:**
> I'm currently building a distributed server system and am having a problem with multicast DatagramPackets looping back to the local system.  

I basically have several servers which are to run this application and will periodically send a multicast message over the network informing the other servers that it is still online.  I have a listening thread running on each server which reacts whenever a packet is received on the MulticastSocket.

However, I am having a problem with each server receiving its own multicast messages.  I have set the multicast socket loopback mode to false but still have the issue.  It would not be an issue could I detect the LAN address of the machine as I could just set it to ignore any packets from its own address, yet calling [multicast]socket.getLocalAddress() it just returns 127.0.0.1, or 0.0.0.0.  

Any help is greatly appreciated.
Cheers,
JC

EDIT:  Sorry, I confused the OP with issues posted by Axos.

I took the code Axos posted in another thread, modified it slightly so that I could compile and run it.  I did not have any of the troubles whatsoever setting the Loopback Mode.  Could it be that you are using a dated version of java??

I have this version of Java on my Ubuntu 9.10 system:
```

javac -version
javac 1.6.0_0

```
Below is the code I tested with.  Note that the socket's **timeout** is set to 1 second, the **TTL** to 1 (so that packets are sent out across the local subnet), and the **loopback mode** is set to **true**, thus preventing the server from receiving its own multicast messages.
```

import java.net.*;
import java.io.IOException;

public class example
{
   //public void example(String name, InetAddress addr, int port, int ttl, int timeout) throws IOException
   public static void main(String[] args)
   {
      try
      {
         String      name    = "Hello World";
         InetAddress addr    = InetAddress.getByName("225.0.0.35");
         int         port    = 12345;
         int         ttl     = 1;
         int         timeout = 1000;
         boolean     loop    = true;

         MulticastSocket sock = new MulticastSocket(port);
         sock.setTimeToLive(ttl);
         sock.joinGroup(addr);
         sock.setLoopbackMode(loop);
         sock.setSoTimeout(timeout);

         long lastSendTime = 0;
         byte[] recvBuf = new byte[32];


         DatagramPacket sendPacket = new DatagramPacket(name.getBytes(), name.length(), addr, port);
         DatagramPacket recvPacket = new DatagramPacket(recvBuf, recvBuf.length);

         for (;;)
         {
            if (System.currentTimeMillis() - lastSendTime >= timeout)
            {
               lastSendTime = System.currentTimeMillis();
               sock.send(sendPacket);
            }
            try
            {
               sock.receive(recvPacket);

               System.out.println("received datagram from " + recvPacket.getAddress() + ": " +
                      new String(recvPacket.getData(), recvPacket.getOffset(), recvPacket.getLength()));
            }
            catch (SocketTimeoutException ex)
            {
               System.out.println("Timed-out waiting for message...");
            }
         }
      }
      catch (IOException ex)
      {
      }
   }
}

```

P.S.  Run this code on two different servers; each server should (will) receive only the messages from its peer.

---

