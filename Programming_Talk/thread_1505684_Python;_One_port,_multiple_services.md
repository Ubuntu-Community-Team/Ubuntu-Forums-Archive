---
title: "Python; One port, multiple services"
date: 2010-06-09
forum: Programming Talk
---

### Post by Psycho.mario on 2010-06-09
Is it possible to have a python socket, listening on a port, which receives a connection (e.g HTTP or SSH) , scans the data, and decides which protocol its on, then redirects it to another socket connected to localhost with the correct port. 

For example: i SSH into the listening socket on (e.g) port 2280, it realises that it's SSH traffic and then sends it to a socket connected to localhost port 22; I then browse to the same port, it sees it as HTTP traffic, then redirects it to localhost port 80

I am basically asking if this is possible, then i could use it to get into my LAN through only one port, but with lots of services

Thanks

---

### Post by DanielWaterworth on 2010-06-09
You could, but I think it might be easier to use ssh forwarding (ssh -L) or a VPN for your web traffic.

---

### Post by Psycho.mario on 2010-06-09
I know that would be easier, and probably more efficient, but i wanted to try and write a program for it, to test my skills, and then it could be used when there is no ssh or vpn server available to me

---

### Post by DanielWaterworth on 2010-06-09
In that case, you'll need a program to print out the first thing that you receive from each protocol. You can then write a program to discriminate between the messages and forward the socket. Something like this will print the first line in a protocol:
```

import socket

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind(('', 10000))
sock.listen()
s, e = sock.accept()
while 1:
    d = s.recv(1)
    if not d:
        break
    print (d)
```

You can then goto [http://localhost:10000](http://localhost:10000) and see what appears and try to ssh it and all sorts. The program above is entirely untested.

---

### Post by Tony Flury on 2010-06-09
No reason why you couldn't do that however you would need to ask yourself :

1) How does your program identify SSH traffic or http - can you reliable do that on every possible packet ?
2) How will you mimimise the delays from your program handing off data from the incoming to the outgoing socket ?
3) What about other information that might be useful - like the source IP address details - or the port - how will your program cope with that ?

---

### Post by Psycho.mario on 2010-06-09
I was thinking about analysing the packets, then sending them off, so that you could only have one connection at the same time, however i cant seem to be able to find a way to read the packets, raw, without stopping them, and then acting on that packet. kind of like a queue, but i would need to be able to recieve the raw packets (e.g what you see in tcpdump) put them in a variable, find out what service they are destined for, and then send them on their way to that service, i imagine there would be some differences between the first HTTP packet and the first SSH packet in a sequence, but i need to be able to view that in python first

---

### Post by DanielWaterworth on 2010-06-09
This is a little more polished:

proto.py:
```
import socket, sys, select

if len(sys.argv) != 2:
    print("USAGE: %s [PORT]" % sys.argv[0])
    sys.exit(1)
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind(('', int(sys.argv[1])))
sock.listen(5)
s, e = sock.accept()
while 1:
    if select.select([s], [], [], 0.5)[0]:
        d = str(s.recv(1), 'utf-8')
        if not d:
            break
        print(d, end='')
        sys.stdout.flush()
    else:
        break
s.close()
```

edit: it'll only work on python3

---

### Post by Psycho.mario on 2010-06-09
Does that just listen on a port and print what it receives? I can do that, its the first packet inspection i dont know how to do.

---

### Post by DanielWaterworth on 2010-06-09
Just put the timeout value on the select call really low. I don't think you can get individual packets on TCP.

---

### Post by Psycho.mario on 2010-06-09
It doesnt look like its possible, for the ssh, its a SYN, SYN ACK, ACK, and then the server sends data, which means that this won't work. Looks like i will have to do ssh local forwarding. There isn't an option for me to use my own client sadly.

If anyone has any suggestions as to how to get this to work feel free to comment.

Thanks for the help

---

### Post by soltanis on 2010-06-09
SSH is a three-way handshake initiated by the server. Your idea is not one of a kind though; TCP port 1 was the "multiplexing" port (not many people use it). Read about it:
[http://en.wikipedia.org/wiki/TCPMUX](http://en.wikipedia.org/wiki/TCPMUX)

---

### Post by Zugzwang on 2010-06-10
It appears as if the people participating in this thread all have a different idea what the actual idea was.

I think that in principle it is possible to do the following:
[LIST]
[*]We have a program listening on a port (the server).
[*]Whenever there is a connection to the server, the server accepts the connection and waits for the client to send some data.
[*]When the client has sent some data, the program uses some heuristic to find what whether it was HTTP, SSH, etc. traffic.
[*]Then, the server looks up in a table where traffic for the respective protocol should be routed. For example, HTTP traffic should be routed to 192.168.0.12:80
[*]The server then opens a connection to that port, sends the first chunk of data recieved and acts as a forwarding program from that point on (until the TCP connection is closed).
[*]Whenever the server does not get some data in step 3 after, let's say, 3 seconds, it asserts that the traffic is belonging to some protocol for which the server sends the first chunk of data. In this case, the connection is forwarded to some fall-back IP-Address/Port.
[/LIST]

Such a thing would work fine with HTTP (as the client sends the first chunk of data) and probably SSH (here, AFAIK, the RFC states that both ends of the line should start communicating, so technically it should suffice to wait for the client. Strictly speaking, this waiting would violate the RFC description, but it might work anyway).

All in all, you can only have one protocol where the server sends the first chunk of data this way. So no TELNET and POP3 at the same time (except if we assume, for example, that the TELNET user first hacks some rubbish into the console in order to signal the usage of the TELNET protocol).

-------------------

@Psycho.mario: Your SYN/SYN ACK/ACK argument is interesting, but for the application you are describing, there is no need to intercept the packages this early. Instead, this forwarding server program could act as "man in the middle". This would, of course, mean that the actual server to which the data is forwarded would not see the original source of the connection, just like this is the case behind a NAT router.

---

### Post by Psycho.mario on 2010-06-10
Zugswang, this is exactly what i wanted. I didn't think that the data would start in different directions. I shall have to look into this tomorrow. It wont be used for things like POP3, email things, or telnet becuase it's so insecure, i think SSH and HTTP will be what i write the program for, but i could re-use it for different protocols as the need comes along

Thanks

EDIT: TCPMUX is the kind of thing i want, but it's not really an option because i cant use custom clients, sadly.

---

### Post by soltanis on 2010-06-10
In any case, I think it is difficult if not impossible to set up this kind of service with SSH. The entire purpose of the protocol is to prevent man-in-the-middle attacks, and so the first step of the protocol is a cryptographic handshake initiated by the server which proves its identity to the client. Even if you wrote a program that replicated this functionality, since the handshake process is started by the server, how would you deal with the HTTP client, whose protocol dictates the client sends the first message?

You can't distinguish between the two during the connection phase, by the way; SYN, SYN ACK, and ACK handshake is characteristic of all TCP connections being initiated and you can't modify this process in any case unless you use raw sockets.

---

### Post by DanielWaterworth on 2010-06-11
@soltanis, a man-in-the-middle attack involves using the response from a client to masquerade as the client. This is different, this is just acting as a dumb pipe.

This is possible and quite simple to do, especially in this limited HTTP/SSH case.

[LIST]
[*]Listen for traffic.
[*]Do a select call with a small timeout.
[*]If the socket is ready for reading, proxy traffic between the web-server and the socket
[*]else, proxy traffic between the ssh server and the socket.
[/LIST]

---

### Post by Psycho.mario on 2010-06-11
If i were to throw the traffic at both services, would one of the services just not understand and give up, whilst the other one would respond?

---

### Post by DanielWaterworth on 2010-06-11
That's an interesting idea. It might work, it's worth a try.

---

### Post by Psycho.mario on 2010-06-11
Hmmm.... Doesnt work, becuase ssh gives a version number to a http client, and ssh hangs on connection to a http server

---

