---
title: "Optional Static Typing in Python - language designer speak his mind"
date: 2007-01-05
forum: Programming Talk
---

### Post by pmasiar on 2007-01-05
For you lovers of static typing, Guido plans [Optional Static Typing]("http://www.artima.com/weblogs/viewpost.jsp?thread=85551"). Py3k beta is coming this year. I am looking forward to it!

Couple other interesting threads about language design I dug out from Guido's blog:
[LIST]
[*][Language Design Is Not Just Solving Puzzles]("http://www.artima.com/weblogs/viewpost.jsp?thread=147358")
[*][The Harry Potter Theory of Programming Language Design]("http://www.artima.com/weblogs/viewpost.jsp?thread=123234")
[*][Adding Optional Static Typing to Python -- Part II]("http://www.artima.com/weblogs/viewpost.jsp?thread=86641") - about syntax and simplicity
[*][The fate of reduce() in Python 3000]("http://www.artima.com/weblogs/viewpost.jsp?thread=98196") - why to remove language features. Lambda was later decided to live again.
[/LIST]

---

### Post by gummibaerchen on 2007-01-05
I think that would confuse many newcomers, when they look at some program who use that.

Why not just leave it the way it is?

---

### Post by pmasiar on 2007-01-05
> **gummibaerchen said:**
> I think that would confuse many newcomers, when they look at some program who use that.

Why not just leave it the way it is?

Well did you read Guido's reasoning? It is:

1) Optional

2) only for people who needs it, like some frameworks, who implement it each own way.

But for people  around us addicted to static typing, it might add warm fuzzy feeling of Big Compiler checking lovingly their types :-)

---

### Post by Van_Gogh on 2007-01-06
> **pmasiar said:**
> For you lovers of static typing, Guido plans [Optional Static Typing]("http://www.artima.com/weblogs/viewpost.jsp?thread=85551"). Py3k beta is coming this year. I am looking forward to it!


FWIW, That article is rather old, and I don't think that the plan currently is to include optional static typing in Python 3.0. Guido has a presentation on it (can be found on Google Video) and I don't recall him mentioning static typing.

This is all from memory  though...

---

### Post by gummibaerchen on 2007-01-06
> **pmasiar said:**
> Well did you read Guido's reasoning? It is:

1) Optional

2) only for people who needs it, like some frameworks, who implement it each own way.

But for people  around us addicted to static typing, it might add warm fuzzy feeling of Big Compiler checking lovingly their types :-)

Yeah, I read his articles. But I would not like that in Python (as I said, for the newbies).
And would it help in any way? Couldn't read anything about speed improvements.

> **Van_Gogh said:**
> FWIW, That article is rather old, and I don't think that the plan currently is to include optional static typing in Python 3.0. Guido has a presentation on it (can be found on Google Video) and I don't recall him mentioning static typing.

This is all from memory  though...
I hope you're right ;)

---

### Post by Wybiral on 2007-01-06
Well, you know me... I think it's a good idea. The programs will look much more laid out and it will be more clear what everything is. The syntax looks funny, but I-for-one think it's a good idea.

---

