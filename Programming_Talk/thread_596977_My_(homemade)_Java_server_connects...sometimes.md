---
title: "My (homemade) Java server connects...sometimes"
date: 2007-10-30
forum: Programming Talk
---

### Post by r0b0h0b0 on 2007-10-30
Hi all

I posted this question in the general section but have had no replies as yet, so I'm trying here. Sorry for the cross-post.

New to Linux.

I've written a simple HTTP server in Java, which is called to life with a script at startup (not boot). It's listening on port 12999 for requests. It will serve up a requested page sometimes, but not always.

When I connect to my Java server from another machine, the browser will neither connect nor timeout...just sit there and think. When I check netstat on the linux box it tells me a the connection is ESTABLISHED on port 12999, but my micro server does not report a connection. This will happen about 8 times out of 10.???

If, however, I restart my server (close and re-open the Java application), it will work without fail - and not only can I connect to it from another box on the LAN, but also from the internet (I've set it up to do so).

I've not installed any firewalls, nor is the port being used by another process (as far as I can tell).

What gives? Why can I sometimes connect to it first time round, but sometimes not? Why does netstat report that the connection is established but my server doesn't report the connection? If the server isn't connected, but my browser doesn't complain (or timeout), what the heck is my browser connecting to?

---

### Post by geirha on 2007-11-05
To me it sounds like a bug in your java code, but without seeing the code, it's hard to say. Though it's probably easier to debug with telnet. Try "telnet hostname 80" and type "GET /". Does it give similar symptoms?

---

