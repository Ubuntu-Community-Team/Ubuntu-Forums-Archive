---
title: "[SOLVED] I cant find a decent python tutorial"
date: 2008-07-14
forum: Programming Talk
---

### Post by MONODA on 2008-07-14
I have been learning pything by myself for a while now and have been switching between tutorials. The reason for this is because one may begin to progress too quickly for me and not go into much detail about certain topics. I have been mainly using the python docs and the dive into python tutorial. 

The python docs tend to just skim over most of the topics so I am left with an unclear idea. The dive into python tutorial is a bit better but assumes too much prior programming knowledge which I dont have, unless bash can be considered a language.

What I ask is for you to share with me the tutorial you used to learn python. I would also like it if you could recommend me a book which you found useful for learning python. Thanks in advance.

P.S. I am willing to relearn everything I have already read in these tutorials since most topics where not explained properly for me.

P.P.S. I have been able to get as far as section 4.5 in the python docs and 4.2 in dive into python, anything beyond that I cannot comprehend since the info given is not enough for me.

---

### Post by ghostdog74 on 2008-07-14
> **MONODA said:**
> 

The python docs tend to just skim over most of the topics so I am left with an unclear idea. 
what topics are skimmed over in the python tutorial?

---

### Post by MONODA on 2008-07-14
so far I have come across the following that I did not understand due to lack of detail in the python docs:
for statements
break and continue statements
pass statements

---

### Post by WiseElben on 2008-07-14
What do you mean by progressing too quickly and not going into details? If you want to know what's going on "under the hood", then I'd suggest that you reconsider. Yes, it's good to know how everything works, but you have limited resources (i.e. limited time), so I would not worry about such things at the moment.

I find that selective ignorance helped me learn faster. I mean, you don't learn how a car is built before learning to drive it. If you want to be build cars, then sure, you should learn everything about it, but learning to drive is the first step.

Python is a high-leveled language, and it should be treated as such. For the moment, don't fret about why something works, just know that it works. Learn to use Python to do actual programming first (i.e. to solve problems), then you can worry about the more detailed stuff.

---

### Post by WiseElben on 2008-07-14
> **MONODA said:**
> so far I have come across the following that I did not understand due to lack of detail in the python docs:
for statements
break and continue statements
pass statements

There is a free Python book here: [http://www.greenteapress.com/thinkpython/](http://www.greenteapress.com/thinkpython/)

---

### Post by LaRoza on 2008-07-14
Don't rely on one tutorial. Try my wiki, which has a lot, and use as many as you find useful.

If you find a topic in one tutorial less fleshed out, another will have it.

---

### Post by Greyed on 2008-07-14
> **MONODA said:**
> so far I have come across the following that I did not understand due to lack of detail in the python docs:
for statements
break and continue statements
pass statements

Er, exactly how are those skimmed?  Those are basic.

For iterates over a list (or dict, etc).

Break breaks out of a loop.

Continue skips to the next item in a loop.

Pass is a blank statement which is used when you're going to create a block that does nothing but don't want Python to give you an error for bad indenting.

Really, not much more to it than that.  Hard to skim because they're simple.

When in doubt, open up the Python interpreter and just work through stuff until you understand it.

---

### Post by ghostdog74 on 2008-07-14
> **MONODA said:**
> so far I have come across the following that I did not understand due to lack of detail in the python docs:
for statements
break and continue statements
pass statements

did you really read the [tutorial]("http://docs.python.org/tut/node6.html#SECTION006200000000000000000")? its covered you know?

---

### Post by MONODA on 2008-07-14
> What do you mean by progressing too quickly and not going into details? If you want to know what's going on "under the hood", then I'd suggest that you reconsider. Yes, it's good to know how everything works, but you have limited resources (i.e. limited time), so I would not worry about such things at the moment.
hmmm... well I thought that if I didnt know how a certain program used as an example in a tutorial works then I wont be able to use this information later, is that not correct? maybe things are different in programming but for me things are usually like that

> Er, exactly how are those skimmed? Those are basic.

For iterates over a list (or dict, etc).

Break breaks out of a loop.  yes of course but it does not go into details on how to use the break.

> 
Continue skips to the next item in a loop.  again, this is obvious but I am left without any knowledge on how to use this

> 
Pass is a blank statement which is used when you're going to create a block that does nothing but don't want Python to give you an error for bad indenting.  same as above

---

### Post by LaRoza on 2008-07-14
> **MONODA said:**
> hmmm... well I thought that if I didnt know how a certain program used as an example in a tutorial works then I wont be able to use this information later, is that not correct? maybe things are different in programming but for me things are usually like that
It is easiest to try it and see what happens. Mess around in the interaction prompt.

> 
 yes of course but it does not go into details on how to use the break.


You put the word in the loop. It isn't really important if you don't see a need for it (yet).
```

>>> while True:
...     if raw_input() == "t":
...         break
...     else:
...         continue
... 
s
t
>>> 

```

---

### Post by MONODA on 2008-07-14
alright thanks, Ill mark this thread solved.

---

