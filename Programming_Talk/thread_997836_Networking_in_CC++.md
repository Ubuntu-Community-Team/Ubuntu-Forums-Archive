---
title: "Networking in C/C++"
date: 2008-11-30
forum: Programming Talk
---

### Post by Arukas on 2008-11-30
I've just recently brushed up on my C/C++.  I've made some simple games with C/C++, now what I would like to do is make some simple games you can play over the internet.

All I want to connect is two people, and possible up to eight.  Anyone know where to start?  I have never done anything like this before.  And things I"ve read have nothing to do with what I want to do.

---

### Post by dwhitney67 on 2008-11-30
You need to develop a server and a client.  These two can communicate using TCP or UDP.

For TCP, the server awaits a connection from the client(s); one the client has connected, data transfers can begin.

For UDP, the server vs. client relationship is connectionless.  Thus the client can send data to the server that is expecting to receive something, then the server can respond to that client (using information obtained while receiving the message).

Google or wiki information concerning TCP and/or UDP to determine which suits your needs, then brush up on the C library calls that can make it happen.

If you are developing in C++, I have a [socket library]("http://www.softhouseproductions.com") that can be used.  As I have stated in other posts, the library will not meet everyone's needs; however for typical TCP or UDP needs for a server and/or client, it works great.

If you are not familiar with multi-threaded applications, you also may want to look into that.  When a TCP server needs to support more than one client, it is useful to be able to accept connections in one thread, and in one or more other threads, handle data exchanges with individual clients.

---

### Post by Arukas on 2008-11-30
I'll read more up on TCP and UDP, I am familiar with TCP.  And I have done with multi threading too.  I've never tried to do something over the internet, so command and libraries elude me at the moment.  

Where do I go to find more libraries if the one you have doesn't solve my problems.

---

### Post by heikaman on 2008-11-30
I just wanted to add that you should really think about the protocol first, how your client and server are going to talk/exchange information about the game.

I also have to say that using threads isn't probably your best choice read "man select_tut"

---

### Post by dwhitney67 on 2008-11-30
> **heikaman said:**
> ...
I also have to say that using threads isn't probably your best choice read "man select_tut"
This really depends on how many messages the server can expect to receive from the client(s) per second.

If the server expects to receive a lot of messages, spend time processing these, and respond to the client, all while accepting connections from new clients, a multi-threaded application would seem to be in order.

Otherwise, clients will be waiting for their turn to access the server while the server is busy servicing the first client.  Now that would be inefficient!

---

### Post by dwhitney67 on 2008-11-30
> **Arukas said:**
> I'll read more up on TCP and UDP, I am familiar with TCP.  And I have done with multi threading too.  I've never tried to do something over the internet, so command and libraries elude me at the moment.  

Where do I go to find more libraries if the one you have doesn't solve my problems.
Read the man-pages.  For example:
```

man socket
man bind
man listen
man accept
man connect
man close
man send
man recv

```

---

### Post by heikaman on 2008-11-30
> **dwhitney67 said:**
> If the server expects to receive a lot of messages, spend time processing these...

yeah that's why I said probably, however, the op mentioned that he expects 2-8 players right ?

and I think there will not be any processing involved, the server will probably forwards the messages between players.

---

### Post by Arukas on 2008-11-30
is there a better way to display those the "man socket" stuff?  I don't like using terminal and not for sure how to fix the problem.

---

### Post by StOoZ on 2008-11-30
so look for the man pages over the web...

---

### Post by Arukas on 2008-11-30
I don't understand what you mean and saying basically "google it" isn't going to help.  Googling comes after I find a my direction.

---

### Post by dwhitney67 on 2008-11-30
Click on this [link]("http://linuxmanpages.com/") to view the man-pages.

Wrt to any application you wish to develop, you will have to start developing that yourself.  You may be required to procure a book on the subject of networking programming, or google for examples.

Once you have code in place, and for whatever reason it is buggy or has some other concrete issue, then please post your query here on the forum.

Thanks.

---

### Post by Sydius on 2008-11-30
The low-level layer used by a lot of applications is based on Berkeley sockets, including the WinSock implementation for Windows.  If you want an additional layer of abstraction above that, there are a number of libraries available (I have yet to find one I love), including ASIO from BOOST in the C++ domain.  I generally prefer BOOST over custom wrappers or other solutions, but I couldn't understand ASIO, so I rolled my own abstraction layer on top of Berkeley sockets.

As for single-threaded asynchronous vs. multi-threaded: my research seems to indicate multi-threaded is the way to go if you expect long processing times for individual responses and don't expect there to be a large amount of communication between threads that might cause locking.  An HTTP server is a good example.  For games, however, I have found asynchronous to be the way to go because my games would spend too much time locking on shared state/data anyway and dealing with concurrency issues hurt my productivity too much to be worth it.  There are some advanced semaphore techniques to deal with the multi-threading issues, but they just weren't worth it for my games.

---

### Post by Arukas on 2008-11-30
Thanks for the link.  

And, thanks for the advice, Getting started is the hardest part for me.  Especially, since everything I know about networks doesn't pertain to programing them.  Most everything I read is "blah blah blah".  For instance, I haven't found an ubuntu IDE for C/C++ that I can use.  Everything is so much more flexible its hard to figure anything out.  Here's an example, I downloaded emacs, it has so many features I can't figure out how to use it.  And I ask for help, and all I got was a wiki link, which didn't help because it was so vast and general.  (Fortunately, gedit and a terminal pluggin work great)

---

