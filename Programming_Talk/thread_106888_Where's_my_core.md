---
title: "Where's my core?"
date: 2005-12-21
forum: Programming Talk
---

### Post by OakRand on 2005-12-21
Just installed 5.10 and I have to say it's feeling great. I big step up from Mandriva 2005.

But I'm having a problem with a program I've written. It's written in C and compiled with gcc 4.02 and flags -g -Wall -02.

I'm getting a Segmentation Fault but no core is being dumped.

Has anyone else had this problem or know how to force it to dump a core? It's a pain having to find the error without it.

---

### Post by sapo on 2005-12-21
hum.. now that you mention it.. i dont recall seeing a core file in ubuntu, btw.. never missed it :)

---

### Post by coredump on 2005-12-21
I havn't actually tried this on Ubuntu, but the general Linux command to set the maximum size of a core dump is 'ulimit'.  You'll find it documented in the 'bash' man page.  Try: 'ulimit -c unlimited' and then run your program again.

Do let us know if this works!

---

### Post by OakRand on 2005-12-21
Oh beauty. Thanks coredump.

I never thought I'd be so happy to see a 40MB core in my folder.

---

### Post by coredump on 2005-12-22
Glad to hear that it worked!  To see all of the various limits, try 'ulimit -a'.

Did the core file help you to pin down the bug in your code?

---

### Post by OakRand on 2005-12-22
Ya, I found the bug. Thanks again.

---

