---
title: "Cross-platform networking with C++?"
date: 2008-06-21
forum: Programming Talk
---

### Post by StOoZ on 2008-06-21
what options do I have , except from using Qt??

I dont want to write the code twice , one for POSIX sockets and then another code for windows (winsock).

---

### Post by Dancingwllamas on 2008-06-21
I've had good luck with [Boost::asio]("http://www.boost.org/doc/libs/1_35_0/doc/html/boost_asio.html") for a project this summer.

---

### Post by WitchCraft on 2008-06-22
wxWidgets!

[http://www.wxwidgets.org/](http://www.wxwidgets.org/)

---

### Post by kknd on 2008-06-23
I've written a sockets / winsocks wrapper for C++ ([http://oproj.tuxfamily.org](http://oproj.tuxfamily.org)).

winsocks part needs testing (worked here on wine).

---

