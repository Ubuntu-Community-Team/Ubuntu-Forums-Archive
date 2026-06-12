---
title: "Streamlining Accessors in Python"
date: 2006-10-20
forum: Programming Talk
---

### Post by Ubuntist on 2006-10-20
I'm a big fan of OO but get tired of having to write accessor methods all the time.  Basic read and write accessors are so simple and so commonly used that I think it would be great if Python had a shortcut for creating them.  I know Ruby has such a shortcut built into the language itself.  Is there some way of faking the same thing in Python?

---

### Post by Wille on 2006-10-20
You probably shouldn't use accessor functions in python. Just use  attributes directly.

Later on, if you want to make attribute "electric" (so that get/set has side effects), you can use the "property" feature.

Though there seems to be a recipe that might interest you:

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/157768](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/157768)

---

### Post by Ubuntist on 2006-10-20
Thanks -- that's cool piece of code!

---

