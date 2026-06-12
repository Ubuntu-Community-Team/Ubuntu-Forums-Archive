---
title: "Python UDP Sockets: connection refused"
date: 2009-01-05
forum: Programming Talk
---

### Post by evymetal on 2009-01-05
I'm writing a little udp networking thing in python and I'm having some troubles: machine A is sending packets to machine B fine, but machine B's packets don't seem to be getting through at all (using tcpdump I can't see anything - but should I be able to with udp anyway?)

Machine A is running Hardy, and machine B is running Intrepid.

The code is the same at both ends, and works when I run two instances on localhost. 

Here's the relevant bit of the code - have I overlooked something obvious?

```


other_machine = "[other machine's ip address]"

class networking(object):
    def __init__(self,port):
        # Use UDP
        server_sock = socket.socket( \
            socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)

        # Set to non-blocking
        server_sock.setblocking(0)

        # Listen to port
        server_sock.bind(("", port))

        self.server_sock = server_sock

        self.client_sock = socket.socket( \
            socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)

        self.client_sock.setblocking(0)

        # Want this to be darn quick
        self.timeout = 0
        self.bufflen = 512

        self.read_msgs  = deque()
        self.write_msgs = deque()


    def fetch(self):
        #Check server for reads, client for writes, and both for errors
        r, w, e = select.select([self.server_sock,],[self.client_sock,], \
                    [self.server_sock,self.client_sock], self.timeout)

        if r:
            for s in r:
                # Ready To Read
                self.read_msgs.append(s.recvfrom(self.bufflen))

        if w:
            self.__do_write()

    def __do_write(self):
        """Write the next message to the network"""
        if len(self.write_msgs) > 0:
            msg = self.write_msgs[0]
            sent = self.client_sock.sendto(msg,("other_machine",3002))
            if sent < len(msg[0]):
                self.write_msgs[0] = msg[sent:]
            else:
                self.write_msgs.popleft()


```

---

### Post by dwhitney67 on 2009-01-05
This is interesting stuff.  I do not know Python that well, but I have tinkered with UDP ports.  Why does your application need to have two sockets for the UDP session?  Typically one socket is used to send and receive.

---

### Post by dwhitney67 on 2009-01-05
This is interesting stuff.  I do not Python that well, but I have tinkered with UDP ports.  Why does your application need to have two sockets for the UDP session?  Typically one socket is used to send and receive.


Edit....

I just tested the following trivial UDP client app with my UDP server (which is written in C++); everything worked as expected.
[php]
#!/usr/bin/python

import sys;
import socket;


msg  = "Hello World"
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM, socket.IPPROTO_UDP)
sent = sock.sendto(msg, ("localhost", 9000))

if sent < len(msg):
        print "msg not sent"
else:
        print "msg sent"

msg = sock.recv(12);

if len(msg) > 0:
        print "received",msg
else:
        print "received nothing"
[/php]

---

### Post by evymetal on 2009-01-06
> **dwhitney67 said:**
> Why does your application need to have two sockets for the UDP session?  Typically one socket is used to send and receive.


Ah, that's probably just a habit because that is how I would have arranged it if I was using TCP.

The problem seems to have been a weird network issue, for some reason the second machine was routing traffic through loopback when I tried the first machine's ip address

(The weird thing being that I had just bzr merge'd over ssh from the first machine and that had worked fine)

restarting the interface got it working as expected.

---

