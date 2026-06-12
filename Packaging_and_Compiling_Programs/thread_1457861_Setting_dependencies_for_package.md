---
title: "Setting dependencies for package"
date: 2010-04-19
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-04-19
I'm trying to figure out how I should set the dependencies for my package, and I have two questions.  My program depends on python, and up until this point I have just put "python" under dependencies.  I'm sure that some people are having issues with my program due to different versions of python on their system.

So my fist question is this:
Wait!! Sorry, I think I just answered my question.  If my program depends on python v2.6, I would put this in the control file:```
Depends: python (>=2.6) | python2.6
```The reason I was asking was because I saw the two different packages in synaptic, "python" and "python2.6".

My other question is about python3.  I'm sure that my program is incompatible with python 3.0--Oh, I think I just realized the answer to this one as well, lol. :)

This is what I would want to put in the control file if I wanted to tell the system greater than or equal to 2.6, but less than 3.0:```
Depends: python (>=2.6,<<3.0) or python2.6
```Please let me know if this is the correct method.  I haven't been able to find a direct answer in the packaging guides for the second one.

**Edit:** Another question:  I see in synaptic that python's version is 2.6.4-0ubuntu1.  Do I need to include the whole version number?  E.g., will it suffice to just put "python (>=2.6)" instead of "python (>=2.6.4-0ubuntu1)", I mean as long as I am sure that my program will work with any of the 2.6 releases?

---

### Post by krazyd on 2010-04-20
1. that is correct.
2. don't worry about python3 at all. the packages python and python3 don't conflict because the default python version is 2.6 so if your program doesn't specifically invoke python3.1 then it won't even know it's there. just depend on python 2.6.
3. just put "2.6". the package manager is smart enough to figure it out :-)

---

### Post by dodle on 2010-04-21
Thanks

---

