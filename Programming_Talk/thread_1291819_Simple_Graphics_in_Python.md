---
title: "Simple Graphics in Python"
date: 2009-10-15
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-10-15
I want to draw simple geometric figures in Python, how is that possible. I don't want to use high end GUI designing stuff. I found this called Turtle, but can't find many resources on the net. 

Can someone please help me, the main structures i want to draw include, Arrows, Circles(i figured this out). 

And is it possible for the turtle output to come in one flash, rather than a turtle walking across a screen??

---

### Post by Can+~ on 2009-10-15
Turtle is part of the standard library (see: [turtle]("http://docs.python.org/library/turtle.html"))

If you want something more powerful, try vector graphics with [Cairo]("http://cairographics.org/documentation/")

---

### Post by wmcbrine on 2009-10-15
Graphics don't get much simpler than SDL, which in Python terms means Pygame. But, vector graphics aren't its strong suit.

---

