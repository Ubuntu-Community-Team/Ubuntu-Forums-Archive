---
title: "Python Conventions"
date: 2007-08-01
forum: Programming Talk
---

### Post by Nekiruhs on 2007-08-01
I was wondering, I know when I programmed VB there were a lot of general naming conventions. Now that I am using PyGTK + glade, do those still apply, is it good style to use them? Also, is underscores ( _ ) or camelCase the more pythonic way to name functions and variables (my_Func() or myFunc()). And if anyone knows anymore conventions, please post them here.

---

### Post by LaRoza on 2007-08-01
> **Nekiruhs said:**
> I was wondering, I know when I programmed VB there were a lot of general naming conventions. Now that I am using PyGTK + glade, do those still apply, is it good style to use them? Also, is underscores ( _ ) or camelCase the more pythonic way to name functions and variables (my_Func() or myFunc()). And if anyone knows anymore conventions, please post them here.

[http://www.python.org/doc/essays/styleguide.html](http://www.python.org/doc/essays/styleguide.html)

---

### Post by pmasiar on 2007-08-01
It was even formalized to PEPs: [0008](http://www.python.org/dev/peps/pep-0008/) Style Guide for Python Code, and [0257](http://www.python.org/dev/peps/pep-0257/) for Docstring.

In one sentence, under_score for names (variables, objects, methods), CamelCase for classes.

Style guide should be linked from top docs page [http://docs.python.org/index.html](http://docs.python.org/index.html) but it isn't :-(

We had also [style guide for whitespace](http://www.artima.com/weblogs/viewpost.jsp?thread=101968) with strict enforcement, but only as an April's Fools.

---

