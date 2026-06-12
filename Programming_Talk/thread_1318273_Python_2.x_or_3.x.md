---
title: "Python 2.x or 3.x?"
date: 2009-11-07
forum: Programming Talk
---

### Post by mivo on 2009-11-07
I haven't really been programming much in the past twenty or so years (used to do quite a bit in Pascal, GFA Basic and VB), but did pick up some Ruby knowledge over the years that I mostly use for small convenience scripts. Just enough to get by.

I'm interested in getting more familiar with Python, just to keep the brain in shape. :) I see that there are two Python lines, 2.x and 3.x. Tutorials seem to be available for both. What are the major differences (I noticed syntax changes) and, more importantly, which version is recommended to start with? (And why.)

Thanks for any pointers and answers!

---

### Post by karimruan on 2009-11-07
I have been programming in python on and off for about a year, and have tried both 2.x and 3.x.

The biggest differences are the syntax differences, such as you call the print() function in 2.6 as:

```

print "your text here"

```

whereas in 3.x you call it like a normal function:

```

print ("Your text here").

```

I stick with the 2.x versions mostly because that is what I started on, and the changes of the 3.x versions didn't seem significant enough to make the switch. THey are not cross compatible though, so I think eventually 2.x will die out.

Hope this helps.

---

### Post by fiddler616 on 2009-11-07
From what I understand, Python 3000 (3.x) is a better idea, and will become the standard soonish, but Python 2.x is still around because:
a) People like me are too lazy to switch.
b) There's a lot more libraries for Python 2.x.

If you start with 2.x, you can later convert it to Python 3000 with the 2to3 tool.

---

### Post by Can+~ on 2009-11-07
The transition is not all that different, I recommend starting with 2.x as it has more libraries (as pointed before) and there are more 3rd-party tutorials about these libraries.

And there are the main python3 gotchas:
[list=1]
[*]print is now a function. So you can pass it around.
[*]"Formatting" % (...) is deprecated
[*]Every string is UTF-8, and ascii strings are called bytearrays.
[*]The with statement can do a lot of fancy new stuff (open-close sockets, semaphores, locks, files, etc)
[/list]

And a lot more.

---

### Post by fiddler616 on 2009-11-07
> **Can+~ said:**
> 
[list]
[*]"Formatting" % (...) is deprecated
[/list]

I have not heard about this wrinkle, and am about to cry. What's the matter with it? What's the new regime? If we're stuck concatenating strings I really will bawl my eyes out.

---

### Post by Can+~ on 2009-11-07
> **fiddler616 said:**
> I have not heard about this wrinkle, and am about to cry. What's the matter with it? What's the new regime? If we're stuck concatenating strings I really will bawl my eyes out.

Was deprecated in favor of .format method.

[http://docs.python.org/dev/3.0/whatsnew/2.6.html#pep-3101](http://docs.python.org/dev/3.0/whatsnew/2.6.html#pep-3101)

---

### Post by fiddler616 on 2009-11-07
> **Can+~ said:**
> Was deprecated in favor of .format method.

[http://docs.python.org/dev/3.0/whatsnew/2.6.html#pep-3101](http://docs.python.org/dev/3.0/whatsnew/2.6.html#pep-3101)
:redface: An RTFM would also have been appropriate, were it not prohibited. I don't know why I didn't just Google it.

And I guess it's a more useful way of doing things, albeit a less efficient one, IMHO.

---

### Post by karimruan on 2009-11-07
I honestly had no idea there were so many differences with python 2.x and 3.x! I tried 3.x for a week, and decided to stick with 2.x because pygame was not yet compatible.

---

