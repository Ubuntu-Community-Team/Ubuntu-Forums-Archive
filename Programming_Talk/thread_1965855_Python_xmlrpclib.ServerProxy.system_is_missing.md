---
title: "Python xmlrpclib.ServerProxy.system is missing"
date: 2012-04-26
forum: Programming Talk
---

### Post by kumoshk on 2012-04-26
```
import xmlrpclib
server=xmlrpclib.ServerProxy("…") //… is shorthand for my server URL
```

//server.system is missing (and more importantly server.system.listMethods() is also obviously gone.

What's going on? Any ideas? Do I need to do something to initialize it before it exists? I'm using python version 2.6.6

---

### Post by The Cog on 2012-04-29
what happems when you try:
> methods = server.system.listMethods()
print "methods:", methods
I understand that this is only optional for xmlrpc servers, so the server you are connecting to may not implement this call.

---

