---
title: "Is it possible to simulate a network on a single machine"
date: 2009-11-11
forum: Programming Talk
---

### Post by rbaleksandar on 2009-11-11
Hi, guys. ;)

  Since I've started with socket programming, I need lots of practice. Alas, I don't want to go to my uni everytime I want to try something out (there are also usage restrictions there too) and since I have only one computer at home (note: with only one network card), I was wondering if it's possible to simulate a client-server behaviour on it. :) Nothing too fancy for now - just sending/receiving packages of data. If it's possible, can you tell me a way to do that in Ubuntu (I don't want to use Win :D).

Thanks in advance!

---

### Post by 0cton on 2009-11-11
127.0.0.1 is the address of the localhost.
This means that if you run a server on your machine that listens to a certain port let's say a web-server on port 80 than naturally connecting with a client (in this case a web browser) to http:/127.0.0.1 will work :P
so yes if you run a server on your machine, to access it with a client you must just connect it to 127.0.0.1 and the port it is listening to.
And you can have as many clients as you want and servers as well (Limited by number of ports , up to 65535 and some are reserved for stuff in other words there are already servers listening on some ports ) and system resources of course.
Hope I made it clear.
edit: the localhost address is OS agnostic you can do it on any OS (that has network support)

---

### Post by rbaleksandar on 2009-11-11
Thank you for your reply. :)

  Ok, now I know that it's possible. I have an idea and hope you can tell me if it's right. It's all basic programming (and no web browsers involved; want to stick to the consoles for now):

```

Terminal 1: running the server here
Terminal 2: running the client (connect to **127.0.0.1** and give the port)

```

  Am I right? :)


Thanks again!

---

### Post by konqueror7 on 2009-11-11
you can also make use of virtual machines if you like. this will also simulate a network wherein different systems are involved...:)

---

### Post by 0cton on 2009-11-11
yes you are right
running server that listens on Port X
connect a number of clients to 127.0.0.1:X
and it should all work :P
Good luck Coding :P

---

### Post by 0cton on 2009-11-11
> **konqueror7 said:**
> you can also make use of virtual machines if you like. this will also simulate a network wherein different systems are involved...:)

Yes but localhost will suffice.
at the kernel level a socket has the same structure, I mean you treat it the same way, no matter what address it is associated with, it is abstracted into "something else".

---

### Post by rbaleksandar on 2009-11-11
Well, I'm trying very basic stuff right now, so running this on different OSs isn't my goal for now. :P Virtual machines can be used for more advanced things. Good idea though. Thanks a lot guys! Time for some coding. :D

---

