---
title: "How to Run Python .py Program on Web ServeR?"
date: 2013-03-05
forum: Programming Talk
---

### Post by Yuva Raj on 2013-03-05
Hi,
I can run Python program (xx.py) in my Ubuntu through Terminal.
Similarly, how can we run our Python program on Web Server?

The task is that, it listens the Client request & responds according to them.
Here,Python Program acts as a Server side Scripting for our coding. 
So,it will be helpful if anybody suggests how to run Or Initialise the Server .py Python program on Web server.

---

### Post by sanderj on 2013-03-05
Search "CGI Python"

---

### Post by Yuva Raj on 2013-03-06
Please look at this : [http://fragments.turtlemeat.com/pythonwebserver.php](http://fragments.turtlemeat.com/pythonwebserver.php)

Here they are running webserver.py in LocalHost.
[COLOR=#000000][FONT=Times New Roman]similarly can i run it in my web site??

Please Help!
[/FONT][/COLOR]

---

### Post by sanderj on 2013-03-06
It looks you ignored my advice, so I'll now unsubscribe from this thread.

Good luck.

---

### Post by lykwydchykyn on 2013-03-06
It's hard to understand exactly what you are asking, but if you want to run a python http service:

- You can set up some WSGI framework like Flask, CherryPy or Web.Py behind apache with mod_wsgi
- You can use a library like twisted to implement a simple http service directly

Really depends on what you're actually writing.

---

