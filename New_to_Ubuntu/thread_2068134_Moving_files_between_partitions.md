---
title: "Moving files between partitions"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Mortificator on 2012-10-08
Hi,

Just installed Linux for the first time (Ubuntu 12.04) and I partitions my HD as a force of habit thing (no real reason behind it).
As I try to copy files I backed up, I can copy them to my home directory but not to my other partitions (names "Uni" and "****" for uni related stuff and random ****, respectively). It says that I do not have permission to move the file since I do not have permission to create it at the destination.



Also - please note that I would be very happy to solve this without having to switch to a super user since I don't want to have to switch to super user every time I want to move a file.
I can, obviously, repartition but this seems less then ideal.


Would really appreciate some help :)

---

### Post by Mortificator on 2012-10-08
Update: never mind - solved it.

For those that encounter it in the future - chown in the terminal is what I did.
Changed the ownership so I can access my other partitions.

---

### Post by newb85 on 2012-10-08
Great work!  Go ahead and mark the thread as Solved by clicking on the "Thread Tools" link at the top of the thread.

---

### Post by audiomick on 2012-10-08
> **Mortificator said:**
> Update: never mind - solved it.

For those that encounter it in the future - chown in the terminal is what I did.
Changed the ownership so I can access my other partitions.

For those that prefer a GUI solution, you can open Nautilus with root priviliges. You need to go to a terminal to do that

```
gksu nautilus
```

then you get an instance of Nautilus (the file manager) that is owned by root. Here, you can right click on any file or directory, choose properties and change the permissions there to what you want.

It is a good idea to close your root nautilus immediately when you are finished. It is not such a great idea to be working in the file manager with root privileges unless you specifically need to.

---

