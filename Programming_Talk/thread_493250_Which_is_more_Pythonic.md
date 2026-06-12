---
title: "Which is more Pythonic?"
date: 2007-07-05
forum: Programming Talk
---

### Post by slumcat05 on 2007-07-05
OK, I just started learning Python, and I love it. I'm a longtime Matlab user, and am novice/intermediate with C (i.e. I've had a 100 level course oriented towards aerospace engineers). I'm trying to practice the whole concept of Pythonic... (ness?). I know that in many cases, the best way to do something is generally the *only*, way, and hence the most Pythonic. However there is one case that I am confused about, and I'm hoping any Python pros can offer some advice. Take for example the following two codes snippets:

**_Method 1:_**
```
a = 1
b = 2
print "The value of a is", a, "and the value of b is", b
```

**_Method 2:_**
```
a = 1
b = 2
print "The value of a is %i and the value of b is %i" % (a, b)
```

Both of these produce the exact same message on the screen, 'The value of a is 1 and the value of b is 2'. My internal debate is this: I'm familiar with the %i, %d, %s, etc. placeholders from C and Matlab, and this method is a little bit quicker to type (fewer double-qoutes and commas). I can't decide, however, which is more readable. To me, both methods are pretty straightforward, so Method 2 seems more desirable (like I said, a little quicker to type), but it seems like a person unfamiliar with the placeholders from C, Matlab, etc. may have trouble seeing what is going on in Method 2.

Can any pros please throw in their $0.02 (by the way, what ever happened to the "cent" symbol? Does nobody use that anymore?). Is there a preffered method? Is one faster or less memory intensive than the other? Are there certain times when one should be used, and other times when the other should be used? Or is this just a unique case where there is more than one way to do it, and it's completely up to the programmer to decide which is best or most convenient? Thanks for any input/opinions.

---

### Post by pointone on 2007-07-05
I'm not really a Python 'pro', so I hope you don't mind me chipping in... :P

I always try to use string formatting because it's much more powerful. You can, for instance, use a dictionary to replace values rather than specify each value individually. For example:

```
z = {"a": 1, "b": 2}
print "The value for a is %(a)i and the value of b is %(b)i" % z
```

While this might not seem like a big deal now, it helps a lot in larger projects where your values might be constantly changing, or where it's easier to package everything together in a dictionary (or where output is a dictionary by default). I also find it easier to read because "print a" doesn't tell you anything about the value of a, whereas "print '%i' % a" shows that the value will be an integer (of course, I wouldn't use string formatting in a case this simple; it's just an example).

Overall, though, it's more a matter of personal preference. Whichever is easier for you is the best solution, in my opinion.

---

### Post by pmasiar on 2007-07-05
Let's define what we are talking about
```

tuples: 
  print 'text', value
String interpolation: 
  print "text %i more ]%s[ text" % (ivalue, svalue)   or 
  print "text %(NAME)i more text" % dict(NAME=ivalue)

```

There is one more slight difference:  Print using tuples adds a space between text and value. Interpolation gives you  more control over formatting (including no extra spaces).

So it depends - and most time I use excellent templating system Kid to output my  text (webpages).

There is no strict rule about usage, but *I* most often use tuples for debug messages, and interpolation for regular output (and if using dicts, I use keys ALLCAP to show where values go).

Tuples are probably simpler (Python does not need to create new  strings with interpolated values), but difference is OMHO very minor and not worth bother.

---

### Post by Note360 on 2007-07-05
pythonic is kinda up to interpretation for somethings. Obviously some ways are more right than others, but in the end its really prefrence. I think python needs something like ruby's "#{variable}". I would suggest %[var]formatting_stuff, this way we get a compact way to do it that looks pretty tame for string formatting.

---

### Post by pmasiar on 2007-07-05
What ruby's "#{variable}" does what cannot be done as easy with string interpolation?

---

### Post by xtacocorex on 2007-07-05
> **slumcat05 said:**
> (i.e. I've had a 100 level course oriented towards aerospace engineers). 
Everyone knows that all Aerospace Engineers need to learn FORTRAN, I myself am one of the proud few.  In fact, it is in the program at Iowa State from day one.  Beside knowing a language 80% of the world forgot about, you'll get the added satisfaction of using a language that ran on punch cards, not something most other languages can offer you.

You can also do the cool OOP that everyone is talking about these days with FORTRAN and would only have to worry about what your original question deals with if you use FORMAT to set up output formatting.

---

### Post by kripkenstein on 2007-07-06
Well, in Python3000 (Python 3.0, coming out in a year or so), this will not be relevant anymore as the 'print' statement is changing. It will be a function, and other things.

So, the **real** pythonic way to write that is yet to come ;)

But meanwhile both of your examples look fine to me.

---

### Post by cwaldbieser on 2007-07-06
> **Note360 said:**
> pythonic is kinda up to interpretation for somethings. Obviously some ways are more right than others, but in the end its really prefrence. I think python needs something like ruby's "#{variable}". I would suggest %[var]formatting_stuff, this way we get a compact way to do it that looks pretty tame for string formatting.

In python 2.4, the string.Template class allows for "shell-style" substitution.

```

import string
t = string.Template("Hello, ${thing}!")
print t.substitute(thing='World')

```

---

### Post by LaRoza on 2007-07-06
> **slumcat05 said:**
> ets:

Can any pros please throw in their $0.02 (by the way, what ever happened to the "cent" symbol? Does nobody use that anymore?) ... Thanks for any input/opinions.
The entity to use is "&cent;"; however, it is disabled in this forum. (It converts the initial "&" into ints entity, which is "&amp;"

---

### Post by slumcat05 on 2007-07-06
Thanks for all the feedback. I guess the general consensus is that there's no general consensus. I did, however, learn a few things, such as the string interpolation method with dictionaries, which I hadn't seen yet, so thanks to all.

> **xtacocorex said:**
> Everyone knows that all Aerospace Engineers need to learn FORTRAN

Yeah, I've seen some of that. In one of my internships at NASA my mentor wanted me to do all my work in FORTRAN. Fortunately for me it was only a 6 week internship (not much time to learn a new language and still get work done), so he had mercy and allowed me to use Matlab. Since then I've used a lot of NASA tools that were written in FORTRAN (I just compiled and moved on), but in my experience so far with Boeing it seems like the trend, at least in the commercial sector, is moving towards Matlab; so I'm glad that my undergrad classes focused on that. In fact I'm rather surprised that Iowa State is teaching it.

---

### Post by xtacocorex on 2007-07-06
Definitely way off topic here.  Iowa State's program is very numerical method oriented (aside from Aerodynamics) and programming is one of the big weed out factors early on.  They are starting to use more Matlab though with the newer classes being brought in.  The only class I used it in was Flight Controls.

---

