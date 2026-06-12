---
title: "[SOLVED] Porting cPickle to Lisp"
date: 2008-05-11
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-05-11
Gents,

I need to port cPickle into Lisp - Has anybody got the sourcecode for the pickle.load() or an overview of how it parses files?


/Lau

---

### Post by Jessehk on 2008-05-11
On my system, the pickle module (pickle.py) 
is located at /usr/lib/python2.5/pickle.py .

That is of course the Python version, not the C version.

---

### Post by Lau_of_DK on 2008-05-11
> **Jessehk said:**
> On my system, the pickle module (pickle.py) 
is located at /usr/lib/python2.5/pickle.py .

That is of course the Python version, not the C version.

That might be of some help, although I dont read Python just yet. The cPickle would be preferred, but thanks thus far :)


/Lau

---

### Post by Smygis on 2008-05-11
The internets rule! You can google and browse SVN!
[http://svn.python.org/view/python/trunk/Modules/cPickle.c?rev=59564&view=markup](http://svn.python.org/view/python/trunk/Modules/cPickle.c?rev=59564&view=markup)

---

### Post by Lau_of_DK on 2008-05-11
> **Smygis said:**
> The internets rule! You can google and browse SVN!
[http://svn.python.org/view/python/trunk/Modules/cPickle.c?rev=59564&view=markup](http://svn.python.org/view/python/trunk/Modules/cPickle.c?rev=59564&view=markup)

Exactly what I needed. Thanks alot!

/Lau

---

