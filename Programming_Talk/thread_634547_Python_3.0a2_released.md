---
title: "Python 3.0a2 released"
date: 2007-12-07
forum: Programming Talk
---

### Post by Majorix on 2007-12-07
I noticed that Python 3000's second alpha was released just today (well actually yesterday for us European's).

I have downloaded its source and installed from there. I will now ask the folks at Hardy development to add it to Backports. We will see how it goes.

Discuss the new features of it!

---

### Post by Wybiral on 2007-12-07
Personally I'm not fond of the changes to map/reduce/filter/zip. I realize it's mostly to help make the code more uniform (helping to enforce the "one obvious way" concept), which I understand.

But realistically it's a minimal concern considering you can write them yourself in less than a few lines of code:

```

def map(fp, lst):
    return [fp(i) for i in lst]

```

But it will make it an extra mental step to translate Python code between other functional languages who use the standard functional components. But, Guido's a smart guy, I'm sure he knows what he's doing.

---

### Post by tyoc on 2007-12-07
which are those "changes" that you say?

---

### Post by pmasiar on 2007-12-07
When OP will grow up, he will learn post more links and less excitement. Until then, sample:

- [Guido](http://www.artima.com/weblogs/viewpost.jsp?thread=208549) on Status, process, changes, even [more details](http://www.python.org/dev/peps/pep-3100/)
- [PEP 3099:](http://www.python.org/dev/peps/pep-3099/) Things that will Not Change in Python 3000
- [discussion](http://lwn.net/Articles/214931/) about changes and what gets postponed to Py4000 :-)
- [video and slides](http://www.artima.com/forums/flat.jsp?forum=106&thread=196889)

Guido's explicit goal with Py3k is to avoid too many too radical changes - avoiding fate of Perl 6.

---

### Post by engla on 2007-12-07
> **Wybiral said:**
> ```

def map(fp, lst):
    return [fp(i) for i in lst]

```

But it will make it an extra mental step to translate Python code between other functional languages who use the standard functional components. But, Guido's a smart guy, I'm sure he knows what he's doing.
The thing was that somehow, you are encouraged to not write map anymore, but to always use ```
[f(i) for i in lst]
```, as I've understood it. When I learned Python, it would have been much easier to learn a map command than list comprehensions (honestly: I had to focus and study to "get it"), but now I agree that list comprehensions are more pythonic.

[quote=pmasiar]When OP will grow up, he will learn post more links and less excitement.[/quote]

One more link: 
[Guido's announcement on his blog]("http://www.artima.com/weblogs/viewpost.jsp?thread=220341")

---

### Post by Wybiral on 2007-12-07
Come to think of it, "zip" at least is one that while I rarely use... I have ran into some situations where I've used it (especially for handling vectors). And it's a little more code to implement on your own:

```

def zip(*args):
    minLen = min([len(arg) for arg in args])
    return [tuple([arg[i] for arg in args]) for i in xrange(minLen)]

```

It's still only three lines, but IMO is less obvious than simply using zip. Oh well, if worst-comes-to-worst, you can always just import googles [Goopy]("http://goog-goopy.sourceforge.net/"). Maybe they should just add a functional module to Python. That way it wouldn't be built into the language (so there still is only one obvious way) but for situations that are best suited for the standard functional components they can just import it?

---

### Post by engla on 2007-12-08
Wybiral, zip will be in Python 3.0. Maybe map won't, but zip definitely will be; the only change is that it, like many other things, will return an iterator (like itertools.izip), not a list.

---

### Post by Wybiral on 2007-12-08
> **engla said:**
> Wybiral, zip will be in Python 3.0. Maybe map won't, but zip definitely will be; the only change is that it, like many other things, will return an iterator (like itertools.izip), not a list.

OK, I was under the impression all four of them were likely to be tossed. I guess that's a bit better, I still don't 100% get the purpose of this though.

---

### Post by engla on 2007-12-08
Hey, I decided to check. This [Python 3 documentation site]("http://docs.python.org/dev/3.0/") is pretty interesting. And on map, zip, filter right now it says...

 [What's new]("http://docs.python.org/dev/3.0/whatsnew/3.0.html")

*zip(), map() and filter() return iterators.

However, it also says:

* Removed: apply(), callable(), coerce(), execfile(), file(), reduce(), reload().

---

### Post by musicinmybrain on 2007-12-22
> **engla said:**
> *zip(), map() and filter() return iterators.

However, it also says:

* Removed: apply(), callable(), coerce(), execfile(), file(), reduce(), reload().

At least for reduce(), "removed" actually means "moved to the functools module", so it's still there for importing if you want it. (If you aren't a hard-core functional programmer, you probably don't.)

---

### Post by Majorix on 2007-12-22
I have installed Python 3.0a2, and have seen that the backwards-compatibility wasn't cared about. Most of my apps stopped working since they run "python module" and since python is set to 3.0, and since it didn't work with older programs, I was left with no choices but to uninstall 3.0 again for now. In the future we will see programs compatible with 3.0 and hopefully we will start writing compatible programs too :p

---

### Post by Lster on 2007-12-22
Hi all

This looks like good news for Python and after the recent thread that turned into a Python vs C debate I have decided that I should try Python (I have only dabbled with it so far). If Python 3.0 is coming out soon (I hadn't heard anything about it), would I be best waiting until 3.0 arrives?

Thanks,
Lster

---

### Post by musicinmybrain on 2007-12-22
> **Majorix said:**
> I have installed Python 3.0a2, and have seen that the backwards-compatibility wasn't cared about. Most of my apps stopped working since they run "python module" and since python is set to 3.0, and since it didn't work with older programs, I was left with no choices but to uninstall 3.0 again for now. In the future we will see programs compatible with 3.0 and hopefully we will start writing compatible programs too :p

Yes, the reason the 3.x branch is such a big deal is that the Python developers are making a one-time break in backwards compatibility. This will bring what most people (myself included) believe are significant improvements to the language that could not have been made while preserving backwards compatibility. However, it does mean that unmodified Python 2.x code will usually not run under Python 3.x. If you want to install Python 3.0a2 on the side to try it out, use "sudo make altinstall" instead of "sudo make install" when compiling the sources. This way, your default Python (/usr/bin/python) will still be Python 2.5.1 (or 2.4 if you're running an older version of Ubuntu), but you can access Python 3.0a2 by running python3.0.

---

### Post by Majorix on 2007-12-22
> **Lster said:**
> Hi all

This looks like good news for Python and after the recent thread that turned into a Python vs C debate I have decided that I should try Python (I have only dabbled with it so far). If Python 3.0 is coming out soon (I hadn't heard anything about it), would I be best waiting until 3.0 arrives?

Thanks,
Lster
3.0 isn't coming anytime too soon. It will officially arrive in Aug08 and you will then have to wait for good docs to be written for it. I would start with 2.5.

> **musicinmybrain said:**
> Yes, the reason the 3.x branch is such a big deal is that the Python developers are making a one-time break in backwards compatibility. This will bring what most people (myself included) believe are significant improvements to the language that could not have been made while preserving backwards compatibility. However, it does mean that unmodified Python 2.x code will usually not run under Python 3.x. If you want to install Python 3.0a2 on the side to try it out, use "make altinstall" instead of "make install" when compiling the sources. This way, your default Python (/usr/bin/python) will still be Python 2.5.1 (or 2.4 if you're running an older version of Ubuntu), but you can access Python 3.0a2 by running python3.0.

Actually, by "uninstalling" I meant that I changed the symlink python to python2.5. I still have Python3.0 installed and can access it via a "python3.0 [command]". I always liked the newest software, so don't go thinking I would remove it just like that :D

---

### Post by musicinmybrain on 2007-12-22
> **Lster said:**
> If Python 3.0 is coming out soon (I hadn't heard anything about it), would I be best waiting until 3.0 arrives?

I agree with Majorix. If I were you, I would go ahead and learn Python 2.5. A final release of Python 3.0 is not expected until at least August 2008, and Python 2.x will still be in wide use for a long time after that. In fact, there will be at least one new release in the backwards-compatible 2.x branch; Python 2.6 is targeted for April 2008.

---

### Post by LaRoza on 2007-12-22
> **musicinmybrain said:**
> I agree with Majorix. If I were you, I would go ahead and learn Python 2.5. A final release of Python 3.0 is not expected until at least August 2008, and Python 2.x will still be in wide use for a long time after that. In fact, there will be at least one new release in the backwards-compatible 2.x branch; Python 2.6 is targeted for April 2008.

The changes are not all that drastic, like:

* print "Hello world" becomes: print("Hello world") 
* raw_input() becomes input()
* input() becomes eval(input())

And a few other changes....

It is still Python, and the changes are for the better.

---

### Post by Majorix on 2007-12-22
But those "few" changes make the programs unable to run with the 3.0 interpreter. I have tested it and am not just assuming.

---

### Post by LaRoza on 2007-12-22
> **Majorix said:**
> But those "few" changes make the programs unable to run with the 3.0 interpreter. I have tested it and am not just assuming.

I believe there will be converters for changing the code, it isn't backwards compatible as you stated.

---

### Post by Majorix on 2007-12-22
Actually there is already one, helpfully titled 2to3, but I didn't know how to install it. It is on python's official site.

---

### Post by LaRoza on 2007-12-22
> **Majorix said:**
> Actually there is already one, helpfully titled 2to3, but I didn't know how to install it. It is on python's official site.

You should wait, it seems it isn't quite ready.

---

### Post by Xavieran on 2007-12-22
Seems a bit strange to me...
What do they need to change raw_input and input() for?
And print("Hello World")!?
Ah well,I guess 'tis for the good of all...

---

### Post by LaRoza on 2007-12-22
> **Xavieran said:**
> Seems a bit strange to me...
What do they need to change raw_input and input() for?
And print("Hello World")!?
Ah well,I guess 'tis for the good of all...

I think the changes make sense. It makes sense for print to be a function (I found it odd it wasn't when I started) and the change of the input methods makes sense also. I usually always have taken input as strings then tested and converted them, and found the input() method to be odd, now it makes sense, eval() is more logical.

---

### Post by Mr.popo on 2007-12-22
The new 3.0 documentation is very nice .

---

### Post by pmasiar on 2007-12-28
> **Xavieran said:**
> Seems a bit strange to me...
What do they need to change raw_input and input() for?
And print("Hello World")!?

All changes were discussed in great detail, and reasoning was documented in PEPs, Guido's blog, and  many presentations, including migration path from 2.6 to 3.0. Some changes are available in 2.6 by standard "from __future__ import ..." trick, as always.

Print() function is more flexible (ie it lets you to redefine your own print function). raw_input() is called simply input() now, to make beginner's life simpler. :-)

Unless you want to report 3.0 bugs, I do not see point in installing/using 3.0 alpha, or even bothering with new syntax.

---

