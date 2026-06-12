---
title: "networking with c++"
date: 2008-03-07
forum: Programming Talk
---

### Post by StOoZ on 2008-03-07
what do I need to read about, in order to make a program (server side, and client side) that can "talk" transfer/send data over the web to another computer?
is it socket programming?

---

### Post by Zugzwang on 2008-03-07
Google is your friend.

See [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html"), for example.

EDIT: Note that that tutorial is in fact for C, but you can use the same stuff in C++ (which is not uncommon). If you prefer the pure C++ way, you can use for example the QT framework for building network applications.

---

### Post by the_unforgiven on 2008-03-07
> **Zugzwang said:**
> 
EDIT: Note that that tutorial is in fact for C, but you can use the same stuff in C++ (which is not uncommon). If you prefer the pure C++ way, you can use for example the QT framework for building network applications.
I think, QT will be an overkill for simple console-based network program - even in C++.

The better option is to **design** the code properly and use the socket API in it - i.e. you might want to create constructs/classes like Server having methods like start() - which does a socket(), bind() and listen() calls. The class like Client might have the connect() method which does a socket() and connect() system calls.

Using QT's network module would make sense if you're already linking to QT for UI - otherwise, it's a huge lib sitting in memory only for some socket calls. Mind you, internally, QT is going to do exactly the same thing - except that you'd get the classes already designed for you :p

However, IIRC, QT4 has separate modules altogether - like GUI, Socket etc. So, you might be able to link to just the network module and be done with it. I haven't tried it yet.

HTH ;)

---

### Post by StOoZ on 2008-03-07
I dont want the classes to be designed , I want to design then, I want to learn.

I found a book , about 'socket programming' with C++ under Linux, I guess it will do the trick.
anyhow, I dont need any GUI, I just want to learn how to do it, and not 'just to do it'.

---

### Post by the_unforgiven on 2008-03-07
> **StOoZ said:**
> I dont want the classes to be designed , I want to design then, I want to learn.

I found a book , about 'socket programming' with C++ under Linux, I guess it will do the trick.
anyhow, I dont need any GUI, I just want to learn how to do it, and not 'just to do it'.
Great :)
All the best for your design adventure - I can guarantee that there's lots to be learnt ;)
You can post your questions here - we'll try to help as much as we can :)

---

