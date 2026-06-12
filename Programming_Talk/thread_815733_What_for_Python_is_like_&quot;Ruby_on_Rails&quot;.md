---
title: "What for Python is like &quot;Ruby on Rails&quot;?"
date: 2008-06-01
forum: Programming Talk
---

### Post by jsmidt on 2008-06-01
I can do a lot of good programming in python.  Mostly for scientific things and gui stuff.

I would like to get more involved in web development.  I've had several people recommend looking at ruby on rails.  

I'm not against learning ruby, but there has to be something similar to "ruby on rails" for python. What is a good web application framework based on python?

---

### Post by mbeach on 2008-06-01
could try django
[http://www.djangoproject.com/](http://www.djangoproject.com/)

---

### Post by Can+~ on 2008-06-01
There are MANY, from "Python in a nutshell":

"...Cherrypy ([http://www.cherrypy.org](http://www.cherrypy.org)), Django ([http://www.djangoproject.com](http://www.djangoproject.com)), Pylons ([http://pylonshq.com](http://pylonshq.com)) and TurboGears([http://www.turbogears.org](http://www.turbogears.org))..."

---

### Post by jsmidt on 2008-06-01
> **Can+~ said:**
> There are MANY, from "Python in a nutshell":

"...Cherrypy ([http://www.cherrypy.org](http://www.cherrypy.org)), Django ([http://www.djangoproject.com](http://www.djangoproject.com)), Pylons ([http://pylonshq.com](http://pylonshq.com)) and TurboGears([http://www.turbogears.org](http://www.turbogears.org))..."

Yes, so I was smart enough to do some background work checked things like the Wikipedia etc...  So I saw lists like this too.

I guess the real question I am after is which one, or two, of all of these are the ones that would be the best to try to use?

---

### Post by LaRoza on 2008-06-01
> **jsmidt said:**
> Yes, so I was smart enough to do some background work checked things like the Wikipedia etc...  So I saw lists like this too.

I guess the real question I am after is which one, or two, of all of these are the ones that would be the best to try to use?

I hear that Turbogears and Django are the top two. They seem to have different foci, so you can check both with your goals.

---

### Post by jsmidt on 2008-06-01
Thanks everyone.  I always know you guys will help out.

---

### Post by pmasiar on 2008-06-01
Another option is Google App Engine, which has it's own web framework. Recently it was open for all developers - free hosting!

Database is little different: non-relational, slow to write but fast to fetch.

I heard about rumors of porting Django to GAE. It's little hard because GAE limits number of files allowed (to about 10K), and framework tend to have many files :-)

Django is good start, has excellent auto-generated admin frontend, to entering data is simpler. But it limits modules you can use (it's basically one-size-fits-all).

Turbogears gives you more control, for little more effort, but it is simpler to swap modules to other, as you prefer. Pylons is meta-framework used by Turbogears to put stuff together.

---

