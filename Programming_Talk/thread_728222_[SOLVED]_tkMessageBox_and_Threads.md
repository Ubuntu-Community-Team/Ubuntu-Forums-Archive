---
title: "[SOLVED] tkMessageBox and Threads"
date: 2008-03-18
forum: Programming Talk
---

### Post by themusicwave on 2008-03-18
I have an interesting and annoying problem.

I have a thread that is started when a user clicks a button in my TK GUI.  

I want to pop up a messageBox and prompt the user in that thread, however when I do all of python freezes.

When I say all of python freezes I mean all of it.  I have to kill the python process.  It totally locks up.

Anyone have this problem before?  I am guessing it is a thread issue??

---

### Post by kknd on 2008-03-19
[QUOTE=themusicwave;4540926
When I say all of python freezes I mean all of it.  I have to kill the python process.  It totally locks up.
[/QUOTE]

You can only do GUI stuff inside the main thread. Maybe Tk have some utility functions to do this.

---

### Post by themusicwave on 2008-03-19
That's what i figured..

Thanks for confirming it. I did manage to get to to work by poping up boxes only in the main thread.  I did some data piping between the main thread and the other threads and it works.

---

