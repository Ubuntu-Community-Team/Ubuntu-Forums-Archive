---
title: "What is a transport? (python + twisted)"
date: 2007-08-23
forum: Programming Talk
---

### Post by oxygen on 2007-08-23
Hi all,

I'm trying to write a simple python script that listen for data via UDP on port 3000 and then writes it out to a file. I've modified an example from the twisted documentation as a starting point.

```
import datetime
import os
from twisted.internet.protocol import DatagramProtocol
from twisted.internet import reactor

class Record(DatagramProtocol):
    
    def datagramReceived(self, data, (host, port)):
        t = datetime.datetime.now()
        #print t.strftime("%Y%m%d%H%M%S")
        filename = t.strftime("incoming\%Y%m%d%H%M")
        if os.path.isfile(filename) == 0:
            print "Writing file"
            f = open(filename,'a')
            f.write(data)
            f.close
        else:
            print "File already exists"
        #print data
        self.transport.write(data, (host, port))

reactor.listenUDP(3000, Record())
reactor.run()
```

It currently works fine - but I don't understand the use of this function.

```
self.transport.write(data, (host, port))
```

Can some explain the concept of a transport to me? I've tried reading the twisted documentation but it's not getting through!

This is the first Python programming I've ever done - so maybe it's a language thing - I do know other languages though (PHP, Javascript, etc).

---

### Post by slavik on 2007-08-24
here comes the OSI model :P

Physical
Data Link
Network
Transport
Application

note: application layer in the "older" OSI model was separated into session, presentation and application, but most applications handle all of that on their own.

transport is tcp/udp/sctp and others.

---

### Post by oxygen on 2007-08-25
Hi slavik,

I do understand a little bit about the OSI model. The part I don't get is that - with the code I have here - I have already received the UDP data (as I can print it to screen, write to a file, etc).

What is the **self.transport.write** function actually doing? Is it retransmitting it or something?

Thanks

---

### Post by slavik on 2007-08-25
looking at the code, seems like it does.

if you can, find the man page for the object :)

Also,
```

            f = open(filename,'a')
            f.write(data)
            f.close

```

do you actually want to open and close the file for every datagram? wouldn't it be better to open it in the beginning of the program and then close it at the end.

---

### Post by cwaldbieser on 2007-08-25
> **oxygen said:**
> Hi slavik,

I do understand a little bit about the OSI model. The part I don't get is that - with the code I have here - I have already received the UDP data (as I can print it to screen, write to a file, etc).

What is the **self.transport.write** function actually doing? Is it retransmitting it or something?

Thanks

Calling write() on the transport writes data back to wherever you received it from.

---

### Post by slavik on 2007-08-25
> **cwaldbieser said:**
> Calling write() on the transport writes data back to wherever you received it from.
since he is using UDP, what could be the point of that (is there one?) my understanding is that once you send a UDP packet, you sit and hope to god that the other party got it.

---

### Post by cwaldbieser on 2007-08-25
> **slavik said:**
> since he is using UDP, what could be the point of that (is there one?) my understanding is that once you send a UDP packet, you sit and hope to god that the other party got it.
It can still be useful to have two endpoints to a communication even if the underlying protocol doesn't make reliability guaruntees.  TCP can be impleneted from UDP, for example.

---

### Post by oxygen on 2007-08-25
> **slavik said:**
> do you actually want to open and close the file for every datagram? wouldn't it be better to open it in the beginning of the program and then close it at the end.

Hehe - at the moment yes to make sure I'm getting the correct data. Eventually I'll be processing it and putting it in a mysql database. It's actually NMEA strings that I'll be receiving.

---

