---
title: "What!!!!!"
date: 2009-11-11
forum: Programming Talk
---

### Post by Anonymouse.squeek on 2009-11-11
More use to solaris but last night started playing with Berkley sockets on my recently installed ubuntu machine using codelite and Gcc. After creating a socket and destroying it, when I wrote to the now defunct socket the machine hanged up?!?!?!?!! don't know if it was just the KB and mouse, but the soft power switch wasn't working either. How is that possible? not even windows 98SE is that unstable. Solaris would have just core dumped, hpux nullified the illigal pointer. Anyone know whats going on and how I can stop my machine from going down when I'm developing?

---

### Post by dwhitney67 on 2009-11-11
You're machine failed for a reason not related to your use of the socket.

---

### Post by Anonymouse.squeek on 2009-11-12
;) Anythings possible but strangely coincidental that it only happens when I'm working on that socket program, the rest of the time its rock solid........ Maybe I should create a project that does it deliberatly, then upload it to here so people can have a try themselfs

---

### Post by dwhitney67 on 2009-11-12
> **Anonymouse.squeek said:**
> ;) Anythings possible but strangely coincidental that it only happens when I'm working on that socket program, the rest of the time its rock solid........ Maybe I should create a project that does it deliberatly, then upload it to here so people can have a try themselfs

That's a great idea!

---

### Post by CptPicard on 2009-11-12
How much are you willing to bet on it being caused by the Linux kernel's socket API? I might want to take the other side :)

---

