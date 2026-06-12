---
title: "python for developing software..."
date: 2011-03-19
forum: Programming Talk
---

### Post by python3e on 2011-03-19
can i use python to create a school managent system or a library  management system or a simple billing software for a retail store or a  web based student information system??

i have started reading the beginners's guide of python

actually i have to create a software and submit it within 3-4 months. a college project..

---

### Post by andrew1992 on 2011-03-19
Absolutely you can! Python is a wonderful language, and I think you'll enjoy building software using it. Be sure to use the forums if you need help learning!

---

### Post by python3e on 2011-03-19
thanks..

should i use python 3.2 or 2.6 (which is already installed on my os) ?

---

### Post by andrew1992 on 2011-03-20
> **python3e said:**
> thanks..

should i use python 3.2 or 2.6 (which is already installed on my os) ?
I suggest 2.6, it's a more mature version of Python.

---

### Post by kurum! on 2011-03-20
I suggest [Ruby]("http://ruby-doc.org/docs/ProgrammingRuby/").

---

### Post by LemursDontExist on 2011-03-20
> **python3e said:**
> thanks..

should i use python 3.2 or 2.6 (which is already installed on my os) ?

It really depends on the details of what you're trying to do.  From a learning perspective, python 3 is more useful since eventually python 2.6 is going to be replaced.  Also, if you want your module to still work on a default install a couple years from now, python 3 will get you ahead of the game.

The main downsides to python 3 are that many modules have not yet been updated for it, and it does worse on performance benchmarks.  However, most modules *will* eventually be updated, so unless you decide you need to use a module which doesn't exist for python 3, that shouldn't be a long term problem.  Performance on benchmarks may eventually improve also, and for the applications you're talking about shouldn't really matter.

I still program in python 2.6, but if I were starting now, I'd go with python 3.

---

### Post by llanitedave on 2011-03-20
> **LemursDontExist said:**
> It really depends on the details of what you're trying to do.  From a learning perspective, python 3 is more useful since eventually python 2.6 is going to be replaced.  Also, if you want your module to still work on a default install a couple years from now, python 3 will get you ahead of the game.

The main downsides to python 3 are that many modules have not yet been updated for it, and it does worse on performance benchmarks.  However, most modules *will* eventually be updated, so unless you decide you need to use a module which doesn't exist for python 3, that shouldn't be a long term problem.  Performance on benchmarks may eventually improve also, and for the applications you're talking about shouldn't really matter.

I still program in python 2.6, but if I were starting now, I'd go with python 3.

On my machine, Python 3.1.2 performs significantly faster than 2.6.  The 3.0 version took a performance hit, but they seemed to have pulled back ahead with 3.1.  That probably depends on specific benchmarks, though.

There's a pretty good argument to be made for sticking with the 2.X version of Python, but if you're learning from scratch, it seems that you're better off in the long run starting with Python3.  Not all of the convenient libraries may yet be ported, and if you want to use tools like wx.Python or Django, you're still held at the lower version.  But they'll come around, and in the meantime, there's really nothing you can't do with Python 3 and its included sqlite3, wsgi, multithreading, and Tkinter.

---

### Post by Vox754 on 2011-03-20
> **LemursDontExist said:**
> It really depends on the details of what you're trying to do.  From a learning perspective, python 3 is more useful since eventually python 2.6 is going to be replaced.  Also, if you want your module to still work on a default install a couple years from now, python 3 will get you ahead of the game.

The main downsides to python 3 are that many modules have not yet been updated for it, and it does worse on performance benchmarks.  However, most modules *will* eventually be updated, so unless you decide you need to use a module which doesn't exist for python 3, that shouldn't be a long term problem.  Performance on benchmarks may eventually improve also, and for the applications you're talking about shouldn't really matter.

I still program in python 2.6, but if I were starting now, I'd go with python 3.

This story never ends.

I suggest the exact opposite. Go with Python 2.6. It's there, already installed, already pre-packaged. It just works. For a beginner, starting on a very solid foundation is recommended.

Python 2 and 3 are intentionally not compatible, but they are not that different. A couple of functions deprecated, the "print()" function, other functions in more standardized modules, and that's it.

Any competent programmer of the 2 series, or more generally, any smart person, should be able to notice the small differences and tackle them without problems.

Besides, Python has excellent documentation.

Here's is how it should go: Read the Python 2 tutorials, read the reference documentation, finish your 4-month project. After you have gotten your passing grade, read the Python 3 tutorial, read the reference documentation, and port your program to the newer version. Realize there is not much difference.

By the way, I'm surprised of people saying that Python 3 is slower on benchmarks. Generally, whenever there is a major upgrade of a virtual machine, the code is always faster, since they always manage to speed up tight loops and improve the bytecode. At least that's the case with other languages such as Perl and Tcl.

---

### Post by llanitedave on 2011-03-20
> **Vox754 said:**
> This story never ends.

I suggest the exact opposite. Go with Python 2.6. It's there, already installed, already pre-packaged. It just works. For a beginner, starting on a very solid foundation is recommended.

Python 2 and 3 are intentionally not compatible, but they are not that different. A couple of functions deprecated, the "print()" function, other functions in more standardized modules, and that's it.

Any competent programmer of the 2 series, or more generally, any smart person, should be able to notice the small differences and tackle them without problems.

Besides, Python has excellent documentation.

Here's is how it should go: Read the Python 2 tutorials, read the reference documentation, finish your 4-month project. After you have gotten your passing grade, read the Python 3 tutorial, read the reference documentation, and port your program to the newer version. Realize there is not much difference.


You can reverse the positions of Python 2 and Python 3 in this post and make the exact same argument.

You're right that's really not such a big deal.  A person can start out on either one and do well.  They aren't that different, and they are both good, solid languages.

---

### Post by LemursDontExist on 2011-03-21
> **Vox754 said:**
> I suggest the exact opposite. Go with Python 2.6. It's there, already installed, already pre-packaged. It just works. For a beginner, starting on a very solid foundation is recommended

If Python 3 weren't in the ubuntu repo, I would agree 100%.  As it stands though, installing it is trivial and, I think, worth the trouble.  That said, Python 2.6 really is a completely legitimate choice here.  The learning curve from 2.6 to 3 is pretty shallow as Vox points out, and if you do find yourself wanting to use a module hat hasn't been ported yet, it will be a nuisance.

Also, a small note for python3e, if you *do* choose to use python 3, don't try to remove python 2.6.  Th two can live side by side perfectly well, and python 2.6 is an integral part of your desktop environment which python 3 can't replace yet.

---

