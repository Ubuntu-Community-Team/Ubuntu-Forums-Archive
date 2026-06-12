---
title: "Everything catches Segfault. Except Debugger."
date: 2010-06-09
forum: Programming Talk
---

### Post by nrs on 2010-06-09
I have minimal GDB / debugging knowledge in general. Just enough to make it work and and fix crashes. I'm having a problem I've never encountered before though: I have a program which reproducibly and consistently segfaults, but when run in GDB to detect the error, it doesn't segfault and exits noramlly. I'm having a hard time wrapping my mind around this. 

Can't post code ATM and obviously don't expect anyone to fix the problem. I'm just wondering if anyone could shed light on how such a thing could happen.

---

### Post by DanielWaterworth on 2010-06-09
If I understand you right, it segfaults except when you run it under gdb. In that case you can debug the old fashioned way, with lots of 'printf's [=

---

### Post by Tony Flury on 2010-06-09
Problems like that are either indicative of :
1) Race conditions - i.e. threaded code where the act of using the debugger changes the order the threads run.
2) Stack/Memory corruption issues - which aren't caught by the debugger as it changes the memory layout of the processes.

Have you used Valgrnd to look for memory corruptions.

You may find that if it is a race condition problem, that putting in printf's changes the nature of the problem - or even makes it dissapear - they can be nasty to find.

---

### Post by nrs on 2010-06-09
> **DanielWaterworth said:**
> If I understand you right, it segfaults except when you run it under gdb. In that case you can debug the old fashioned way, with lots of 'printf's [=
Yeah, that's what I figured. The main question is how could something conceivably crash in every scenario, yet run without incident in the debugger? 

i just don't understand it.

---

### Post by DanielWaterworth on 2010-06-09
Are you using threads? Race conditions are something I forgot about and would be a good thing to rule out.

---

### Post by nrs on 2010-06-09
> **Tony Flury said:**
> Problems like that are either indicative of :
1) Race conditions - i.e. threaded code where the act of using the debugger changes the order the threads run.
2) Stack/Memory corruption issues - which aren't caught by the debugger as it changes the memory layout of the processes.

Have you used Valgrnd to look for memory corruptions.

You may find that if it is a race condition problem, that putting in printf's changes the nature of the problem - or even makes it dissapear - they can be nasty to find.
i actually traced the problem to glTexImage2D / the image I was using, so #2 is almost certainly the problem. Since the OP i've fixed it.

I was just interested in how the debugger of all things could miss it and exit normally. This explains it to some extent.

---

### Post by nrs on 2010-06-09
> **DanielWaterworth said:**
> Are you using threads? Race conditions are something I forgot about and would be a good thing to rule out.
Nope. At least not on my own end. I haven't had the misfortune of dealing with race conditions yet. :)

---

