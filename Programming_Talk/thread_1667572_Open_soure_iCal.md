---
title: "Open soure iCal?"
date: 2011-01-15
forum: Programming Talk
---

### Post by MiXor on 2011-01-15
Hi everyone,

I would like to develop an open source calendar for an association, and I don't know where to start! Help! :) (I have programmed before, but it was always for physics, so I don't know much about real world programming)
Many heaps of thanks!:KS

Aline

---

### Post by ssam on 2011-01-15
are you after something like this?
[http://en.wikipedia.org/wiki/DAViCal](http://en.wikipedia.org/wiki/DAViCal)

---

### Post by Some Penguin on 2011-01-15
If you wish to design something, it's likely best to first write an overview of your requirements.  These will include

* things that you /will/ support immediately,
* things that you won't support immediately, but may/will in the future, and therefore shouldn't design in such a way as to make them unnecessarily difficult
* things that might seem interesting and possibly obvious but that have explicitly decided that you won't do, so you don't waste time overengineering

Then you need to translate from functionality requirements to things like what data will you need, how to organize it, in what ways you can manipulate it -- and how you'll test whether or not it actually fulfills what you want it to do.  The organization may go down to determining APIs -- e.g. what function calls your storage layer needs to support, and how users' clients interact with your system.

---

