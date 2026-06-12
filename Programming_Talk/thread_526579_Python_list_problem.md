---
title: "Python list problem"
date: 2007-08-15
forum: Programming Talk
---

### Post by chrisN_uk on 2007-08-15
Can someone explain this behaviour to me? I'm not sure about it at all...


```

>>> aList=[ [0]*3] *3
>>> print aList
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]
>>> aList[0][0]=1
>>> print aList
[[1, 0, 0], [1, 0, 0], [1, 0, 0]]

```

Why is aList now not equal to [[1, 0, 0], [0, 0, 0], [0, 0, 0]] ? It seems like aList is actually a list of three pointers all pointing to another list = [0,0,0] which seems strange to me.

---

### Post by kevinlyfellow on 2007-08-15
I think it may be in the way you define aList (I'm not sure why myself)

Try this
```
aList=[[0,0,0],[0,0,0],[0,0,0]]
aList[0][0]=5
print aList
```

---

### Post by Wybiral on 2007-08-15
Lists have strange behavior... They don't copy over (create a brand new object when assigned), they ARE handled with pointers.

Check this out:

```

x = [0, 1, 2, 3]

y = x

y[0] = 7

print x
print y

```

---

### Post by chrisN_uk on 2007-08-15
Ok, thanks. Is there any good reason for them to work like this, ie where would it be usefull. It just seems odd to me!

---

### Post by ssam on 2007-08-15
have a look at [http://docs.python.org/lib/module-copy.html](http://docs.python.org/lib/module-copy.html) if you want to make independant copies of objects.

for creating zeroed lists you can use list comprehension (see [http://docs.python.org/tut/node7.html](http://docs.python.org/tut/node7.html))

eg
```

>>> [0 for x in range(3)]
[0, 0, 0]
>>> [[0 for x in range(3)] for x in range(3)]
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]

```

or look at scipy [http://www.scipy.org/](http://www.scipy.org/) which has tools for arrays and matricies of numbers

---

### Post by Wybiral on 2007-08-15
> **chrisN_uk said:**
> Ok, thanks. Is there any good reason for them to work like this, ie where would it be usefull. It just seems odd to me!

For use in a language like python... I have no idea, I agree... Very odd behavior for python.

If I had to guess I would say it's like that for efficiency... Imagine you have a large tree structure and you pass it to a function or assign it to another variable, python has to do a lot of work to allocate memory and copy all of that data recursively.

But... I thought the point of python was to not worry about things like this... Who knows. Bad choice of design on their behalf, IMO, it doesn't fit with the rest of the language.

---

### Post by scooper on 2007-08-15
> **chrisN_uk said:**
> Ok, thanks. Is there any good reason for them to work like this, ie where would it be usefull. It just seems odd to me!

Python is very consistent, although different from some other common languates.  Variables, including simple types like integer, are just labels for pointers.  Everything is a reference.  A couple of links from a google search.

[Semantics of Python variable names from a C++ perspective]("http://rg03.wordpress.com/2007/04/21/semantics-of-python-variable-names-from-a-c-perspective/")
[Excerpt from Python in a Nutshell]("http://books.google.com/books?id=6TEcaEzA8N0C&pg=PA39&lpg=PA39&dq=python+variable+references&source=web&ots=mf2ObV9HkS&sig=Q_FKFVBjiyC_pDP6DiiHtdHT4b4")

Hope that helps.  You do need to keep in mind the different semantics of Python variables, particularly coming from C, C++, BASIC, etc.  It's not hard, just different.

---

### Post by chrisN_uk on 2007-08-15
Ok, that makes sence. Interesting...this may help to explain some bizzare bugs I've found in my code. Thanks for the help. 

I also didn't know python could do list comprehensions. That could be very usefull.

Thanks for the help!

---

### Post by pmasiar on 2007-08-15
> **chrisN_uk said:**
> Can someone explain this behaviour to me? I'm not sure about it at all...

Why is aList now not equal to [[1, 0, 0], [0, 0, 0], [0, 0, 0]] ? It seems like aList is actually a list of three pointers all pointing to another list = [0,0,0] which seems strange to me.

It is perfectly consistent. Inner [0] * 3 creates single instance of list [0, 0, 0], this reference when is copied 3 times by outer *3. 

All names are just references to objects. Assigning name copies the reference only.

Misunderstanding was caused by inadequate mental model about how [0] * 3 works. Other languages (except Python) cannot do such things at all.. :-)

Copy reference is simple and quick. If you need more functionality, standard library has [module copy](http://docs.python.org/lib/module-copy.html) with deepcopy() function.

---

### Post by pmasiar on 2007-08-15
> **Wybiral said:**
> For use in a language like python... I have no idea, I agree... Very odd behavior for python.

As I explained in previous post, all names are references, so it is perfectly consistent - at least from the Python's perspective :-)

> If I had to guess I would say it's like that for efficiency... Imagine you have a large tree structure and you pass it to a function or assign it to another variable, python has to do a lot of work to allocate memory and copy all of that data recursively.

Exactly. As you just did prove, it *really* helps to understand "bare metal" perspective, as ASM and C gives you, without any clouds of abstraction added by high-level languages!

> But... I thought the point of python was to not worry about things like this... 

Well, it *does* get translated to C after all, doesn't it? :-)

> Bad choice of design on their behalf, IMO, it doesn't fit with the rest of the language.

Any other choice would be *vastly* ineffective in terms of memory and CPU processing required. Or oy have any other better idea how to simply quickly copy deeply nested structures?

Copy reference is simple and quick. If you need more functionality, standard library has [module copy](http://docs.python.org/lib/module-copy.html) with deepcopy() function. Now pray tell me, what will happen when you copy recursive structures? :-)

BTW simple way to copy top level of list, is bList = aList[:]

---

