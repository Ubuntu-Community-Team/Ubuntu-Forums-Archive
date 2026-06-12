---
title: "minix system calls"
date: 2013-05-06
forum: Programming Talk
---

### Post by mixalisjoe on 2013-05-06
Hello, maybe the wrong place to ask, but let's try..
I want to edit a system call that already exists in minix, let's say the chown
system call.. Do you know which files i have to edit? and which of them need compiling?

---

### Post by MG&amp;TL on 2013-05-06
From [http://en.wikipedia.org/wiki/System_call](http://en.wikipedia.org/wiki/System_call): 

> In [computing]("http://en.wikipedia.org/wiki/Computing"), a **system call** is how a program requests a service from an [operating system]("http://en.wikipedia.org/wiki/Operating_system")'s ***[kernel]("http://en.wikipedia.org/wiki/Kernel_%28computing%29")***.

You'll need to find where the minix *kernel* implements system calls, or alternatively find a way to modify that part of the kernel dynamically (see the next post) I would suggest that changing something that fundamental is a bad idea though...

---

### Post by trent.josephsen on 2013-05-06
Not necessarily. In Linux, it's possible to edit the dispatch table and redirect existing syscalls to your own functions. [Here's](https://bbs.archlinux.org/viewtopic.php?id=139406) a forum post I read a few weeks ago on the subject. Interesting stuff. I wouldn't have thought it possible without at least recompiling the kernel, but that just shows how much I know.

Of course, that says nothing about Minix. I don't even know if Minix uses such a table, but if it does, that would be a good place to start. Either way, though, there's a good chance you will break something, so don't do this on a system you care about, etc.

---

### Post by MG&amp;TL on 2013-05-06
> **trent.josephsen said:**
> Not necessarily. In Linux, it's possible to edit the dispatch table and redirect existing syscalls to your own functions.

That's awesome! I stand corrected (although still no idea about Minix).

---

