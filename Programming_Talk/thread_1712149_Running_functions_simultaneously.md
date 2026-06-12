---
title: "Running functions simultaneously"
date: 2011-03-22
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-03-22
Hello there,

I'm still a beginner at programming and i am wondering about one thing (which i haven't yet come across anywhere): is it possible to run several functions or methods simultaneously. So far i believe i have seen various functions in a single program run in series, once a function comes to an end, another may start.

For instance, imagine a chronometric program that counts seconds on start/stop, this program should be able to run several counters simultaneously.

How to achieve this?

Cheers,
Benjamin

---

### Post by andrew1992 on 2011-03-22
[http://en.wikipedia.org/wiki/Thread_(computer_science](http://en.wikipedia.org/wiki/Thread_(computer_science))

---

### Post by Arndt on 2011-03-22
> **andrew1992 said:**
> [http://en.wikipedia.org/wiki/Thread_(computer_science](http://en.wikipedia.org/wiki/Thread_(computer_science))

I haven't looked at this page, and it probably gives pointers to other related concepts, but I'll mention a few anyway: Apart from threads (which run in the same process), you can run several processes at the same time and have them communicate in various ways (pipes, sockets, shared memory, messages, etc.). There are also programming languages which implement their own process-local scheduling, which could be called threads, but which doesn't use the system's thread library. Erlang is one such language.

Sequencing and coprocesses are two words used in this area, but they may have been superseded by other words/concepts.

---

### Post by andrew1992 on 2011-03-22
Yes multiple processes could be used as well. :)

---

