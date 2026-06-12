---
title: "How to get ipython history a consistent indentation"
date: 2011-01-14
forum: Programming Talk
---

### Post by tachyian on 2011-01-14
Hello everyone! I have a (probably stupid) question about ipython.
When I use the history function of ipython, I encounter the following situation. Suppose I typed the following manually (underscores denote spaces):

--------------------------------------------------
In [1]: for i in range(4):
___...:     print i,
___...:     
___...:     
0 1 2 3
--------------------------------------------------

Now, if I use the history function of ipython by pressing up-arrow key, I get this:

--------------------------------------------------
In [2]: for i in range(4):
____print i,
--------------------------------------------------

But, when I use Mayavi2 with ipython shell and do the same thing, I get this:

--------------------------------------------------
In [2]: for i in range(4):
......:____print i,
--------------------------------------------------
so that I can get exactly same look or a consistent indentation as I typed manually. Of course, this does NOT seem to cause any problem when I hit enter key twice to get any result. But, it's just annoying that I can't get quite the same look as I typed. How can I make ipython put additional periods in front as Mayavi does for its ipython prompt?
Thanks in advance!

---

