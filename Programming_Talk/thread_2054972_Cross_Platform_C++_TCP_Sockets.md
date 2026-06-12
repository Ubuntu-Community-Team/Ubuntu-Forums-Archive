---
title: "Cross Platform C++ TCP Sockets"
date: 2012-09-08
forum: Programming Talk
---

### Post by SuperCamel on 2012-09-08
G'day  ):P

I was browsing around on an old hard drive the other day, and I found a half finished project that I started a few years ago. A C++ TCP socket library for Windows AND Linux. I could do with something like that for a current project, so I decided to finish it off. 

I know it's been done before (like with Boost.Asio and so on) but this implementation is very very simple. It's good for basic client server applications, HTTP, SMTP, POP and the like. 

Anyway, please tell me what you think. I'm certain the code isn't 100% clean yet. 

[http://www.camelsoftware.com/sockets/index.php](http://www.camelsoftware.com/sockets/index.php)

SuperCamel

---

### Post by dwhitney67 on 2012-09-08
> **SuperCamel said:**
>  
Anyway, please tell me what you think. I'm certain the code isn't 100% clean yet. 


You have a ways to go.  A socket library should be written such that it is generic enough to be used for a variety of application needs.  Your library, as you have mentioned, focuses only on TCP.  It does not allow for UDP, nor any other type of socket; for example file (Unix) sockets or raw sockets.  There's also no way to configure a socket once it has been created.

Also, it should have been obvious to you (the developer) that the underlying socket, whether used by a client or a server, is setup the same way.  Thus there's no need to duplicate code in both areas.  Consider changing your design to something similar to the following (which I don't profess to be perfect either):
```

         Socket                 
           ^                      
           |
   +-------+--------+
   |                |
UDPSocket       TCPSocket
                    ^
                    |
         +----------+-----------+
         |                      |
   TCPClientSocket       TCPServerSocket


```
App developers should be able to instantiate either a UDPSocket, a TCPClientSocket, or a TCPServerSocket.  The other classes should not have their constructors declared public.  When a TCP client connects to a TCP server, then your implementation of the accept() method could return a TCPSocket object.

The other option you could employ is to model the Java API for your socket needs.

---

### Post by SuperCamel on 2012-09-08
Thanks for the feedback. This library was intended to be a simple TCP library, so UPD and other sockets are out of it's scope. It's purpose is to allow quick and easy access to the internet and interprocess communication, rather than be a full socket implementation. 

I think there is a need to have different constructors for both cClient and cServer. Yes, the sockets are set up the same way, but the constructors set up different sockets.  cClient creates the client socket in it's constructor whereas cServer creates the listening socket. cServer doesn't create a client socket until caccept() is called. The purpose for this is so that client socket as well as csend() and crecv() can be inherited rather than implemented separately.

---

