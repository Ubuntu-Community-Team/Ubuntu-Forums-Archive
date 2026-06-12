---
title: "Proplem with Make anjuta-2.32.0.0"
date: 2010-10-09
forum: Programming Talk
---

### Post by Black Spider on 2010-10-09
Hi

basically  i have downloaded anjuta v2.32.0.0 from it's website and I have read installation guide it Say's *cd* to  anjuta folder then write [I]make.
[/I]
i did that but i always got error  *make: *** No targets specified and no makefile found.  Stop.*

can any one help ?

thaks

---

### Post by spjackson on 2010-10-09
> **Black Spider said:**
> 
basically  i have downloaded anjuta v2.32.0.0 from it's website and I have read installation guide it Say's *cd* to  anjuta folder then write [I]make.
[/I]
i did that but i always got error  *make: *** No targets specified and no makefile found.  Stop.*

can any one help ?

Is there a reason why you are not installing the binary package from the repositories?

That message from make tells you that there is no makefile. Running ./configure is the step that is needed to create the makefile; both the INSTALL and README text files tell you to run ./configure. Did you do this? The fact that you have no makefile indicates that either you didn't run ./configure or that ./configure failed.

If ./configure has failed, it will tell you why it failed. If it isn't clear to you, then please post the output of ./configure.

---

