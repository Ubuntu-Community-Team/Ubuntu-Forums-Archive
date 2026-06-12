---
title: "Developing a networking engine"
date: 2007-11-06
forum: Programming Talk
---

### Post by CaptainPanick on 2007-11-06
Hi guys, I need to develop a multi-client networking server grabbing HTTP data on the one end and spitting it out to one or more client TCP connections on the other side using a pre-designed custom protocol. It's nothing too complex but it needs to run very stable and should be low maintenance.

Instead of going the usual route and developing the server from scratch using Java or something else, I decided to look at some "middleware" networking engines.

The first one I found which looks promising is called Twisted ([http://twistedmatrix.com/trac/](http://twistedmatrix.com/trac/)) and is licensed under the MIT license agreement. Twisted is a Python based solution and provides a non-asynchronous/non-blocking event driven design. As I haven't worked with Python in the past I'll have to learn that also, unless they have some really good examples of servers with custom protocols.

Have any of you guys gone this route before and which networking engine did you use (not that there are that many).

---

### Post by PaulFr on 2007-11-06
Have you looked at libcurl (**[http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)**) ?

---

### Post by pmasiar on 2007-11-06
If you are not afraid of java, working in Python will be pure joy. You will pick it within a week.

Different issue is Twisted - it is called so for a reason. But it is very flexible, and IIRC they have many building blocks already build, like chat. My local Python guru loves it.

---

