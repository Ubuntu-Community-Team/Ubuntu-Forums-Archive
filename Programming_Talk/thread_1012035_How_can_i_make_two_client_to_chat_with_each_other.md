---
title: "How can i make two client to chat with each other?"
date: 2008-12-15
forum: Programming Talk
---

### Post by bt87 on 2008-12-15
How can i make two client to chat with each other.. without any work of server, i mean peer to peer i am making chat messenger on which all host will connect to/via server and if any host want private chat then thay work independently...

this is code(attached) which i have made for server side(so far):-

---

### Post by dwhitney67 on 2008-12-15
I took a peek at your "server" code.  I do not quite get why you are forking, why you are creating a directory, and much less why there is a system call being made.

The server needs to accept connections from one or more clients.  Your server code only accepts a connection from a single client.  The application then assumes that the clients will ping-pong with their chat session.  In the real world, this is not the case.  One client can send multiple messages, and while the other client just receives.

I recommend that you consider using a multi-threaded application for your server:  one thread to accept connections, the other thread to receive, and lastly another thread to send data.  It is wise to use select() if your server will handle multiple clients.

For your client application, a multi-threaded application can also be used (although in this case, forking would suffice).  You would need one thread to connect and then send messages, and another to receive messages.

Now, to get two clients to disconnect from the server, and yet continue to chat with each other is a dandy.  Each client would need to act as a server, allowing the other client to connect, or consider switching to using UDP which is connectionless.

Anyhow, if I were you, I would refine your current server application such that it allows multiple clients to connect and chat with each other.  In other words, get the basics working, then later on worry about providing additional functionality.

---

### Post by digitalvectorz on 2008-12-18
Threading, first example (basic)
[http://www.wellho.net/solutions/python-python-threads-a-first-example.html](http://www.wellho.net/solutions/python-python-threads-a-first-example.html)

Threading, using Server/Client as a basis:
[http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/3/](http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/3/)

Socket Programming (Client-server)
[http://www.evolt.org/article/Socket_Programming_in_Python/17/60276/](http://www.evolt.org/article/Socket_Programming_in_Python/17/60276/)


Just a few links to get you pointed in the right direction.

---

