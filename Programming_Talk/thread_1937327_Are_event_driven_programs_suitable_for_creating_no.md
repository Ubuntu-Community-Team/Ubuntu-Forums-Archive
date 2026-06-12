---
title: "Are event driven programs suitable for creating non-graphical applications?"
date: 2012-03-07
forum: Programming Talk
---

### Post by MeguhNad on 2012-03-07
I'm currently doing an assignment for school and this is one of the questions I'm stuck on:
[FONT=Verdana][SIZE=1][FONT=&quot]
Are event driven programs suitable for non-graphical applications? [/FONT][/SIZE][/FONT]

I'm a total noob when it comes to programming so no patronising or any other snide comments please. Any answers/in-depth answers are much appreciated.

Thanks.

---

### Post by Simian Man on 2012-03-07
Event-driven programs are just those that respond to some kind of requests and sit idle at other times.  These are often graphical applications where the requests are things like clicking buttons.  But there are other examples of event-driven programs that are not graphical.  For example a server application could be event driven in that it does nothing until a client makes a request.  Likewise a program that monitors some sensor (like the fuel pressure sensor in your car), will respond to events given to it from the sensor.

So yes :).

---

### Post by lisati on 2012-03-07
A couple of everyday examples from the web: email and web servers. Both sit round idle until someone wants to send an email or browse a web page.

---

### Post by pconroy on 2012-03-07
My first programming jobs in the 80's was in real time embedded systems.  Software in a machine or device that controls it.  They were *all* event driven back then. :)

Event driven stuff is the only way to go...

---

### Post by Khayyam on 2012-03-08
.. and perhaps the most obvious example ...

Welcome to Linux
localhost login:

best ... khay

---

