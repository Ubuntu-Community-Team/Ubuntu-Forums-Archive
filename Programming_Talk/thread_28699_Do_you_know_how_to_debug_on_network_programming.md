---
title: "Do you know how to debug on network programming?"
date: 2005-04-21
forum: Programming Talk
---

### Post by Se7EnNi9E on 2005-04-21
On network(socket) programming, it is very hard to debug the bug.

GDB is useless on network programming.

Do you know a good tip how to debug well?

---

### Post by andvaranaut on 2005-04-21
Maybe using a packet sniffer (ethereal, for instance) would help? I have used ethereal/tcpdump in troubleshooting network problems and they have helped immensely. 

However, with these you will only see what your program sends/receives. If the error is on a lower layer (ie. your program is not able to bind to the socket or something like that) you might have to complement them with more traditional debuggers such as gdb.

Best regards

---

### Post by xsdevnet on 2005-05-15
Actually, I find GDB to be very useful when debugging network programs.  The biggest help is having two computers where you can run GDB.  One for the client and one for the server.  Then you can see what is being sent and what is being received.

Thanks,
Steven

---

### Post by odyniec on 2005-05-15
Another tool worth mentioning is netcat (nc), often referred to as the swiss army knife of networking. In fact, the tcpdump+netcat duo is all I ever needed to debug my network applications.

---

### Post by subterrific on 2005-05-15
I mainly use 3 tools when doing network programming.

1) good logging. this includes printf-style debug statements and writing packets to a file. log with time stamps too, the extra effort it takes to write good logging code will save you tons of debugging headaches.

2) tcpdump. this is great for debugging at the networking stack level.

3) gdb. learn it well, it is a powerful tool for any debugging.

---

### Post by LordHunter317 on 2005-05-15
It's kinda hard to tell you what tools to use when you won't tell us what's wrong.  "It doesn't work" isn't useful.

---

