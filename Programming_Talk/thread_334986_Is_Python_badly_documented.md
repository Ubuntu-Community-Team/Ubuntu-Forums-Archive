---
title: "Is Python badly documented?"
date: 2007-01-09
forum: Programming Talk
---

### Post by kd_pease on 2007-01-09
Hi,

I'm an experienced developer with knowledge of C, Perl, .Net, SQL and a few other bits and pieces who has been trying to learn Python over the last few weeks. Python appears to be an excellent language, and I'm getting on ok (ish), but I'm finding it very frustrating that it always takes me a long time to learn to use a new part of the library. The library reference guide just doesn't seem to have the information you actually need. As a recent example, nowhere in the library reference could I find anything that tells me how to call re.Search() with an un-compiled regular expression. The Perl documentation is much clearer in this regard IMHO. 

I guess there must be a few experienced Python developers reading these forums. Am I missing something that would help me out?

Please - no posts saying "You should just learn xxx programming language..." Python is where my interest lies at present - I'm going to get it if it kills me... :)

---

### Post by lloyd mcclendon on 2007-01-09
```
lloyd@localhost:~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import re
>>> help(re)
```

not sure if that's badly documented or waht you're looking for but i think it's a pretty cool feature.

---

### Post by meng on 2007-01-09
I assume by library reference guide you mean docs.python.org
I must admit that I find this a little confusing also, but then I only have my experience with Java to compare with, and the Java docs seemed even more arcane!
In the end, I found I just had to go back to the many excellent books pitched at beginners AND advanced users, and get familiarity that way.
Look at [www.diveintopython.org](www.diveintopython.org) if you haven't already. An excellent (I think) chapter on regular expression library there.

---

### Post by maxamillion on 2007-01-09
Not only is python one of the better documented languages I have found but its self documented, which is really nice.....

---

### Post by pmasiar on 2007-01-09
No, you are learning right language - you just need to became more familiar with one of Python's biggest user - Google :evil:

Simple Google search "re.search+python" gave on the first page excellent hits:
- standard docs: [http://docs.python.org/lib/re-syntax.html](http://docs.python.org/lib/re-syntax.html)
- [http://www.regular-expressions.info/python.html](http://www.regular-expressions.info/python.html)
- Kuchlings. How-to: [http://www.amk.ca/python/howto/regex/](http://www.amk.ca/python/howto/regex/)
 - Python cookbook at ASPN: [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/456151](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/456151)

---

### Post by johnnymac on 2007-01-09
Python's great with documentation - especially all of the additional pieces you can use with python.  I'm not sure about internal documentation because I don't use it...but what's available out on the Web is PLENTY to get anyone into trouble...

---

### Post by kd_pease on 2007-01-10
Thanks guys, that's helpful - especially the comment from lloyd mcclendon - I didn't know about that. That might just be the thing I'm missing...

I did mean the docs at docs.python.org. I might draw a bit of fire for this, (And it does sicken me slightly to say it...) but I do have to say that Microsoft's documentation of the .Net framework is much more helpful than the docs for Python.

Anyway, the things to take from this discussion appear to be that I could do with a decent Python book, and that Google is my best friend... :)

Thanks again for all your comments.

---

### Post by UbuWu on 2007-01-10
Also very useful: [a python documentation sidebar]("http://www.edgewall.org/python-sidebar/") in firefox

---

### Post by meng on 2007-01-10
> **UbuWu said:**
> Also very useful: [a python documentation sidebar]("http://www.edgewall.org/python-sidebar/") in firefox
Ooh thanks for the link, this is going straight onto my system when I get home.
To the OP: documentation that isn't clear to you as one individual user is still a problem. You may have a good point - so I encourage you (when you get more proficient in Python) to sally forth and fix it!!!

---

### Post by jblebrun on 2007-01-10
I've found the docs at docs.python.org to be a bit lacking as well. They talk about everything, but sometimes details are missing. I think the docs would be best helped by more code examples.

---

### Post by pmasiar on 2007-01-10
> **jblebrun said:**
> I've found the docs at docs.python.org to be a bit lacking as well. They talk about everything, but sometimes details are missing. I think the docs would be best helped by more code examples.

Docs are more for reference - if you have too many pages to go through, you would complain docs are too wordy :-)

More examples and explanations - that's why books are written. O'Reilly books are above average. [Python Cookbook]("http://aspn.activestate.com/ASPN/Python/Cookbook/") has loads of examples - more useful because they show function in context of solving a problem. Or just search for function - Google is smart.

---

### Post by dwblas on 2007-01-10
Look in activestate or faqts for examples or code snippets
[http://aspn.activestate.com/ASPN/Cookbook/Python/](http://aspn.activestate.com/ASPN/Cookbook/Python/)
[http://www.faqts.com/knowledge_base/index.phtml/fid/199/](http://www.faqts.com/knowledge_base/index.phtml/fid/199/)
Python eggs has links to everything
[http://www.python-eggs.org/](http://www.python-eggs.org/)
and this is a link to free as in beer online Python books 
[http://python-forum.org/py/viewtopic.php?t=12&postdays=0&postorder=asc&start=0](http://python-forum.org/py/viewtopic.php?t=12&postdays=0&postorder=asc&start=0)
If you get stuck, ask here or on python-forum.org.

---

### Post by kripkenstein on 2007-01-11
Generally docs.python.org is excellent, for basic and intermediate stuff. For some advanced topics I found it to be missing some important details (e.g. BaseHttpServer).

But as others have mentioned, other sites are very useful, and there are a lot of friendly Python programmers who are helpful, here, on IRC or other places.

---

