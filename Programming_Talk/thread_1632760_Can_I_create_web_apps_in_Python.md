---
title: "Can I create web apps in Python?"
date: 2010-11-28
forum: Programming Talk
---

### Post by stamatiou on 2010-11-28
Hey guys, I have recently started Python and I'd like to know if I can create web applications with it....
If yes, where can I learn?

---

### Post by DaithiF on 2010-11-28
Django, start with the tutorial at [http://www.djangoproject.com/](http://www.djangoproject.com/)

---

### Post by stamatiou on 2010-11-28
Off topic:
    Is there a programing language better than python to create web apps or sites?

---

### Post by debsankha on 2010-11-28
You can take a look at [google appengine]("http://code.google.com/appengine/").

---

### Post by stamatiou on 2010-11-28
> **debsankha said:**
> You can take a look at [google appengine]("http://code.google.com/appengine/").
I will  check it out......
What about Ruby?

---

### Post by DaithiF on 2010-11-28
my advice ... pick **one **language (it doesn't matter much which), learn it, use it, and once you're proficient then pick another and repeat ...

---

### Post by stamatiou on 2010-11-29
> **DaithiF said:**
> my advice ... pick **one **language (it doesn't matter much which), learn it, use it, and once you're proficient then pick another and repeat ...
Yes but in Python is the delf thing that I dont have understood and I have read it million times but... I still cant understand it............ :( :confused:

---

### Post by DaithiF on 2010-11-29
> **stamatiou said:**
> Yes but in Python is the delf thing that I dont have understood and I have read it million times but... I still cant understand it............ :( :confused:
I don't know what you mean by 'delf thing'

---

### Post by stamatiou on 2010-11-29
> **DaithiF said:**
> I don't know what you mean by 'delf thing'

Sorry I mean the self thing.....

---

### Post by juancarlospaco on 2010-11-29
[http://web2py.com/](http://web2py.com/)

There, go there

---

### Post by stamatiou on 2010-11-30
> **juancarlospaco said:**
> [http://web2py.com/](http://web2py.com/)

There, go there
Is this something like pygame?

---

### Post by ziekfiguur on 2010-11-30
You should also take a look at the libapache2-mod-python and libapache2-mod-python-doc packages, they're in synaptic.

---

### Post by stamatiou on 2010-11-30
> **ziekfiguur said:**
> You should also take a look at the libapache2-mod-python and libapache2-mod-python-doc packages, they're in synaptic.
What are these, how can I use them?

---

### Post by juancarlospaco on 2010-11-30
> **stamatiou said:**
> Is this something like pygame?

No, i mean, i dont understand the question.
Just try it ;)

---

### Post by ziekfiguur on 2010-11-30
> **stamatiou said:**
> What are these, how can I use them?

libapache2-mod-python is a package that allows you to use python for server-scripting, similarly to how PHP is normally used. The other package contains documentation of how to use it.

---

### Post by stamatiou on 2010-12-01
> **juancarlospaco said:**
> No, i mean, i dont understand the question.
Just try it ;)
Can I upload my apps with this  on my site?

---

### Post by DanielWaterworth on 2010-12-01
> **ziekfiguur said:**
> libapache2-mod-python is a package that allows you to use python for server-scripting, similarly to how PHP is normally used. The other package contains documentation of how to use it.

I'd recommend you use wsgi instead of mod python. mod python reloads the interpreter for every request. It's much faster to use wsgi.

---

### Post by juancarlospaco on 2010-12-01
Yes.

---

