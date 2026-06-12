---
title: "How To Create a Forum in MoinMoin"
date: 2008-08-18
forum: Programming Talk
---

### Post by ealite on 2008-08-18
HI, 

I am new to moimoin. Does anyone know how one can create a simple forum in moimoim wiki ? 

Thanks in advance 

Erion

---

### Post by pmasiar on 2008-08-18
> **ealite said:**
> I am new to moimoin. Does anyone know how one can create a simple forum in moimoim wiki ? 

AFAIK, MoinMoin is a wiki, not a forum. Users share editing each page, which is orthogonal to forum (where each members touts own opinion).

If you don't mind users editing each other comments, wiki is all right.

One way to hack a forum from a wiki is to add Comment Plugin (which allows to add comment to a page) and allow only to some people edit the pages. This way you have best of both worlds.

---

### Post by ealite on 2008-08-18
Thank you pmasiar,

This forum is for developers only. We just want have only one application managing the developers discussions and documentation. Do you know how I can install this plugin ? 

Thanks

---

### Post by pmasiar on 2008-08-18
Developers are smart enough -- you may not worry about "disagreement by deleting", and IIRC  MoinMoin does have history, so is easy to revert changes?

I used TRAC - [http://trac.edgewall.org/](http://trac.edgewall.org/) version of MoinMoin, which might be something for you too: it integrates wiki, bug tracker, and code repository, in one package and united markup.

[http://trac.edgewall.org/wiki/PluginList](http://trac.edgewall.org/wiki/PluginList)
[http://trac-hacks.org/wiki/DiscussionPlugin](http://trac-hacks.org/wiki/DiscussionPlugin)

I used comment plugin I found somewhere and hacked it to my wants in hour or so - it was in Python, quite obvious. That website is gone for long time, so sorry no code available :-(

---

