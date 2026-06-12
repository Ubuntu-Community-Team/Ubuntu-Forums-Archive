---
title: "SIGCHLD and waitpid"
date: 2007-09-17
forum: Programming Talk
---

### Post by DBQ on 2007-09-17
Hey everybody, 

   I have this situation.  Suppose you have a parent process which forked off a child.  Then suppose before the parent gets to the waitpid function the child terminates, and the parent changes the SIGCHLD handler from something to ie. signal(SIGCHLD, SIG_DFL).  When the parent finally gets to the waitpid, in my case, it says that there are no child processes.  BTW, the parent puts the child in the foreground as soon as it is forked off.  Any ideas?

---

### Post by the_unforgiven on 2007-09-17
> **DBQ said:**
> Hey everybody, 

   I have this situation.  Suppose you have a parent process which forked off a child.  Then suppose before the parent gets to the waitpid function the child terminates, and the parent changes the SIGCHLD handler from something to ie. signal(SIGCHLD, SIG_DFL).  When the parent finally gets to the waitpid, in my case, it says that there are no child processes.  BTW, the parent puts the child in the foreground as soon as it is forked off.  Any ideas?
May be, [this]("http://en.wikipedia.org/wiki/SIGCHLD") would help?

I would like to see your code - I think somewhere SIGCHLD is getting explicitly ignored causing it to NOT generate any zombie process that can be waited for.

---

