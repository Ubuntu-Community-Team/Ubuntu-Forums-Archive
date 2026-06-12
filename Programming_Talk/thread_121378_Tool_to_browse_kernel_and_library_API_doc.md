---
title: "Tool to browse kernel and library API doc"
date: 2006-01-25
forum: Programming Talk
---

### Post by metaosp on 2006-01-25
What is the best way to browse documentations of kernel and library APIs?  'man' is good when you want to check a specific thing, but what if I want to browse, say, all time related functions provided by stdc++ library?  Any good tool to use?

---

### Post by toojays on 2006-01-25
Unfortunately there is no 'best'. It depends on what you want to look up. For instance, docs for Qt, KDE and wxWidgets are HTML only afaik. HTML is a crappy format for API docs because there is not very good facility for searching. But unless you want to reformat the docs yourself, there is no other choice.

For the C library, info format is the best. For instance, if you are in Emacs and want to browse functions related to time, press the following key combos (described in brackets):

C-h i (info mode) m libc RET (libc menu item) i time RET (lookup time in the index)

You can then press comma to see the next thing to do with time, or press 'u' to go "up" in the documentation and see other things in the same chapter.

Of course you can also navigate info with the mouse, but when you learn the key combos you get the info you need so much faster.

The info format is seriously great. The fact that it is not used so much these days is one of the big losses of the early Free/Open acrimony.

Oh, by the way, I think you need to have libc-doc installed for my example to work. Many Ubuntu packages do not install info format docs by default.

---

