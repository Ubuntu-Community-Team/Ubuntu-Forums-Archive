---
title: "Python completion is not working in emacs"
date: 2008-06-11
forum: Programming Talk
---

### Post by oneself on 2008-06-11
Hi All,

I've just recently started to learn Python.  I use emacs with the 
default python-mode.  When I invoke the  python-complete-symbol
command, I only get the default methods that all objects share.

For example, trying to complete the following:
s = "a string"
s.endsw

Will generate the following suggestions:

s.__class__			   s.__cmp__
s.__contains__			   s.__delattr__
s.__delitem__			   s.__doc__
s.__eq__			   s.__ge__
s.__getattribute__		   s.__getitem__
s.__gt__			   s.__hash__
s.__init__			   s.__iter__
s.__le__			   s.__len__
s.__lt__			   s.__ne__
s.__new__			   s.__reduce__
s.__reduce_ex__			   s.__repr__
s.__setattr__			   s.__setitem__
s.__str__			   s.clear
s.copy				   s.fromkeys
s.get				   s.has_key
s.items				   s.iteritems
s.iterkeys			   s.itervalues
s.keys				   s.pop
s.popitem			   s.setdefault
s.update			   s.values


How do I get this to work, or debug it?

Thanks

---

