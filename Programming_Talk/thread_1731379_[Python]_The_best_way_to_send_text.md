---
title: "[Python] The best way to send text"
date: 2011-04-17
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-17
What's the best way to send text via python from one computer to another (Without writing a file)? I've read about telnet and servers, but what is the best way to do it? All other suggestions besides the two named are welcome also.

---

### Post by Tony Flury on 2011-04-17
open a socket

---

### Post by cgroza on 2011-04-17
If the computers are on the same network, use the socket module.

---

### Post by nvteighen on 2011-04-17
Really, a socket. And you could use telnet as your client...

Look at:
[http://docs.python.org/howto/sockets.html](http://docs.python.org/howto/sockets.html)
[http://ilab.cs.byu.edu/python/](http://ilab.cs.byu.edu/python/)

You'll be likely using Threading too if you want your server to accept multiple simultaneous connections.

---

### Post by ki4jgt on 2011-04-17
They could be on the same network, or they could be half way around the world. Just depends what the program decides. I'm wanting to send files and text via this. . . I need to be able to use encryption and assign (both in LAN and out of LAN) IPs

---

### Post by cgroza on 2011-04-17
Take a look at twisted...

---

