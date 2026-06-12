---
title: "valgrind problem"
date: 2015-06-29
forum: Programming Talk
---

### Post by mark allyn on 2015-06-29
Hello everyone,

I installed valgrind on a 14.04 ubuntu box.  I removed a previous version using apt-get remove --purge command.  The new installation appears to be correct.  The man page is there.  And, "which valgrind" command shows that the executable is located in /usr/local/bin and cd'ing to that directory and doing a "ls -ail valgrind" shows that it is an executable and appears to have a large number of bytes.    I wrote a trivial c program (nu.c) and it runs without a problem. However, when I issue the command "valgrind ./nu" , I immediately get a seg fault.  In fact, if I just type "valgrind" I get a seg fault.

Ideas?

Thanks,
Mark Allyn

---

### Post by mark allyn on 2015-06-29
Hello everyone,

Fixed it by ripping out all the valgrind files in /usr/bin, /usr/lib, /usr/include, /usr/local/bin, and /usr/local/lib.  Downloaded a fresh .deb doing usual sudo apt-get valgrind.  The new install works as expected.  BTW, the executable is located in /usr/bin not /usr/local/bin.  I point this out, because in some of the google research various authors claim it should be /usr/local/bin.  I can tell you from bitter experience that if it's there, it will crash.

Mark Allyn

---

