---
title: "Port-binding shellcode"
date: 2009-04-09
forum: Programming Talk
---

### Post by jcafaro10 on 2009-04-09
This may not be the best place to post this but, here goes.

I'm exploring buffer overflow for educational purposes.  I have an Ubuntu virtual machine with client and server code.  The server code creates an http server.  I can connect to the http server with the client code and send a request that overflows the buffer with port-binding shell code.  It's supposed to open up a port to listen for connections and then launch a shell when it receives a connection.  At least, that's how I think it's supposed to work.  I've tried two different shell codes for port binding and both have the same effect.  When I netstat -l I can see that the port is indeed listening, but when I try and nc localhost to the port I've opened, the port closes.  I don't think its a problem with my code, so I'm curious if anyone is aware of any Ubuntu features that might cause this to happen?

---

