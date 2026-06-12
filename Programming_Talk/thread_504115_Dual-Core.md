---
title: "Dual-Core"
date: 2007-07-18
forum: Programming Talk
---

### Post by Sockerdrickan on 2007-07-18
How do I take advantage of the dual-core when programming in C++?
Would someone show me an (as simple as it can get) example of how to achive this? :)
Going to make a 3D game and need horsepower.

---

### Post by crashie on 2007-07-18
You need to create a multithreaded program. For example, if you're creating a game you can use an extra thread for networking, or one for loading stuff from disk in advance (for example maps), etc.

**If you're new to programming you should NOT start with threading.** Threading is hard, you need to do synchronization between your threads because they can't use the same data (variables) at the same time, and you must check that all code (libraries etc.) you use is thread-safe and that you use it in a thread safe way.

You can use the Boost library to get threading in your program:
_[Getting started with Boost]("http://www.boost.org/more/getting_started/index.html")_
_[Boost.Thread]("http://www.boost.org/doc/html/thread.html")_

Or you can use _[SDL]("http://www.libsdl.org/")_ for threading. I don't know which one is better because I've only done threading in C with pthreads.

Btw, I'm just guessing, are you coding an entry for the intel challenge? :)

---

### Post by Sockerdrickan on 2007-07-18
I just learnt SDL so that would be cool!

No I'm not actually hehe :) This project will take longer time...

---

