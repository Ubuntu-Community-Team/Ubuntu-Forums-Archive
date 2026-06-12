---
title: "How to execute external program inside app and return program's output ..."
date: 2012-10-26
forum: Programming Talk
---

### Post by rdzurney on 2012-10-26
Inside of an application, I'm trying to execute a shell app and then get the output from that shell app back into my application (not the return value of the shell app).  The "system" call does not seem to do this and I can't use exec.  Thanks in advance for all replies.

---

### Post by spjackson on 2012-10-26
I don't know what language you are using for your application, but for many languages, popen might be what you  want.

---

### Post by rdzurney on 2012-10-29
Thanks for the info.  Looks like that's what I need.

---

