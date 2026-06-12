---
title: "RPC port mapper problem"
date: 2009-10-28
forum: Programming Talk
---

### Post by calin.burloiu on 2009-10-28
I'm trying to run some RPC c examples. I compiled the client and the server and then I tried to excute the server:
```
$ ./server &
```but I get this error:
```
Cannot register service: RPC: Unable to receive; errno = Connection refused
unable to register (MESSAGEPROG, MESSAGEVERS, udp).
```I noticed that the RPC port mapper rpcbind / pmap si not running by using ```
netstat -tlnp
``` .
**How can I turn on the port mapper?**

---

