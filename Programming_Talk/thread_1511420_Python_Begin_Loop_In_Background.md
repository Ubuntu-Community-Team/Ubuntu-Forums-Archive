---
title: "Python Begin Loop In Background"
date: 2010-06-16
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-16
What's Up?

OK, So I'm still scripting my first python project and I've hit a snag, I need to be able to perform
some commands in a loop, However also carry on performing other functions, Using bash you 
could send your procces to the background by using a ampersand, What's the Python eqivelent?

Thanks Bye!

---

### Post by patchwork on 2010-06-16
Sounds like the threading module might be useful here.  This will allow you to create a thread for the operation in the background, or multiple threads.

A tutorial is found here:
[http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/1/](http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/1/)

---

