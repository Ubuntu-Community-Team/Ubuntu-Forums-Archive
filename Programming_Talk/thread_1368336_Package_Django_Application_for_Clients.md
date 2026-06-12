---
title: "Package Django Application for Clients"
date: 2009-12-30
forum: Programming Talk
---

### Post by deejross on 2009-12-30
I am developing a business application using Django and the application is intended to be used by those who may not even know what Linux is. I will most likely compile my application into a Python Egg file. I was thinking about using remastersys to make a custom Ubuntu CD configured with Apache + mod_wsgi, ready to go, almost like an appliance. But then I'd probably end up supporting not only my application, but Ubuntu as well.

What would be the best way to approach this kind of distribution? Also, if I went with a custom Ubuntu CD, what would be the legal concerns there if I made the CD a free download, but charged for the license keys which would be required to use the application?

I've looked at the Django reusable apps project, but it requires a fully working Linux + Django installation already, and again, the customer may not even know Linux exists, much less how to use it.

Thanks for your insight

---

### Post by delfick on 2009-12-30
can it be run locally such that you don't need apache ?? (just use "python manage.py runserver")

Otherwise someone would surely have to setup that stuff for them......

---

### Post by deejross on 2009-12-31
The only problem with that is that they tell you to only use that during development and specifically never to use it in production. I know that from using it, it only handles one request at a time, so using it in a multiple-user environment (for which it is intended), will not work.

---

