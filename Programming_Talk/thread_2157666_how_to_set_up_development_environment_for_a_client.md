---
title: "how to set up development environment for a client/server program"
date: 2013-06-26
forum: Programming Talk
---

### Post by VideoAddicted on 2013-06-26
I need to setup a development environment for a client/server program and am limited to doing my programming on a Ubuntu 13.04 VM (using VirtualBox), is there a way to set it up such that I can effectively simulate the client/server interaction on the same host?  Or is there a way to make my real host act as the client and then I can just push my client script to it?  Initially I wanted to do that last one, but I can't ping my VM from my real host.  Which makes sense kind of I'm really knowledgeable about VMs so I wasn't sure.  For clarification, the server (which is mostly written at this point) is done in Django (which uses Python).  Thanks in advance for any help.

---

### Post by dwhitney67 on 2013-06-26
It's odd that you cannot ping your VM from the host system.  Perhaps a firewall is enabled?  I'm not familiar with VirtualBox, but instead use VMWare (Player).

As for your original question, you should have no trouble setting up a server on your VM and having a client, running on the same VM, exchange data with it.  Your server should, at a minimum, bind its socket to the loopback device (127.0.0.1).  It does not hurt to bind to all interfaces either.  If you do the latter, then your host system should be able to exchange data with the VM.

P.S.  I do not know which programming language you plan to use, not do I know whether you plan to set up a TCP or UDP server.  Hence my response above is very generalized.

---

### Post by VideoAddicted on 2013-06-26
As I stated, Python is the language being used.  As for the binding that you mentioned could you clarify the process involved there or point me in the right direction?  I'm rather unfamiliar with web programming to be honest.

---

### Post by dwhitney67 on 2013-06-26
I do not know Django at all, and my Python is as good as all the money I've been paid to develop in that language... which is none.

However, I have dabbled a bit with Python, and to set up a TCP Server Socket, one would employ the following steps:

1.  Create a socket
2.  Bind the socket
3.  Listen on the socket
4.  Accept connections from clients

Some languages (Python and Java for instance), do not require step 3 to be performed directly.  It's implicitly done when binding the socket.

Here's an example in Python:
```

import Socket

listenSock = Socket.TCPServerSocket()

listenSock.bind('', 9000)

if listenSock.isSocketReadable():
    clientSock = listenSock.accept()

    while 1:
        if clientSock.isSocketReadable():
            data = clientSock.recv(1024)

            if len(data) == 0:
                break

            ...

    clientSock.close()

listenSock.close()

```
I do not know anything about handling multiple clients in Python (either by forking a new process or using threads).  I suppose Google can help you with that.

---

### Post by VideoAddicted on 2013-06-26
Thanks so much for the help.

---

