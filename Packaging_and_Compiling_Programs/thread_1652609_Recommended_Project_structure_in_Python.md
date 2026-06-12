---
title: "Recommended Project structure in Python"
date: 2010-12-25
forum: Packaging and Compiling Programs
---

### Post by viMitch on 2010-12-25
I am posting to ask if there is a pythonic way to structure my project
For example in Linux you would have /bin, /sbin & /usr/bin.

What common practices would you follow when building your project?

I want code I write to be neat, both in the source and in the end package

I am still new to programming and don't know everything :)

Thank you.

---

### Post by QUARKSPIN on 2010-12-27
I can't really call myself an expert, but by general advice is to create a special directory in your home folder for your project, and make it as standalone as possible. Considering how much harddisk space people have these days, most of us would rather have two copies of pygame than have a dependency resoloution issue.

---

### Post by MadCow108 on 2010-12-27
I'm also no expert in python structuring but from a distribution point of you don't want it to be as standalone as possible. This may be common in windows but not in linux distributions.
having two copies of e.g. pygame makes it very hard to maintain and is a potential security risk (if a flaw is discovered you may forget to update one)

here is the debian python policy which covers how programs should be installed on debian like systems:
[http://www.debian.org/doc/packaging-manuals/python-policy/](http://www.debian.org/doc/packaging-manuals/python-policy/)

---

### Post by viMitch on 2010-12-27
Thank you for you input, the link you gave me looks perfect for what I need. :)

EDIT: I read through the link, but it doesn't say anything about the actual project, only talks about dependency handling and making your package apt friendly, nothing about the style of the files in it (It does mention about _init_.py as a python style guideline, but sadly not in depth.)

Any ideas if there is any python docs on packaging? (Now googling it)

EDIT 2: [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)
Did not provide much info on how you should package it, and was the best I found.

---

### Post by MadCow108 on 2010-12-28
you might also want to read this:
[http://diveintopython3.org/packaging.html](http://diveintopython3.org/packaging.html)
its about a python3 tool but it also has a few words about structure which should also apply to python2

---

### Post by viMitch on 2010-12-29
Thank you so much MadCow,
I didn't even have a clue about it, and this is good for Python 3, since I use Python 3.
:)

---

