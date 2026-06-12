---
title: "How will the python 3.0 API breakage effect general linux desktop software?"
date: 2008-10-21
forum: Programming Talk
---

### Post by eragon100 on 2008-10-21
How do you guys think the release of python 3.0, which will render all current python code obsolete (even the print statement won't work anymore)... :

[http://www.linux.com/feature/150399](http://www.linux.com/feature/150399)

... will effect the software we like to use? I have no doubt that, say, the battle for wesnoth (AI is written in python) will be ported over, but this could destroy a lot of nice desktop software available for linux, at least for a few months. How bad do you people think it will be for end-users of python programs?

---

### Post by Canis familiaris on 2008-10-21
I don't think because AFAIK Python 2.x code can be easily converted to Python 3.0 code. And anyway we are still few years away of totally implementing Python 3.0
Not to mention there aren't that significant changes that will break the code.

---

### Post by pmasiar on 2008-10-21
Switch for 2.6 will warn at all suspicious constructs. Most can be coded in a cleaner way, which can be converted programmatically to valid 3.0 code (converter is part of Py3K development).

Conversion is planned in a very careful way, and (together with unit testing) there should be little surprises and disruption, not substantially more than any other version of any library upgrade.

Summary: write your unit tests and relax :-)

> we are still few years away of totally implementing Python 3.0

Wrong.

first release candidate of Python 3.0 was released on September 17, 2008.

[http://www.python.org/dev/peps/pep-3000/](http://www.python.org/dev/peps/pep-3000/)
[http://www.python.org/dev/peps/pep-0361/](http://www.python.org/dev/peps/pep-0361/)

Dec 03 2008: Python 3.0 final planned. 

"I expect that there will be parallel Python 2.x and 3.x releases for some time; the Python 2.x releases will continue for a longer time than the traditional 2.x.y bugfix releases." (GvR)

But Py2.9 will be the last one, no Py2.10 because it does not sort properly ;-)

---

### Post by slavik on 2008-10-21
A year ago a new version of EVE came out that wouldn't run on WINE ... WINE was fixed in about a month.

I gather that the code change will take like 2 weeks at most, unless people become lazy ...

---

### Post by snova on 2008-10-21
It won't affect "general linux desktop software" at all. Why would it? It's just a new version. Python programs will continue to depend on what are now current releases, until they port (which should be easy), then they will depend on something else. Only developers are going to care.

> which will render all current python code obsolete

That's just plain wrong. "Broken" might be closer to it.

I hope they make the standard library a bit more hierarchal. That would be nice...

---

### Post by nvteighen on 2008-10-21
IMO, it won't break anything at any time: until your code is not Python 3.0, Python 2.5/2.6 interpreters will still be around and I guess still downloadable from Python.org...

---

### Post by scottuss on 2008-10-21
I hope there are no major changes, I've just started learning Python! At least it will keep me on my feet :lolflag:

---

### Post by eragon100 on 2008-10-21
> **scottuss said:**
> I hope there are no major changes, I've just started learning Python! At least it will keep me on my feet :lolflag:

same thing for me, actually! :(

---

### Post by shadylookin on 2008-10-21
well the interpreters for python 2.x isn't going to drop off the face of the earth or anything. So they could not upgrade at all as long as the interpreter for it is still around you'll be able to use the program.

---

### Post by eragon100 on 2008-10-21
> **shadylookin said:**
> well the interpreters for python 2.x isn't going to drop off the face of the earth or anything. So they could not upgrade at all as long as the interpreter for it is still around you'll be able to use the program.

But installing both 2.x for old and 3.0 for new programs is a pain... :(

---

### Post by sheto on 2008-10-22
It won't. People will switch to it in no time.

---

### Post by alberto ferreira on 2008-10-22
I was starting to learn python (3 days ago) - I have version 2.5.2. How do I upgrade to 3 or 2.6?

Should I wait for version 3 to learn it/is it worth learning python now, when it's going to be changed?

---

### Post by snova on 2008-10-22
The changes won't be drastic. Learn now, and then it'll be easy to learn the differences between 2.x and 3.x.

Upgrading should be as simple as installing new packages. I doubt that Ubuntu is going to remove the older ones for a long time.

---

