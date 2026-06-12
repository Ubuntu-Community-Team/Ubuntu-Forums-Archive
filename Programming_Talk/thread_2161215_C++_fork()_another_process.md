---
title: "C++ fork() another process?"
date: 2013-07-09
forum: Programming Talk
---

### Post by XtrmJosh on 2013-07-09
I'm trying to read the memory of a process which I have no real access to. The process is a game, and I want to find values within its memory. I'm currently using ptrace, but it pauses the game, so I'm looking to fork the process, ptrace it, then unfork it (if that's a thing!)

I'm reading memory just fine, just can't work out how to fork using a PID.

Can anyone advise?

Kind regards

---

### Post by Tony Flury on 2013-07-11
What do you mean "fork using a pid".

Fork creates a brand new process - it sounds like you want to attach somehow to an already running process.

Also not sure what you mean by "unfork" - do you mean kill the process - or do you mean detach from it ?

---

### Post by XtrmJosh on 2013-07-11
> **Tony Flury said:**
> What do you mean "fork using a pid".

Fork creates a brand new process - it sounds like you want to attach somehow to an already running process.

Also not sure what you mean by "unfork" - do you mean kill the process - or do you mean detach from it ?

I want to read a processes memory without interrupting the process. Currently, when using ptrace I'm forced to freeze the process whilst reading. I was hoping to duplicate the external process which I'm trying to read, read from the dupe, then dispose of it. Is there any better way you could advise to do this? Or even just to read memory without freezing the process?

---

