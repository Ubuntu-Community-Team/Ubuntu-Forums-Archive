---
title: "Freeing up RAM"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by sayakb on 2008-04-30
Hello all,
I have observed that after exiting virtualBox, my RAM usage goes down from 50% to 15%. So I want to create a launcher/execute a command at a terminal to clear up my RAM. Does someone have any idea in this context? 

Dave

---

### Post by skymera on 2008-04-30
I don't have a command, sorry.

But im interested in freeing up RAM too, seems to be minor OCD :lol:

---

### Post by stijngysemans on 2008-04-30
Isn't that just the normal behavior? Virtualbox will allocated a fixed percentage of your memory on star-up. When it clooses, it will free that ram? I don't understand the question.

---

### Post by sayakb on 2008-05-01
My question is that if VirtualBox can do it, can't it be done separately thru the CLI?

---

### Post by Joeb454 on 2008-05-01
I don't think so. I think it's just that Virtual Box had the memory set aside for it by the OS, and that now VBox has been closed, the OS has freed the RAM.

From what I've learnt (at Uni - Computer Science :)) The OS handles what RAM is given to what. But applications can dynamically access the memory for variables if you need them to etc.

---

### Post by sayakb on 2008-05-01
So we might need to close the program and it's libraries to free up the space. I remember trying that too. I had about 20% RAM usage until I opened firefox, it rose up to 21. But even after I killed firefox-bin, the RAM remained at 21%.. Why does that happen, since I couldn't find other firefox processes running..

---

### Post by mivo on 2008-05-01
Are you sure that it's not only disk caching? Linux's memory management is different from how Windows handles RAM. [This article]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management") may shed a bit of light on how Linux uses memory. :)

---

