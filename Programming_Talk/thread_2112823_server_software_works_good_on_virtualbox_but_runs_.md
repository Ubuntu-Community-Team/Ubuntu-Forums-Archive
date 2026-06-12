---
title: "server software works good on virtualbox but runs differently on vps"
date: 2013-02-05
forum: Programming Talk
---

### Post by luckyisdog on 2013-02-05
When running the server software on VirtualBox, it replies to the client's requests to LOGIN or REGISTER or JOIN_QUEUE, and details socket connect/disconnect

On the other hand when running the same server software on an Ubuntu VPS, it does not reply to the client's request but it still works with socket client/disconnect just not with LOGIN/REGISTER or JOIN_QUEUE. 

It is still the same exact software. Any reason behind this? Maybe VPS's are more skimmed out to the bare minimums?

---

### Post by luckyisdog on 2013-02-05
Maybe it's because I'm not applying a NULL \0 to every message..?

---

### Post by luckyisdog on 2013-02-13
now it is segfaulting right on execution. Maybe permissions? or allowing more memory for the program? Can anyone give me any tips for allowing more memory for my server software? Like when you compile and run a program and the compiler automatically allocates memory for the program to debug.

---

