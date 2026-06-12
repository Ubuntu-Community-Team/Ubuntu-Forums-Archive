---
title: "Any languages similar to python?"
date: 2006-12-12
forum: Programming Talk
---

### Post by ironfistchamp on 2006-12-12
Hey all


I have a question not about how to do something but about alternatives. I love Python but I would like it to be faster. Also not having to use an interpreter (for distrobution purposes) would be very useful. Does anyone know of similar languages (i.e. similar syntax(e.g. no bloody semi-colons, indendation and so on)).

Some people may want to know why I want this. There are 3 reasons.

1) Because I would like that extra speed if necessary. You never know I may get into graphically intensive programs and things that would need power and speed close to C++
2) I would like to use C++ but I hate the syntax. It is cluttered and confusing. 
3) Because I am just curious. It is a question I have seen re-hashed over the net but not here (to my knowledge). Just wondered what you guys would say on the matter.


Thanks

Ironfistchamp

---

### Post by angustia on 2006-12-12
python + pyrex (first learn python, then learn python C API, and then learn pyrex)

you can embed the python interpreter within the program (for Win, there's something called py2exe)

with this you have:

- the C speed where needed (you can embed ASM code inside the C code even)
- no need to use C++, just C
- better crash reports (at least the interpreter gives you better crash reports)

there's something not so great about python and threads: on multiprocessors, the interpreter uses only one of the cpu's at time, but inside your C modules you can spawn private threads that don't suffer this limitation.

---

### Post by ironfistchamp on 2006-12-12
Thanks for the reply. I assume though that I will still be limited to using the C syntax correct. From my observations this is just as cluttered as C++ which is the main problem with it. That is the one reason I use Python above anything else.

Thanks

Ironfistchamp

---

### Post by gummibaerchen on 2006-12-12
I think thinks like psyco or later pypy speed python up a lot.

---

### Post by pmasiar on 2006-12-12
Speed is not a problem until it is a problem.

*Then* you reimplement bottleneck - 5% of the code.

Or upgrade to a faster processor. :-)

---

### Post by ironfistchamp on 2006-12-12
Thanks for your input guys. I am going to research Pythons speed a little more actually.

Thanks again

Ironfistchamp

---

### Post by pmasiar on 2006-12-12
Couple of this forum threads in last 3 days touched issue of python execution speed (and other popular myths about python): 

[LIST]
[*][Python or Ruby?]("http://ubuntuforums.org/showthread.php?t=308831") 
[*][Comparing C++ to Python]("http://ubuntuforums.org/showthread.php?t=316601")
[*][good language to make game]("http://ubuntuforums.org/showthread.php?t=315557")
[*][Best crossplatform programming language]("http://ubuntuforums.org/showthread.php?t=314348")
[/LIST]

If you have more questions, ask here or in new thread :-)

---

### Post by angustia on 2006-12-12
> **ironfistchamp said:**
> Thanks for the reply. I assume though that I will still be limited to using the C syntax correct. From my observations this is just as cluttered as C++ which is the main problem with it. That is the one reason I use Python above anything else.


take a look at pyrex again...

---

