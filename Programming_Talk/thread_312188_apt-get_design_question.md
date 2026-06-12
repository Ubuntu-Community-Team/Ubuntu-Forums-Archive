---
title: "apt-get design question"
date: 2006-12-04
forum: Programming Talk
---

### Post by gmatt on 2006-12-04
I've always wondered why apt-get never allows more than one application to use it at a time. It seems kind of a waste since if two operations don't affect each other, then they should be allowed to run in parallel. I'm pretty sure apt-get is a C library, and so obviously written in C, but what I don't understand is why the file locking mechanisms aren't implemented to lock only sections of the file(s) at a time, so that users can have more control. 

By the way, I'm writing this while I'm waiting for apt-get to finish downloading 50mb at 20kb/s when I want to install some more programs through apt-get that are much smaller, doh!

---

### Post by engla on 2006-12-04
Interesting question. It could be implemented so that there is a daemon that does the job (like now), and that subsequent requests just push them into a queue. The problem is, you can do really advanced things with apt-get (and the like) and once you get into nested dependencies and conflicts that won't work so well.. or will it? It could store a snapshot of what the database would look like between all the steps.

---

### Post by gmatt on 2006-12-05
> **engla said:**
> Interesting question. It could be implemented so that there is a daemon that does the job (like now), and that subsequent requests just push them into a queue. The problem is, you can do really advanced things with apt-get (and the like) and once you get into nested dependencies and conflicts that won't work so well.. or will it? It could store a snapshot of what the database would look like between all the steps.

Yea, you brought up an important point, all apt-get really is is a fancy database. I know databases by design allow multiple operations that do not conflict to run at once. 

I don't expect this question to be answered by an actual dev of apt-get, but it'd be cool if I could maybe get a ubuntu dev's opinion on this. 

I think its entirely possible to let apt-get do parallel operations, and kind of a nice improvement in the future if it was ever implemented (perhaps by me haha!)

---

