---
title: "Quick Make question"
date: 2005-04-27
forum: Programming Talk
---

### Post by oddabe19 on 2005-04-27
So, here's my question....

i download a source tarbal for program XXXXXXX.
I unpack it
run autoconf
./configure
then I do this
```
oddabel@ubuntu:~ $ make CFLAGS="-march=athlon-xp -pipe -O2"
```

i was wondering if that actually did anything.... the display looks like it adds it in, but i was almost certain that i had to do a gcc programx file.c with the optimizations for anything to be optimized.

So, long story short, did that make cflags actually do anything to help with optimizations?

if it does, is there a file i can edit (an equivalent to /etc/make.conf in gentoo) to bring those optimization on every program i compile?

---

### Post by vague- on 2005-04-28
Well, it really depends on the makefile of the project.  If it is autotools, it should have dealt with it properly.  There are a few variables that should be there, so in the general case what you did should have made a difference.

A cursory glance over the make info documentation did not seem to name any files where you can set these values.  However, you could probably alias the make command to include them.  I'll have another look about and post here if I do find a file.  Alternatively, you could patch make.

---

