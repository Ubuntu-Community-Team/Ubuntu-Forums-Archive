---
title: "compileation error: No space left on device"
date: 2009-07-03
forum: Programming Talk
---

### Post by flylehe on 2009-07-03
Hi,
I am compiling my C++ program with g++ on a server and receive out of space error:
> 
count.cc:76: fatal error: error writing to /tmp/cckf2zK1.s: No space left on device
compilation terminated.
...

Does it mean that the usage in /tmp is full? Is this problem for the whole server or only for my account? What can I do to free up space so that I can compile my program?
Thanks and regards!

---

### Post by monraaf on 2009-07-03
How about giving the -pipe switch to g++?

---

### Post by flylehe on 2009-07-03
How to give the -pipe switch to g++? What does it mean? Thanks!

---

### Post by monraaf on 2009-07-03
It means exactly what it says ;) Use pipes instead of temporary files. You might still get into trouble during linking though, so see if there's some junk in /tmp that you can rm.

g++ -pipe ....

Or add it to the Makefile CFLAGS/ CPPFLAGS or whatever you are using.

---

### Post by flylehe on 2009-07-03
It works. Thanks!

---

### Post by soltanis on 2009-07-03
Also consider cleaning out the /tmp directory or rebooting.

---

