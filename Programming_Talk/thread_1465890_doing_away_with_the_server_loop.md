---
title: "doing away with the server loop"
date: 2010-04-29
forum: Programming Talk
---

### Post by guest_user on 2010-04-29
for writing server programs, there usually is an infinite loop meant to accept connections and process them and when I want to end the server I would normally have to ctrl-c, I find this very inelegant, is there a better way to exit gracefully?

---

### Post by dwhitney67 on 2010-04-29
Setup a signal handler to catch the SIGINT (which is sent via the ctrl-c).  In the handler, set a flag indicating that the program should end.

The server should utilize a select() call (or something similar) that allows one to specify a timeout period.  If after a while there is no activity on the server's socket, and the flag indicating that the server should quit is set, then exit gracefully.

P.S.  I don't know what language your app is written in; with the description I provided above, I assumed either C or C++.

---

### Post by slavik on 2010-04-29
> **dwhitney67 said:**
> Setup a signal handler to catch the SIGINT (which is sent via the ctrl-c).  In the handler, set a flag indicating that the program should end.

The server should utilize a select() call (or something similar) that allows one to specify a timeout period.  If after a while there is no activity on the server's socket, and the flag indicating that the server should quit is set, then exit gracefully.

P.S.  I don't know what language your app is written in; with the description I provided above, I assumed either C or C++.
pretty much every "server" has to do a loop ... because you are always waiting for a connection or similar event.

---

