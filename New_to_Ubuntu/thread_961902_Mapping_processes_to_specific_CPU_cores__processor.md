---
title: "Mapping processes to specific CPU cores / processors"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by pteri498 on 2008-10-28
I use VirtualBox for XP within Ubuntu. I have a dual-core processor, and it pleases me to see that one core seems dedicated to the process of powering the virtual machine, but I'm concerned that other processes might be making use of that processor, too.

Is there a way I can specifically map a process to one of my cores so I can leave the other core wide open for the virtual machine?

Thanks.

---

### Post by aeiah on 2008-10-28
not in a convenient manner, no. not that i know of anyway although im no expert. take comfort in the fact that linux isnt stupid though. if you have xp on the 2nd core and its using 80%, and your first core is only using 6%, then ubuntu will predominantly use the first core.

---

### Post by pteri498 on 2008-10-28
Yeah, that's basically what's happening. VirtualBox is chugging away at 100% of my second core, but I just want to make sure that the full 1.6Ghz available on that core goes directly to VirtualBox, and not to another process that may be using the same resources.

---

