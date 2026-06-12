---
title: "Curious about ^c"
date: 2010-02-17
forum: Programming Talk
---

### Post by Carl Hamlin on 2010-02-17
I've been doing some heavy development this last week on a program for a client, and I've notice a number of times during testing that when I use ^c to pull out of an execution gone horribly wrong that while I *do* get the terminal back, sometimes the program still shows up in my ps listing, and still holds onto the port it was using to listen for incoming connections.

Have I misunderstood about ^c, or is there a ghost in my shell?

---

### Post by Ferrat on 2010-02-17
are you sure it's not just a zombie or perhaps an orphan? (depending on how your program works)

---

### Post by Carl Hamlin on 2010-02-17
> **Ferrat said:**
> are you sure it's not just a zombie or perhaps an orphan? (depending on how your program works)

I could see that if I was threading and failing to dump, but so far there's only the one thread to contend with.

Thanks, though!

---

### Post by Bachstelze on 2010-02-17
AFAIK, ^C sends SIGINT so it might not always terminate the process

---

