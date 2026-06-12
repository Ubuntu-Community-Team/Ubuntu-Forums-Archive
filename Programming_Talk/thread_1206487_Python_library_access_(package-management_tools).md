---
title: "Python library access (package-management tools)?"
date: 2009-07-07
forum: Programming Talk
---

### Post by Markhor on 2009-07-07
Hi. I've heard that python has impressive libraries available. 
I'm wondering how do I access the primary library repository?? 
For example: perl has cpan, ruby has rubygems, haskell cabal.
I've been unable to find what python has. 
What is the de facto standard for python library management? Thanks

---

### Post by unutbu on 2009-07-07
Unfortunately, as far as I know, Python has no third-party repository that rivals Perl's CPAN.

When looking for modules, there is of course the standard library:
[http://docs.python.org/modindex.html](http://docs.python.org/modindex.html)

Next, the official Ubuntu repository has a number of python packages which provide extra functionality:
```
apt-cache search python | grep '^python'
```

Finally, just google. You may find what you are looking for here:

[http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/)

If this is not helpful, tell us what in particular you are looking for. We might be able to point you in the right direction.

---

