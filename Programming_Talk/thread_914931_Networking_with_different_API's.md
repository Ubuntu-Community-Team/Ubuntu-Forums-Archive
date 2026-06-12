---
title: "Networking with different API's?"
date: 2008-09-09
forum: Programming Talk
---

### Post by StOoZ on 2008-09-09
is it possible to make a simple networking app (simple means , the app sends some strings to the server and receives a string back..)
that the client will use wxSockets (wxWidgets sockets...) on windows , and the linux version will use boost::asio ??

---

### Post by dribeas on 2008-09-09
> **StOoZ said:**
> is it possible to make a simple networking app (simple means , the app sends some strings to the server and receives a string back..)
that the client will use wxSockets (wxWidgets sockets...) on windows , and the linux version will use boost::asio ??

Libraries give you access to the tcp channel, but it is the data that makes it to the other end. Libraries used in both ends need not be related. Boost::asio and probably wxSockets are wrappers around OS socket layer, so they will be different no matter what you do.

---

### Post by StOoZ on 2008-09-09
Im using C++ , and reading now the Beej's network programming (amazing guide btw!!) , just for learning , I would like to make my linux server side use the linux sockets (dropped the idea of boost , I want to go deeper into linux for educational purposes) , and the client side (windows) , with wxwidgets , so I guess , as for the technical part , everything should work fine?

---

### Post by henchman on 2008-09-09
well, i would recommend either using the OS api (linux sockets / win32 sockets) or an existing abstraction layer like wxwidgets for that job... i wouldn't mix both, because if you use wxwidgets, why don't you make use of it's cross-platformity :)

---

### Post by dribeas on 2008-09-09
> **henchman said:**
> well, i would recommend either using the OS api (linux sockets / win32 sockets) or an existing abstraction layer like wxwidgets for that job... i wouldn't mix both, because if you use wxwidgets, why don't you make use of it's cross-platformity :)

+1
If you are building both sides you'll be better off using just one technology at both ends. At work we use ACE for network layer abstraction, but boost, wxwidgets, poco... there are quite some options out there.

---

