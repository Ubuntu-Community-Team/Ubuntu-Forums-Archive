---
title: "Python web programming"
date: 2010-02-28
forum: Programming Talk
---

### Post by hoboy on 2010-02-28
What is the best web programing framework for python.
I want to make some web pages in python, and need a davice to chose a web technology for python

---

### Post by CptPicard on 2010-02-28
Django.

---

### Post by cb951303 on 2010-02-28
it depends.

**Django:** easy to learn, all-in-one framework

**Pylons**: modular, with ability to choose your own ORM or template engine

**Web.py:** lightweight

**Turbogears 2:** built on pylons. as it's noted on their website, it's a megaframework. lots of features (Sourceforge decided to go with Turbogears)

**Web2Py:** never tried this one. it looks ok to me but a lot of people thinks its badly designed. but be warned it might be completely wrong.

I personally love Django. It's so easy to start with and has everything one needs out of the box. My only wish would be an official NoSQL ODM but AFAIK none of the Python web frameworks officially support it yet.

EDIT: Oh by the way Django has a very nice e-book here: [http://www.djangobook.com/](http://www.djangobook.com/)

---

### Post by DaithiF on 2010-02-28
Django +1

---

### Post by n0dix on 2010-02-28
> **DaithiF said:**
> Django +1

+1 Django.

---

### Post by mdipierro on 2010-02-28
web2py is designed differently than other Python frameworks since it gives more importance to "do not repeat yourself" than the Python motto "explicit is better than implicit". For example you do not need to know in which module the framework keywords are defined, they are already imported for you in the name-space (like in Rail, it is the only Python framework to do so). It also has a fully web based IDE (it is the only Python framework to that too) and the only database abstraction layer that works on both relational databases and the Google App Engine. Some people love it because of its ease of use, other people hate it for the very same reason.;)

---

### Post by cb951303 on 2010-02-28
mdipierro, I think you have replied every single web2py thread on the internet :) how do you do that?

btw, do you plan implementing any NoSQL ODM in web2py?

---

### Post by mdipierro on 2010-02-28
You may be right. Unfortunately I do not sleep much :sad:
The web2py Database Abstraction Layer already supports GAE which is a NoDB. We are about to release a complete re factoring of DAL (it is already in trunk but needs a little more work) that is 100% backward compatible but has a more modular structure. I allows to built "adaptors" for both DBs and NoDBs. We hope to have support for MongoDB and CouchDB in 2 months.

---

### Post by cb951303 on 2010-02-28
> **mdipierro said:**
> You may be right. Unfortunately I do not sleep much :sad:
The web2py Database Abstraction Layer already supports GAE which is a NoDB. We are about to release a complete re factoring of DAL (it is already in trunk but needs a little more work) that is 100% backward compatible but has a more modular structure. I allows to built "adaptors" for both DBs and NoDBs. We hope to have support for MongoDB and CouchDB in 2 months.

great news, I was hoping to try MongoDB without messing with mongokit and alikes.

---

### Post by WillyTheDisk on 2010-02-28
web2py is the most productive python framework I've ever used.

---

