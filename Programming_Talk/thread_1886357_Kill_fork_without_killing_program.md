---
title: "Kill fork without killing program"
date: 2011-11-24
forum: Programming Talk
---

### Post by cmwarre on 2011-11-24
hello all,
  I'm currently working on a multi process server program and I'm having some issues shutting down a fork...  Whenever I call kill(pid, SIGKILL), I am getting an error from my socket saying ERROR on accept: Interrupted system call.  Any ideas?

I can attach the program if you need it but it's getting quite large... haha

---

### Post by ziekfiguur on 2011-11-26
Why are you using an hard kill, why don't you try SIGTERM first?

I can't be sure about the answer to your question, but do you open the socket before you fork the program? if so, do you close it in the fork?
When you fork a program all file descriptors are copied to the fork, so they both have access to the same socket, I'm not sure what happens to the other if you kill one of them.

---

