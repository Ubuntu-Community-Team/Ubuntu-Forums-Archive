---
title: "[python/c/c++] Meaningless question but still..."
date: 2011-06-20
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-20
I know its an idiotic question...but is thre any way we can execute two statements at the same time????

like in c++   a=5; b=8; are two statements which execute in order is thre any way to execute these statements at the same time....](*,):lolflag:

---

### Post by schauerlich on 2011-06-20
Not without forking the process or spawning a new thread, but I have a feeling that's not what you really want. What issue inspired this question?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-20
curiousness.... :)

---

### Post by NovaAesa on 2011-06-20
I know you haven't said it in your question, but "Python" is in the tag so I'll bite.

In python, you are able to do something such as
```

>>> x = 2
>>> y = 3
>>> x, y = y + 1, x + 1
>>> x
4
>>> y
3
>>> 

```
Now while it appears that the assignment statement is doing 2 assignments at once, it's really only syntactic sugar for a process that is occurring in sequence.

---

### Post by slooksterpsv on 2011-06-20
Technically in python you could do:

x, y = 5, 3

but that would still do x first then y next.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-20
> **NovaAesa said:**
> I know you haven't said it in your question, but "Python" is in the tag so I'll bite.

In python, you are able to do something such as
```

>>> x = 2
>>> y = 3
>>> x, y = y + 1, x + 1
>>> x
4
>>> y
3
>>> 

```Now while it appears that the assignment statement is doing 2 assignments at once, it's really only syntactic sugar for a process that is occurring in sequence.
how does that work???? i mean assignments....and how did u know that??

---

### Post by NovaAesa on 2011-06-20
> **Dhiraj Thakur(Invincible) said:**
> how does that work???? i mean assignments....and how did u know that??
All of the right hand side parts are calculated using the values of the variables before the assignment statement. Those values are stored as they are calculated, but they aren't stored into the left hand side, they are stored in temporary variables. Once all the right hands sides have been evaluated, the stored values are assigned to the left hand sides. It doesn't just work with 2 parts on the LHS and RHS, it can work with an arbitrary number of parts.

How did I know this? It's all there in the tutorials and language references in the official Python website.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-20
> **NovaAesa said:**
> All of the right hand side parts are calculated using the values of the variables before the assignment statement. Those values are stored as they are calculated, but they aren't stored into the left hand side, they are stored in temporary variables. Once all the right hands sides have been evaluated, the stored values are assigned to the left hand sides. It doesn't just work with 2 parts on the LHS and RHS, it can work with an arbitrary number of parts.

How did I know this? It's all there in the tutorials and language references in the official Python website.
thanks fr help...

---

### Post by ziekfiguur on 2011-06-20
With assignments this is, as far as i know, not possible. But modern intel processors offer MMX and SSE instruction sets which allow several arithmetric instructions to be executed at the same time, video cards can also be used to do this. The drawback is that most programming languages don't offer direct support for this, though you could use inline assembly in C/C++

---

