---
title: "python-profiler missing"
date: 2005-10-18
forum: Programming Talk
---

### Post by boobis on 2005-10-18
I'm trying to use the hotshot python profiler, but it fails, complaining that:

>>> import hotshot
>>> import hotshot.stats
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/hotshot/stats.py", line 3, in ?
    import profile
ImportError: No module named profile
>>>

I've seen this error around, but no working solution. The profile module is indeed missing and the python-profiler set of packages are not installable ...

What to do?

---

### Post by TimL on 2006-02-18
BUMP!

I've come across this problem too - I'm having trouble finding a .deb of python2.4-profiler.

I've found it on [packages.ubuntu.com]("http://packages.ubuntu.com/breezy/python/python2.4-profiler") and I'm sure I have all the repositories enabled, but I can't find it in synaptic...

Has anyone got any ideas?

Cheers,
Tim

---

### Post by ow50 on 2006-02-18
You need the python-profiler package and it's in multiverse.
[http://packages.ubuntu.com/breezy/python/python-profiler](http://packages.ubuntu.com/breezy/python/python-profiler)

When you have multiverse  properly enabled in your sources.list, it'll show up in Synaptic.

---

### Post by TimL on 2006-02-18
Yeah, I just found that I didn't have multiverse properly enabled. I saw it written in the backports line the sources list, but I didn't spot that it wasn't actually in my other sources.

Thanks

---

### Post by boobis on 2006-02-20
Since I don't have multiverse enabled I guess this will solve my issue to. Thanks mate!

---

### Post by ow50 on 2006-02-20
Just to note, the reason for python-profiler being in multiverse:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=293932](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=293932)

---

