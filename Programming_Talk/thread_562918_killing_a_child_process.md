---
title: "killing a child process?"
date: 2007-09-29
forum: Programming Talk
---

### Post by Fixman on 2007-09-29
It is possible, if you are a parent process and have created a child process with fork(), to kill the child process?

---

### Post by DMills on 2007-09-29
Man 2 kill.

You have the pid from the call to fork, so just decide what signal you want to send and stick the appropriate value in the call to kill.

Regards, Dan.

---

