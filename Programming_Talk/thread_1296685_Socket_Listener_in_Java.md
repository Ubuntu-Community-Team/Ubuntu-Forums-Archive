---
title: "Socket Listener in Java"
date: 2009-10-20
forum: Programming Talk
---

### Post by MCBTunes on 2009-10-20
Ok I am making a Client-Server program in Java, I don't have much experience but everything I try seems to be failing miserably :).

I am wondering if I can make a helper Thread class(say HelperB) that can listen on Client class (say ClientA's) socket... so ClientA can connect to ServerC and when ServerC sends a message back to ClientA on that socket rather than ClientA reading the object if HelperB could read it? That way the user could keep sending messages with ClientA.

Basically, what I am doing is passing the Socket that ClientA made with its connection to ServerC to an instance of HelperB that is being run on ClientA.

Any help?

Thanks.

---

### Post by myrtle1908 on 2009-10-21
[http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html#later](http://java.sun.com/docs/books/tutorial/networking/sockets/clientServer.html#later)

---

