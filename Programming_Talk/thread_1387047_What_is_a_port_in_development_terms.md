---
title: "What is a port in development terms?"
date: 2010-01-21
forum: Programming Talk
---

### Post by MaindotC on 2010-01-21
I've taken some programming classes but never wrote anything that involves telling an application to transmit data somewhere, especially using a specified port.  It's just something I've always wondered.  What would code look like that is telling an application to send its traffic to a specific port?  For example, VNC uses port 5900.  So can you just give me a general idea what code would look like that instructs to use a specific port?

I guess this would vary from language to language.  If you have an array of examples, from assembly up to ruby, I welcome them.

---

### Post by dwhitney67 on 2010-01-21
Typically one does not use the term 'port' for what you describe, but instead 'socket'.  You can find boat loads of information if you Google for "socket programming".

Anyhow, after a socket is created, it can be bound to a particular network interface (eg. eth0), or all interfaces (eg. eth0, wlan0, lo) using a specific port number, in the range of 1 through 65535, inclusive.  Using a port number that is less than 1024 requires root-privileges.

Once a port is bound to on a particular interface, it cannot be bound to by another other process.  (I have not confirmed this; maybe root can kick off some grunt application?)

Here's a good guide that many C/C++ folks reference:
[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by MaindotC on 2010-01-21
I'm familiar with what you are describing.  However, my understanding was a socket consists of the address and the port.  I'm a net admin, just not a developer of net admin software.  I'll check out googling the term you suggested.

---

### Post by Some Penguin on 2010-01-22
[http://en.wikipedia.org/wiki/Berkeley_sockets](http://en.wikipedia.org/wiki/Berkeley_sockets)

might be of help.

---

### Post by Zugzwang on 2010-01-22
> **Some Penguin said:**
> [http://en.wikipedia.org/wiki/Berkeley_sockets](http://en.wikipedia.org/wiki/Berkeley_sockets)

might be of help.

That should indeed be of help. Interestingly, this page also talks about "UDP and TCP ports". More details can be found here: [http://en.wikipedia.org/wiki/TCP_and_UDP_port](http://en.wikipedia.org/wiki/TCP_and_UDP_port)

For simplicity, I'll just state the idea of a "port": Assuming that you have a computer with a lot of server software running. Now some client connects to the server. How is the kernel (which is supposed to forward incoming connection requests to the respective application) supposed to know for which application this request is? For this, it uses the port number transmitter together with the communication request. As all server software have registered with the kernel with their desired port number, it just checks if there is any registered application having the port number matching the incoming connection request and forwards it to this particular application.

EDIT: I think I misread your question and focussed too much on the heading. Sorry!

---

### Post by MaindotC on 2010-01-22
No it's cool - I appreciate your answer in any event.  I really understand what a port is, I just wanted to see an example of code that refers to a port.  For example, if I write an application in Java, there is a place to define an address of a SQL-compliant database, the username and password that should be sent to that database.

What I was hoping was someone would show something a little more along those lines, not posting links to wikis.  The Beej's guide is pretty cool though and at first glance it has what I'm looking for:
```

// (IPv4 only--see struct sockaddr_in6 for IPv6)

struct sockaddr_in {
    short int          sin_family;  // Address family, AF_INET
    unsigned short int sin_port;    // Port number
    struct in_addr     sin_addr;    // Internet address
    unsigned char      sin_zero[8]; // Same size as struct sockaddr
};

```
I realize that in development anything can be anything but this seems a little more definitive.  Again, this is on first glance - it's like 500 pages long - so I'll view more of it when I have time.  It's just something I've always wondered.

---

### Post by dwhitney67 on 2010-01-22
I've written a socket library which includes examples written in both C and C++.  You can download it from [here]("http://softhouseproductions.com/SocketLibrary.tgz") if you wish.

---

### Post by MaindotC on 2010-01-25
> **dwhitney67 said:**
> I've written a socket library which includes examples written in both C and C++.  You can download it from [here]("http://softhouseproductions.com/SocketLibrary.tgz") if you wish.

I may check it out but at a later date.  I'm not a dev - it's just one of those things I've always wondered - so it may be difficult for me to understand your source code on first glance.  In any even thank you for the link.

---

