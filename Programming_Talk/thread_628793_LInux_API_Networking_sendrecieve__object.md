---
title: "LInux API Networking send/recieve  object"
date: 2007-12-01
forum: Programming Talk
---

### Post by belikewater on 2007-12-01
I know how to send strings via  write ,read commands
have seen also that there are send recieve commands
Does this commands capable to send/recieve full objects like in java?
maybe cust the const vois *msg parameter?

i will be more than happy if you link me to some learning stuff, my program uses the TCP/IP PROTOCOL in client server implementation

---

### Post by belikewater on 2007-12-01
to sum up : how to pass objects through sockets using linux api netwroking:popcorn:

---

### Post by Vadi on 2007-12-01
In Java?

Java has methods for doing that, I think. At least it has them for reading/writing whole objects.

---

### Post by stroyan on 2007-12-01
It is not clear what kind of 'objects' you are trying to transfer.
If you are dealing with C structs or C++ class instances then you could look
at rpc and xdr library functions for serializing data structures for send and receive.

  There is a old overview of rpc and xdr at 
[http://www.linuxjournal.com/article/2204](http://www.linuxjournal.com/article/2204)

  The RPC concept was reinvented as the XML based SOAP protocol in the
time of the internet boom.  There are many linux libraries for interoperating
with SOAP as well.  Have a look at the output of "apt-cache search soap" for some candidates.

---

### Post by belikewater on 2007-12-02
i use c++  read() write() defined at the linux man pages
also read about:
nt recv(int sockfd, void *buf, size_t len, int flags
I don't use xml right now

---

### Post by belikewater on 2007-12-02
meanwhile i found this:

[http://gnosis.cx/publish/programming/sockets2.html]("http://gnosis.cx/publish/programming/sockets2.html")

---

