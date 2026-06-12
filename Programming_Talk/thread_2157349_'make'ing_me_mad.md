---
title: "'make'ing me mad"
date: 2013-06-25
forum: Programming Talk
---

### Post by IAMTubby on 2013-06-25
Hello,
This Makefile issue really gave me a tough time.

I was building the right files, but my changes were not getting reflected, until I did an **rm** to the target executable and then built it again.
I understand why this worked, and the concept of timestamps in Makefiles.

But is there a way to make sure this problem can be prevented? What if, I was building a huge project(this itself was a huge one, just that I was building only one executable)? It would be difficult to figure out which executable was "outdated", if I could use that word :)

Is the solution that you should always do a make clean first ?(In that case, this Makefile did not do a rm to this executable, giving me all the trouble)

Please advise.
Thanks.

---

### Post by r-senior on 2013-06-25
It sounds like your makefile is incorrect. You should be able to type make and it will reflect your changes (but no more than that) in the build. Deleting all the products defeats the object of using make -- imagine that on the Linux kernel source with ~15 million lines of code to recompile every time!

If you were working on a huge project, you'd probably use a build tool, e.g. GNU Autotools, rather than building the makefiles by hand.

---

### Post by spjackson on 2013-06-25
It sounds like the dependencies in your Makefile are incorrect. For example, if you have the following and b.c is newer than prog, prog will not be built because it is not declared to depend on b.c
```

prog: a.c
    gcc -o prog a.c b.c

```
You can get around this by using make -B (or make --always-make), but it would be better to fix the dependencies.


"make clean" does whatever the Makefile tells it to. Makefiles are sometimes written such that the clean target removes intermediate files, but not the top level targets (e.g. remove all the .o files but not
the linked executables).


You can also get into difficulties if the system clock changes while make is running, or if you are using a network file store (e.g. over NFS) and the relevant machines' clocks are out of synch. However, I would expect you to be getting further symptoms if this was your problem.

---

### Post by PaulM1985 on 2013-06-25
I have found the same issue recently. I'm also quite new to make files. I found online that it is possible to auto generate the dependencies. See here: [http://scottmcpeak.com/autodepend/autodepend.html](http://scottmcpeak.com/autodepend/autodepend.html). I haven't tried it yet myself but it is something I will be looking into when I get the time.

Good luck

Paul

---

