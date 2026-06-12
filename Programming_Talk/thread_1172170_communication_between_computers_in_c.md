---
title: "communication between computers in c"
date: 2009-05-28
forum: Programming Talk
---

### Post by night_fox on 2009-05-28
What is the fastest, best, and simplest way of sending/recieving data between processes on different computers over the internet from c?

And is there a simple tutorial?

---

### Post by Zugzwang on 2009-05-28
> **night_fox said:**
> What is the fastest, best, and simplest way of sending/recieving data between processes on different computers over the internet from c?

If there was only one way that is fastest, best and simplest at the same time, then there would only be this single way. But there isn't.

First of all, check what you *really* need. Look up TCP and UDP in Wikipedia. Choose what fits best. TCP is slower, i.e., sometimes causes delays due to lost packets. On the other hand, UDP is faster as all information is immediately forwarded to your program, but it may lose packets. If your application is robust against that, then it's possibly the way to go.

The standard way of using either UDP or TCP is by using the UNIX socket functions. But this is just one way. As far as "simple" is concerned, at least for TCP you will have to choose between blocking and non-blocking communication.

---

### Post by night_fox on 2009-05-28
Thanks for that. These sockets seem relatively simple to use. Is there a higher level api that does it?

---

### Post by dwhitney67 on 2009-05-28
> **night_fox said:**
> Thanks for that. These sockets seem relatively simple to use. Is there a higher level api that does it?
Yes, you can try SDL_net library or one that I have written [here]("http://softhouseproductions.com/SocketLibrary-1.1.5.tgz").  Note that my library has not been ported to work on windoze.

---

### Post by night_fox on 2009-05-28
Thankyou!

---

