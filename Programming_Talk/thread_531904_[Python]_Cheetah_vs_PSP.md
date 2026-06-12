---
title: "[Python] Cheetah vs PSP"
date: 2007-08-22
forum: Programming Talk
---

### Post by aks_! on 2007-08-22
Hi,

I've started to work on a blog project written in python (using apache's mod_python - publisher handler) but now I don't know which template engine would be a better choice to use. I have done some research and somehow I've decided for two favorites - Cheetah and PSP (Python Server Pages).

I find cheetah syntax somehow more readable and I've also noticed that it is quite popular among the python web developers. But on the other hand, mod_python already comes with PSP and due to its similarity with PHP it may be more suitable for people unfamiliar with python.

What is your opinion about both choices?

---

### Post by pmasiar on 2007-08-22
Use Django, it has everything. See wiki example. Don't waste time on PSP - it is almost as messy as PHP.

BTW: IMHO best Python template engine is Kid (and Kid 2 == Genshi).

---

### Post by aks_! on 2007-08-22
Hmm, I'm not sure if I want to use a whole framework. I think that using a framework would make this project too big since I only need a template engine and some good orm (sqlalchemy, geniusql or storm). What is django's template module like? Is it possible to use it standalone?

---

### Post by pmasiar on 2007-08-22
for lightweight approach use Pylons.

Turbogears integrates SqlAlchemy and Kid, i am not sure why you want to reinvent the glue code binding it all together, but you are free to do that.

---

