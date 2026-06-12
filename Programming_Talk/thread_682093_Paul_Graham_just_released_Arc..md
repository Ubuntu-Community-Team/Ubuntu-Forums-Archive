---
title: "Paul Graham just released Arc."
date: 2008-01-29
forum: Programming Talk
---

### Post by a9bejo on 2008-01-29
[http://paulgraham.com/arc0.html](http://paulgraham.com/arc0.html)

[http://arclanguage.org/](http://arclanguage.org/)

[http://reddit.com/r/programming/info/6710p/comments/](http://reddit.com/r/programming/info/6710p/comments/)

With Paul Graham and all his fans pushing it, maybe this could be the hype in computer languages in 2008?

**Update:** "Arc only supports Ascii" => ](*,)

---

### Post by lnostdal on 2008-01-30
> **a9bejo said:**
> **Update:** "Arc only supports Ascii" => ](*,)

mh, well .. read it in context .. i'm guessing it sort of underlines a point they are trying to make .. especially note what is mentioned about "form and content in web pages" .. now, how can this be?

remember that unicode characters ultimately only consist of bytes, or "ascii" at the base ---> bottom-up-programming ---> no border between language (arc) and library (some unicode library) ---> unicode support in arc .. no? 

edit: it turns out this is not the case actually .. but, it could have been :)

but, interesting .. i will have to take a look later, ty

---

### Post by moma on 2008-01-30
Hello,

Can it compile to and run on Parrot Virtual Machine?
See: [http://www.parrotcode.org](http://www.parrotcode.org)
Many languages already support [Parrot VM..]("http://www.parrotcode.org/languages/").

---

### Post by pmasiar on 2008-01-30
> **moma said:**
> Many languages already support Parrot VM.

IMHO it is other way around: Parrot is able to run couple languages, but AFAIK the only language which **relies** on Parrot is Perl6. All other languages developed their own VMs, optimized for theer own purposes, and I doubt they will switch to Parrot. Why would they? Will Parrot run Python or Ruby code faster than dedicated VM?

Or do you have different information? Is there any language which plans to abandon VM they have and use Parrot instead? Any links?

ie interesting development in Python VMs, that beside original C Python, JVM based Jython and .NET based IronPython, there is 4th VM: PyPy, Python in Python: Python VM written in (rpython - type aware subset of) Python.

And developers say PyPy allows them experiment with different implementation of features in Python instead of C, and optimize them for speed in Python, which gains are then effortlessly transformed for final user.

So I certainly do not see point in switching to Parrot, when CPython runs strong and PyPy is almost usable.

---

### Post by lnostdal on 2008-01-30
meh .. we lacked portability (edit: and/or the ability to communicate on a "language neutral level") between architectures and machines .. then came the virtual portable machine, and the problem was solved .. but then came more virtual portable machines, and we're back to where we started .. x)

---

### Post by Wybiral on 2008-01-30
> **pmasiar said:**
> And developers say PyPy allows them experiment with different implementation of features in Python instead of C, and optimize them for speed in Python, which gains are then effortlessly transformed for final user.

So I certainly do not see point in switching to Parrot, when CPython runs strong and PyPy is almost usable.

Actually, I watched a [Google Tech Talk]("http://video.google.com/videoplay?docid=1906120035435953529") by some of the PyPy developers where they explained quite a bit about it. Before, I thought PyPy was just Python implemented in Python, but it turns out it's actually Python implemented in Python with the purpose of being compiled into anything. The goal seems to be to design a framework(?) for designing new custom Python interpreter implementations with interesting perks (such as JIT compilation, custom GC implementation, etc). An implementation of Python with runtime profiling and JIT compilation sounds like a pretty sweet deal, IMO.

---

### Post by Tuna-Fish on 2008-01-30
> **Wybiral said:**
> Actually, I watched a [Google Tech Talk]("http://video.google.com/videoplay?docid=1906120035435953529") by some of the PyPy developers where they explained quite a bit about it. Before, I thought PyPy was just Python implemented in Python, but it turns out it's actually Python implemented in Python with the purpose of being compiled into anything. The goal seems to be to design a framework(?) for designing new custom Python interpreter implementations with interesting perks (such as JIT compilation, custom GC implementation, etc). An implementation of Python with runtime profiling and JIT compilation sounds like a pretty sweet deal, IMO.

Also, it is not spesifically limited to python; you can use it for other languages without that much more work.

---

