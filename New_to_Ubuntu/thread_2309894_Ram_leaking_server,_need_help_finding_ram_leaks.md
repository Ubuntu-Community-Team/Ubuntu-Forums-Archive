---
title: "Ram leaking server, need help finding ram leaks"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by filmjolk_1 on 2016-01-14
Have been running a server for half a year now, but at some point it started leaking and I have been emptying the cache to bring it back to normal

Here is the ram usage over time and the swap.

[IMG]http://i.imgur.com/y4LIa9J.png[/IMG]
How can I track down what's causing the leak?

---

### Post by TheFu on 2016-01-14
This isn't the whole story. Unused RAM is a waste.  It gets used by the OS for file buffering. Those buffers are cleared as needed for processes.

Use the **free -m** cmd to see this. 
The **top** command will let you easily see which processes are using CPU/RAM ... but be certain to read and understand about the different RAM use columns. Some is shared memory by many different processes.

Unused RAM is a waste. Don't forget that.  My goal is to have as much RAM used as possible for anything the system needs without swapping, but no more.  On file servers, more RAM used for buffers is nice since it will speed up file transfers (RAM access is **MUCH** faster than disk).

BTW, without knowing what the workload for the "server" is, hard to provide any more clues. After all, something could be wrong, but restarting the major processes will clean up any RAM leaks.  After you've determined that something actually is leaking, you can use some developer tools (valgrind and strace come to mind) to dig into the processes, but those tools really aren't meant for non-developers to use.

---

