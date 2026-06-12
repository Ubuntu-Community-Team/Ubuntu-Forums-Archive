---
title: "Multicore programming?"
date: 2008-03-28
forum: Programming Talk
---

### Post by t.s on 2008-03-28
(I just copy-paste this article from [www.hardspell.com/english/](www.hardspell.com/english/) which they get From theinquirer.)
[COLOR="Navy"]
**Microsoft and Intel finally team up on multi-core programming**
Date: 2008-3-18
Author: Rocky

WALL STREET JOURNAL reader Mike Magee says Microsoft and Intel are expected to announce a joint research project to engage in programming for multicore processors.

The research and development of the multicore programming project will purportedly be carried out by boffins from the University of California, Berkeley, where the Vole and Intel are funding a laboratory for research into parallel computing.

The lab would let researchers imitate 1000 core systems and could cost a cool $2 million a year for the next five years, the Journal learned today and the rest of us will learn later on.

The materialisation of processors with two or more cores has led to many calls for more research into bettering a devices processing ability using less power. The research hopes to lead the way in the scuttle to defining parallel programming models able to serve multicore computer processors which are already in the pipeline.

Multiple processing units have, in the past, proven to be a significant stumbling block to both hardware and software providers, because without optimal programming, applications dont profit from added chip power, and in some cases can even become slower because of it.

The boffins will centre their research on attempting to set up development frameworks to facilitate dispersing computing jobs to be done in parallel by processors with multiple cores. They will also attempt to build parallel programs which use a more flexible set of standard modules, which would be dynamic enough to set up parallel tasks from the actual modules across available hardware in complex heterogeneous multi-core CPUs.

Intellivole will host a teleconference later today to confirm the Journals story.[/COLOR]

Have we has to follow their footstep? I mean, on linux in general, providing a better *whatever* for taking advantages on multi-core world, like just now?
or, we already have it?

---

### Post by scourge on 2008-03-28
> Have we has to follow their footstep?

It's more like they are following our footsteps. Linux has been the dominant multi-cpu (super computers, render farms, etc.) OS for a long time.

---

### Post by bruce89 on 2008-03-28
OpenMP and GOMP comes to mind.

---

### Post by slavik on 2008-03-28
> **bruce89 said:**
> OpenMP and GOMP comes to mind.

then there is MPI and MOSIX2 ...

---

### Post by t.s on 2008-04-03
thanks for the input...
I've heard about this (open multicore programming) before, but I'm not that sure about that...
now I'm reading about OpenMP on wikipedia...

but still, will their project be more easy to implement, to use to build a framework etc..
hehe.. just curious

thanks, everyone. Now i can feel more confident using linux (and, if I want to coding on linux--on the future)

---

