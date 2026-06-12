---
title: "server programing"
date: 2013-05-16
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-16
hi all.

i'm student in [iust university]("http://www.iust.ac.ir/home_en.php"), i have operating system this season. and i have a project, i have to write client and server application that server provide some services. for example : get ,put,...

and i can not use multithread programing. but server should services to many clients. how can i implement that?!

is it correct that take requests and put them into queue , and response one by one?! do you have idea?!

---

### Post by SeijiSensei on 2013-05-16
Maybe it would help to look at the source for an existing daemon.  I suggest [xinetd](http://www.xinetd.org/), since it does nothing but accept incoming requests and spawns services to handle them.  It also has strong security.

---

### Post by dwhitney67 on 2013-05-16
> **ferizhandi said:**
> hi all.

i'm student in [iust university]("http://www.iust.ac.ir/home_en.php"), i have operating system this season. and i have a project, i have to write client and server application that server provide some services. for example : get ,put,...

and i can not use multithread programing. but server should services to many clients. how can i implement that?!

is it correct that take requests and put them into queue , and response one by one?! do you have idea?!

Each time a client connects to the server, you will obtain a socket descriptor from the accept() call; just add that to your collection containing the listen socket descriptor and any other client socket descriptors that may have previously connected, and use this collection with poll().  When a client disconnects, remove its socket descriptor from the collection.

[Here's]("http://vouters.dyndns.org/tima/All-OS-TCPIP-Programming-TCP-Servers-Using_C_poll.html") an example of how to use poll().  If you require other examples, just Google.

---

