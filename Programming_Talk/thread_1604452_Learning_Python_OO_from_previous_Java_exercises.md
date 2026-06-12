---
title: "Learning Python OO from previous Java exercises"
date: 2010-10-24
forum: Programming Talk
---

### Post by skytreader on 2010-10-24
As the title says, I am trying to learn Python OO through my beginner Java OO exercises. I'm running into some bumps and I was hoping someone could help me.

I'm currently doing a lock vs. unlocker simulator. That is, I have a Lock class (which simulates those locks with an array of number rollers---get the right combination to open) and an Unlocker class (which tries to pick the proper combination through brute-force). Now, in Java, I'll set the LockCombination (an int[]) private so that the Unlocker will be forced to brute-force. However, as there are no private variables in Python (see [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html) Section 9.6), the Unlocker class can access the LockCombination easily which kinda defeats the purpose.

So, is this a Python feature or bug? Or is the exercise simply not suited for Python/a job specifically for a language the likes of Java?

---

### Post by NovaAesa on 2010-10-24
In python you are able to "mark" a member as private by prepending it with an underscore. Of course, this doesn't really make it private... This is one area of python that I have yet to come to terms with, if it wasn't for this sort of thing I might use it more often for things other than short scripting.

---

### Post by schauerlich on 2010-10-24
Python has a more "We're all adults here" attitude towards these things compared to Java or C++. You mark things as private by giving it underscores, even though it's still accessible from the outside. The underscores just announce to the world that even though you *can* access those variables, you probably shouldn't because it will probably mess things up. See [here](http://stackoverflow.com/questions/1641219/does-python-have-private-variables-in-classes) for another discussion.

---

### Post by worksofcraft on 2010-10-24
> **skytreader said:**
> 
So, is this a Python feature or bug? Or is the exercise simply not suited for Python/a job specifically for a language the likes of Java?

Private/protected can help readability of code by letting you know what bits of a class are internal details that you can usually remain unaware of.

The times when private and protected class members are **really** important is when there is a mutual dependency between them that must be maintained.

In my own C++ code I mostly use "struct", a kind of class that has all members as public by default. I add the private/protected specifier only where necessary as a reminder that those items need to be handled with appropriate methods to maintain integrity and internal consistency.

I think the design of Python is very sensible in this respect, because it avoids the senseless code bloat we sometimes see in other languages and I'll start using those underscores where they are appropriate in the future too :)

---

### Post by nvteighen on 2010-10-24
1. Python has a way to do this, but it's not 100% failproof because it's a very naïve approach for it: to make something private name it using **two** leading underscores but **none** ending: __myprivate (__myprivate__ won't do the trick). What this does is to activate a very simple name mangling that will not allow you to access that data using, in my example, __myprivate. But again, it's very easy to break (I leave the exercise to you).

2. I don't know about Java, but C++ privacy is only valid at compile-time. You can break it at runtime. The idea is to establish an API the compiler can enforce, not really to protect the data. In that sense, it isn't that different to what Python offers to you with the __myprivate idiom; the difference between them is that C++ is a statically compiled language, while Python is not and therefore, in C++ you get the illusion of "real" privacy as you can't modify the code on the fly so easily (and commonly) as in Python.

---

### Post by skytreader on 2010-10-24
nvteighen, that's pretty interesting. Thanks I'll try it out.

(For the record, I've abandoned the lock vs. unlocker exercise in favor of others where private/public doesn't matter. Thank you for everyone who answered my question.)

---

