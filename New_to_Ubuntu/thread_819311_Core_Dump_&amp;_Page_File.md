---
title: "Core Dump &amp; Page File"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-05
1) --> Is there any package available for analysing Core dumps.

2) --> Is there any way to extract page file of a particular time to view it.

---

### Post by Cypher on 2008-06-05
Core dumps are usually analyzed with GDB.
```

gdb <executable> <core>

```
Depending on how the executable was made, you might get source or just assembly..

As far as page file goes, I'm going to guess no..

P.S., Kamal Haasan is awesome..;)

---

### Post by rraj.be on 2008-06-05
Ok i will try GDM for my core dump analysis.

Is there any kernal level command that i can invoke to extract or analysis my page file.

I am not woried about invoking any kernal or base level commands.

so you can sugest me any commands.

And further i am big fan of Mr.Dr.Kamal Hasan [not regarding his cine life but regarding his personal life and talents]

Is that Great man famous in Us too.

Much happy to hear if so.

---

