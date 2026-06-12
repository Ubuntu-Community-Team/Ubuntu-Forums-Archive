---
title: "Ubuntu / gnome performance articles"
date: 2006-07-06
forum: Other OS Talk
---

### Post by viraptor on 2006-07-06
I've read some nice articles lately on Ben Maurer's blog - latest one is:
[http://bmaurer.blogspot.com/2006/07/today-in-performance.html](http://bmaurer.blogspot.com/2006/07/today-in-performance.html)
He tries to find many places of optimizing performance by little steps (missed chance for icon caching, late init of rarely used libs, etc.) It's a fascinating blog lately.

Thought that someone would be interested also :)
Get some news at [http://bmaurer.blogspot.com/](http://bmaurer.blogspot.com/)

---

### Post by FredB on 2006-07-06
Interesting article. But on my computer (P4-2.6 Ghz), I don't know if I ever will see more speed using those tips ;)

---

### Post by viraptor on 2006-07-06
Right, but you still load those progs (most of those proposals have effect on loading time and mem - not really responsivness, or 'speed'). And you still have ~20 of them running all the time.
Caching will always help you. For example bringing some background application from swap to active mem will always take less time, if it uses mmaping files shared with other apps, instead of rereading originals from disk.

Summing some of the estimates from previous articles (of progs that i'm running only) gives me >30MB... that's half of mem that firefox takes now (3 pages on). Maybe it's not much, but seeing that go wasted? It hurts :)

---

