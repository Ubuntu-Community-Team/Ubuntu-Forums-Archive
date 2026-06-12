---
title: "Python framework for Desktop"
date: 2008-07-14
forum: Programming Talk
---

### Post by gfa on 2008-07-14
Hi everyone.

Is there some kind of Django framework but for desktop applications written in Python?

(DB abstraction, MVC focus, ...)

Thanks.
gFa

---

### Post by Wybiral on 2008-07-14
I'm not sure about MVC, but you can use the database abstraction... [SQLObject]("http://www.sqlobject.org/") and [SQLAlchemy]("http://www.sqlalchemy.org/") are both their own libraries that you can use to ORM something like sqlite.

Depending on your goals, you could always just run a local server and use a webframework for your desktop needs.

---

### Post by pmasiar on 2008-07-14
[http://www.google.com/search?q=python+desktop+mvc+framework](http://www.google.com/search?q=python+desktop+mvc+framework) shows your question as #3 hit :-) but there is some hopeful links there...

Seems like there are too many ways to do the 'view' part?

---

### Post by Quikee on 2008-07-14
There is gtkmvc for the MVC part but I don't remember seeing a complete solution either.

---

### Post by gfa on 2008-07-15
Last week I found 2 projects, but I just didn't get convinced (and wanted replies without my subjective):

- Kiwi
- Dabo

Both looks like if abandoned (or at least low attention), so Quikee's reply is the one I will study...


> **Quikee said:**
> There is gtkmvc for the MVC part but I don't remember seeing a complete solution either.

Thanks!!! Looks promising, I'll start reading about it.


> **Wybiral said:**
> I'm not sure about MVC, but you can use the database abstraction... [SQLObject]("http://www.sqlobject.org/") and [SQLAlchemy]("http://www.sqlalchemy.org/") are both their own libraries that you can use to ORM something like sqlite.

Depending on your goals, you could always just run a local server and use a webframework for your desktop needs.

OK, I will see SQLObject and ORM (I found python-storm) but as 2nd options.


> **pmasiar said:**
> [http://www.google.com/search?q=python+desktop+mvc+framework](http://www.google.com/search?q=python+desktop+mvc+framework) shows your question as #3 hit :-) but there is some hopeful links there...

Seems like there are too many ways to do the 'view' part?

Right now I see these post as #3 using that search ;)

If that comment was kind of STFW, I already did it (as you can see above this post), and found Kiwi and Dabo neither convincing me.

---

### Post by vinicius.marconi on 2009-06-19
Hi,

There are a new Python framework for Desktop: pyHed ( [http://www.pyhed.com]("http://www.pyhed.com/index_us.html") )  pyHed uses sqlAlchemy  and PyQT4, its a very nice choice for those who want build Python desktop  applications with speed and efficiency. It's currently in version 1.0 and has  tutorials to help you to begin.
I'm one of the developers and I use pyHed in  many applications and pyHed meets all my needs.

Visit the project site: [www.pyhed.com]("http://www.pyhed.com/index_us.html") <[http://www.pyhed.com]("http://www.pyhed.com/index_us.html")>

Regards

Vinícius  Marconi
pyHed Team

---

