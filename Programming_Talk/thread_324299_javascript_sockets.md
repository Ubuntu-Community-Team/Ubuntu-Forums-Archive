---
title: "javascript sockets??"
date: 2006-12-23
forum: Programming Talk
---

### Post by orlox on 2006-12-23
I was wondering if there exist a way to use tcp/ip sockets on jvascript. I'm working on a project where this possibility would be very usefull...

Does anyone know of a way to do this??

---

### Post by lloyd mcclendon on 2006-12-23
what are you trying to do

afaik, that would be a security nightmare since js is a client side thing.  maybe you want ajax?  it allows you to do http requests from java script

---

### Post by Tomosaur on 2006-12-23
Yeah, JS definately isn't the way to go here, even if it was possible (which I don't think it is). If you want a TCP/IP connection, you are much better off writing a client and server app package than try and hack together something. Are you sure you're going about this the right way? The browser and web-server usually handles the connection stuff, are you sure you can't just do a GET/POST dohickey?

---

