---
title: "sockets not blocking :("
date: 2007-08-12
forum: Programming Talk
---

### Post by desijays on 2007-08-12
Im writing a very silly port scanner. If I give the program a host name and a port number it is supposed to print "PORT OPEN" if the port is open on that host. And it will print "PORT CLOSED" if the port is closed on the host. 

Ive run into a strange problem here.

Now if the port on the host is open it prints "PORT OPEN" as expected. But if the port on the host is closed, the entire program goes into block state. 

The culprit, as I have come to realize is the statement where Im using the 'connect' system call. The connect blocks by default. That is the reason the call returns if a port is open and blocks if a port is closed ( waiting for it to open, i suppose ). 

So, as you can see, I know what the problem is. I just don't know how to solve it.

Please let me know if my understanding of the problem itself is questionable.

Regards

---

### Post by aks44 on 2007-08-12
You're probably trying to connect to a stealthed port, rather than a closed one. If it really was closed, you'd get a response immediately.

You didn't read much about how TCP handshaking works, huh? ;)

---

### Post by the_unforgiven on 2007-08-12
As per the man page of [connect]("http://linux.die.net/man/2/connect"), if the connection cannot be established, you'd get one of the error codes (in errno) and connect() will return with -1.
Are you checking for these conditions?
One of the error codes is ETIMEDOUT.

---

### Post by desijays on 2007-08-12
> **aks44 said:**
> You're probably trying to connect to a stealthed port, rather than a closed one. If it really was closed, you'd get a response immediately.

You didn't read much about how TCP handshaking works, huh? ;)

I did come across stealthed ports in course and the fact that its a non-standard behaviour employed by hardware or software firewalls across the protocol stack.

In any case, stealthed ports do not conform to protocol. And that's why I didn't think google or yahoo would be using them. I was testing this silly port scanner on them :)

---

### Post by desijays on 2007-08-12
> **the_unforgiven said:**
> As per the man page of [connect]("http://linux.die.net/man/2/connect"), if the connection cannot be established, you'd get one of the error codes (in errno) and connect() will return with -1.
Are you checking for these conditions?
One of the error codes is ETIMEDOUT.

Thanks mate. Should have read TFM :)

Like you said, ETIMEOUT is set when the kernal enforced timout comes into play.

Its EINPROGRESS that I should be checking for.

---

